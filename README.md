# CMPS 2200  Recitation 01

**Name (Team Member 1):** Meyer Polanco 

NOTE FROM MEYER: THIS WAS SUBMITTED FROM MY OWN REPO BECAUSE I STILL HAVE NOT BEEN ABLE TO GAIN ACCESS TO THE OTHER ONE THROUGH CANVAS.

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`. All tests are in `test_main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest test_main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

ANSWER: The worst case input value for `key` in both `linear_search` and `binary_search` is a value that is not in the list. For example, in a list [1,2,3,4,5] something like 10 would be an example of the worst case.

- [ ] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

ANSWER: The best case input value for `key` in `linear_search` is whatever value is in index 0 of the relevent list. For example, in a list [1,2,3,4,5] an input of 1 would be an example of the best case.

The best case input value for `key` in `binary_search` is whatever value is in the middle index of the relevent list. For example, in a list [1,2,3,4,5] an input of 3 would be an example of the best case.

- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest test_main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

|            n |   linear |   binary |
|--------------|----------|----------|
|       10.000 |    0.001 |    0.007 |
|      100.000 |    0.003 |    0.001 |
|     1000.000 |    0.029 |    0.002 |
|    10000.000 |    0.301 |    0.002 |
|   100000.000 |    2.922 |    0.002 |
|  1000000.000 |   29.530 |    0.010 |
| 10000000.000 |  291.470 |    0.017 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

ANSWER: Yes, my results generally match the theory. As n grows larger and larger, the runtime of the linear function grows massively while the binary function grows at a much slower rate.

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? 
  ANSWER: The worst case complexity will be $O(kn)$
  + For binary search? 
  ANSWER: The worst case complexity will be $O(n^2 + klog_2(n))$
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? 
  ANSWER: It becomes generally more efficient to sort and use binary search when k>n.
