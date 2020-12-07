## PROJECT CONTRIBUTORS

Hoang Trung Hieu (hieu.ht183915@sis.hust.edu.vn)

Nguyen Tien Thanh (nguyenthanh@soict.hust.edu.vn)

Nguyen Khanh Van (vannk@soict.hust.edu.vn)

Bui Manh Cuong

Le Vinh Nhon (nhon.lv176841@sis.hust.edu.vn)

Nguyen Chi Hieu

## LICENSE / USE

The javatuples repository contains a collection of network topologies, which are not our work. All other code / scripts / materials are original contributions of the above contributors, and are released under the MIT LICENSE (see "./LICENSE"). 

We would appreciate you citing this code and the most relevant of our associated research publications below.

## BACKGROUND

The following research paper (with their BibTex entries) explain the ideas behind this tool:

A Reduction Model For Simulating Large-Scale Interconnection Network (Nguyen Tien Thanh, Nguyen Khanh Van, Bui Manh Cuong)

## CONTENTS AND STRUCTURE

Directory listing:

* common:

* config

* custom:

* events:

* infrastructure

* javatuples

* network

* results

* routing

* simulator

* weightedloadexperiment

gnuplotscripts -- contains gnuplot plot files corresponding to some plots in our above papers (mostly (2)).
lpmaker -- Java code which has a large number of graphs (in the 'graphs' subdir) and writes out the linear program for throughput for given graph parameters and traffic matrices (a few of which are encoded in Graph.java).
plots -- This is where you'll find the plots in pdf format after you've run some scripts.
resultfiles -- The text output from the scripts which 'gnuplotscripts' use to output 'plots'.
scripts -- Contains a few scripts to generate results that appear in our papers.
topology -- Temporary data holding directory where the linear program files are stored before they're run.
upperBound -- Code for the upper bound on throughput; details in paper (2) above.
graphRepo -- Several networks that we found in the public domain and tested. A description of the topologies is in graphRepo/sources.txt, and the appropriate references are cited in graphRepo/references.pdf. We are grateful to all the researchers that have made these network topologies available.

INSTRUCTIONS FOR USE
--------------------
1.  You must have a linear program solver that accepts the standard LP format used by multiple available solvers. By default, our code uses the Gurobi solver (http://www.gurobi.com/) which is available free to academics. If you want to use a different solver, you'll need to rewrite scripts/lpRun.sh accordingly. If you want a solver that uses a different LP format, more extensive changes will be needed in Graph.java, where you'll modify the 'PrintGraphforMCFFairCondensed' method. If you're using Gurobi, please ensure that you can run it from the command line as 'gurobi_cl <a file containing some test linear program>'. Instructions for setting up Gurobi can be found on their website (and keep evolving over time).

2.  If you've accomplished #1 above, you can quickly get something running and test that our code is working as expected, by changing to the 'scripts' directory and executing:
	
	./fatCompare.sh

After execution, check the 'plots' directory for fatCompare.pdf. The values > 1 indicate that many more servers could have been added to Jellyfish while still achieving full throughput. Note that the script runs only 3 sizes for comparison with only 3 runs each for this quick demo. You can look at fatCompare.sh and uncomment a clearly marked line to be able to run the comparison for many sizes, and see a more meaningful plot result.

3.  The other scripts in 'scripts' plot various other results from our papers. The clean.sh script deletes all temporary / data / result / plot files. The lpRun.sh script has already been discussed above.

4.  You can write similar scripts to the ones in 'scripts' to run the multitude of graph types we have made available in lpmaker/graphs. All the results in our papers have been generated using variations of these scripts!

5.  Paper (3) includes results on a large number of real-world graphs. These can be found in 'graphrepo'.

NOTES
-----
* Error handling is poor at this time. For example, if you're running networks that are too large, there will be memory errors etc. These have not been gracefully handled so far.

* In order to support scalability under all-to-all traffic, a simplified version of the LP has been added. While both the LPs yield the same result, the new version runs faster under dense traffic matrices such as all-to-all. Please note that the results in the papers were computed using the old version.

* This README, another README in upperBound, our papers mentioned above, and the comments in the code are the entirety of the documentation available. You can reach us at the email addresses mentioned above for other queries. Help is not promised, but if we have time, we can look into it.

* The scripts use gnuplot 4.4 or higher (for the pdfcairo terminal). But if you don't have it, you can still get the result files in 'resultfiles' and plot them whichever way you like.

* Facebook traffic matrices were retrieved from Roy et. al. [SIGCOMM'15]. We derive approximate relative weights through image processing on the traffic heatmaps. Please mail us to obtain these TMs. Absolute traffic values are not available.
