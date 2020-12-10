## PROJECT CONTRIBUTORS

Hoang Trung Hieu (hieu.ht183915@sis.hust.edu.vn)

Nguyen Tien Thanh (nguyenthanh@soict.hust.edu.vn)

Nguyen Khanh Van (vannk@soict.hust.edu.vn)

Bui Manh Cuong

Le Vinh Nhon (nhon.lv176841@sis.hust.edu.vn)

Nguyen Chi Hieu

## LICENSE / USE

The javatuples directory contains a collection of network topologies, which are not our work. Other code is original contributions of the above contributors, and is released under the MIT LICENSE (see "./LICENSE"). 

We would appreciate you citing this code and the most relevant of our associated research publications below.

## BACKGROUND

The following research paper explains the ideas behind this tool:

A Reduction Model For Simulating Large-Scale Interconnection Network (Nguyen Tien Thanh, Nguyen Khanh Van, Bui Manh Cuong)

## CONTENTS AND STRUCTURE

Directory listing:

* common: contains some data structures and some utility classes for standard inputs and outputs

* config: provides a class which contains all constants in this project

* custom: code for creating the fat-tree graph and and its routing algorithm

* events: contains all the events for the simulator and actions for these events

* infrastructure: provides essentials for infrastructure of this project

* javatuples: contains tuples of network elements

* network: contains all elements of the topology such as layers, hosts, switches, buffers, routing tables, ...

* results: you will find the results of the program here

* routing: code for routing algorithm and routing path

* simulator: code for create the simulator and its actions

* weightedloadexperiment: contains some ways to pair source hosts and destination hosts, GUI of the throughput grapha and main method

## INSTRUCTIONS FOR USE

1. You must have a linear program solver that accepts the standard LP format used by multiple available solvers. By default, our code uses the Gurobi solver (http://www.gurobi.com/) which is available free to academics. If you want to use a different solver, you'll need to rewrite scripts/lpRun.sh accordingly. If you want a solver that uses a different LP format, more extensive changes will be needed in Graph.java, where you'll modify the 'PrintGraphforMCFFairCondensed' method. If you're using Gurobi, please ensure that you can run it from the command line as 'gurobi_cl <a file containing some test linear program>'. Instructions for setting up Gurobi can be found on their website (and keep evolving over time).

2. If you've accomplished #1 above, you can quickly get something running and test that our code is working as expected, by changing to the 'scripts' directory and executing: ./fatCompare.sh

After execution, check the 'plots' directory for fatCompare.pdf. The values > 1 indicate that many more servers could have been added to Jellyfish while still achieving full throughput. Note that the script runs only 3 sizes for comparison with only 3 runs each for this quick demo. You can look at fatCompare.sh and uncomment a clearly marked line to be able to run the comparison for many sizes, and see a more meaningful plot result.

3. The other scripts in 'scripts' plot various other results from our papers. The clean.sh script deletes all temporary / data / result / plot files. The lpRun.sh script has already been discussed above.

4. You can write similar scripts to the ones in 'scripts' to run the multitude of graph types we have made available in lpmaker/graphs. All the results in our papers have been generated using variations of these scripts!

5. Paper (3) includes results on a large number of real-world graphs. These can be found in 'graphrepo'.

## NOTES

* Error handling is poor at this time. For example, if you're running networks that are too large, there will be memory errors etc. These have not been gracefully handled so far.

* In order to support scalability under all-to-all traffic, a simplified version of the LP has been added. While both the LPs yield the same result, the new version runs faster under dense traffic matrices such as all-to-all. Please note that the results in the papers were computed using the old version.

* This README, another README in upperBound, our papers mentioned above, and the comments in the code are the entirety of the documentation available. You can reach us at the email addresses mentioned above for other queries. Help is not promised, but if we have time, we can look into it.
