# Water Jug Problem
Water Jug Problem is a famous puzzle that has many variations. One of the most famous one is that you are given 3-gallon bucket, 4-gallon bucket and unlimited supply of water. You are allowed to empty and fill the buckets and pour from one to another one. How can you measure 2 gallons of water using the two buckets?

In case you haven't come up with the solution yet. Here it is. Let (bucket1, bucket2) be the amount of water in each bucket, then <a href="https://www.codecogs.com/eqnedit.php?latex=(0,0)\rightarrow&space;(0,4)\rightarrow(3,1)\rightarrow(0,1)\rightarrow(1,0)\rightarrow(1,4)\rightarrow(3,2)\rightarrow(0,2)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(0,0)\rightarrow&space;(0,4)\rightarrow(3,1)\rightarrow(0,1)\rightarrow(1,0)\rightarrow(1,4)\rightarrow(3,2)\rightarrow(0,2)" title="(0,0)\rightarrow (0,4)\rightarrow(3,1)\rightarrow(0,1)\rightarrow(1,0)\rightarrow(1,4)\rightarrow(3,2)\rightarrow(0,2)" /></a> to get 2 gallons in 4-gallon bucket.

That was easy, but what happens when you have <a href="https://www.codecogs.com/eqnedit.php?latex=m" target="_blank"><img src="https://latex.codecogs.com/gif.latex?m" title="m" /></a>-gallon and <a href="https://www.codecogs.com/eqnedit.php?latex=n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n" title="n" /></a>-gallon bucket?

## Can you measure all numbers of gallons up to n with m-gallon and n-gallon bucket?
You can measure all numbers of gallons up to n as long as <a href="https://www.codecogs.com/eqnedit.php?latex=m" target="_blank"><img src="https://latex.codecogs.com/gif.latex?m" title="m" /></a> and <a href="https://www.codecogs.com/eqnedit.php?latex=n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n" title="n" /></a> are relatively prime, that is <a href="https://www.codecogs.com/eqnedit.php?latex=GCD(m,n)=1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?GCD(m,n)=1" title="GCD(m,n)=1" /></a>. If <a href="https://www.codecogs.com/eqnedit.php?latex=m" target="_blank"><img src="https://latex.codecogs.com/gif.latex?m" title="m" /></a> and <a href="https://www.codecogs.com/eqnedit.php?latex=n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n" title="n" /></a> are not relatively prime, you can measure only number of gallons that are multiples of their greatest common divisor.

<p align="center">
  <img src="https://github.com/marie-yau/Algorithmic-Projects/blob/master/images/(3%2C5)%20and%20(3%2C6)%20solutions.png" width="600" title="Github Logo">
</p>

## How do you find a solution that measures x number of gallons?
You have to create a tree, where every node holds number of gallons in each bucket <a href="https://www.codecogs.com/eqnedit.php?latex=(x,y)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(x,y)" title="(x,y)" /></a> and has six branches. Every branch stands for one allowed move – fill bucket1, fill bucket2, empty bucket1, empty bucket2, pour from bucket1 to bucket2, pour from bucket2 to bucket1. If the new <a href="https://www.codecogs.com/eqnedit.php?latex=(x,y)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(x,y)" title="(x,y)" /></a> combination is already in the tree (you can use breadth search first to find it), do not add it to the tree.
You can stop building your tree once there are no other nodes to add or once you find <a href="https://www.codecogs.com/eqnedit.php?latex=m" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x" title="x" /></a> number of gallons in one bucket.

## Is there anything special about the tree?
Every tree has <a href="https://www.codecogs.com/eqnedit.php?latex=\frac{2(m&plus;n)}{GCD(m,n)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{2(m&plus;n)}{GCD(m,n)}" title="\frac{2(m+n)}{GCD(m,n)}" /></a> nodes. That is because the tree contains every possible combination <a href="https://www.codecogs.com/eqnedit.php?latex=(x,y)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(x,y)" title="(x,y)" /></a> exactly once.
Every tree has 2 main branches one from fill bucket1 and the other one from fill bucket2. Both branches have the same length <a href="https://www.codecogs.com/eqnedit.php?latex=\frac{m&plus;n}{2}-1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{m&plus;n}{2}-1" title="\frac{m+n}{2}-1" /></a>. 

<p align="center">
  <img src="https://github.com/marie-yau/Algorithmic-Projects/blob/master/images/(3%2C5)%20graph%2C%20tree.png" width="600" title="Github Logo">
</p>

You can see how tree looks like on Figure 2b. Figure 2a shows plotted graph in xy-coordinates. 

## Is there anything special about the bucket operations?
At any given moment at least one bucket is either full or empty. For example, when there are buckets <a href="https://www.codecogs.com/eqnedit.php?latex=(3,5)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(3,5)" title="(3,5)" /></a>, it is not possible to get combination <a href="https://www.codecogs.com/eqnedit.php?latex=(2,2)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(2,2)" title="(2,2)" /></a>.

Because at any given moment at least one bucket is either full or empty, all bucket operations are reversible. Every operation has its inverse (fill bucket1 - empty bucket1, fill bucket2 - empty bucket2, pour from bucket1 to bucket2 - pour from bucket2 to bucket1). For example, when there are buckets <a href="https://www.codecogs.com/eqnedit.php?latex=(3,5)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(3,5)" title="(3,5)" /></a> and the current combination is <a href="https://www.codecogs.com/eqnedit.php?latex=(2,2)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(3,2)" title="(3,2)" /></a>. When you pour from bucket1 to bucket2, you get <a href="https://www.codecogs.com/eqnedit.php?latex=(2,2)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(0,5)" title="(0,5)" /></a>. This operation can be reversed by pouring from bucket2 to bucket1. Then you get <a href="https://www.codecogs.com/eqnedit.php?latex=(2,2)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(3,2)" title="(3,2)" /></a> and that is the combination you had before applying pour from bucket1 to bucket2.

## How is the graph plotted in xy-coordinates?
See the animation below. Every move stands for one of the allowed operations - fill bucket1, fill bucket2, empty bucket1, empty bucket2, pour from bucket1 to bucket2 and pour from bucket2 to bucket1. Note that the animation doesn't contain <a href="https://www.codecogs.com/eqnedit.php?latex=(m,n)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(m,n)" title="(m,n)" /></a> because this point can be in either branch and it was distracting from the symmetry.
<p align="center">
  <img src="https://github.com/marie-yau/Algorithmic-Projects/blob/master/images/(3%2C5).gif" width="300" title="Github Logo">
</p>

## Does the plotted graph in xy-coordinates depends on parity of m and n?
Yes, the graph looks different based on parity of m and n:
- m is even, n is odd: The middle vertical line is missing.
- m is odd, n is odd: The middle diagonal is missing.
- m is odd, n is even: The middle horizontal line is missing.
<p align="center">
  <img src="https://github.com/marie-yau/Algorithmic-Projects/blob/master/images/parity.png" width="600" title="Github Logo">
</p>

## Is the plotted graph in xy-coordinates symmetric?
Yes, it is. Note that when you flip point <a href="https://www.codecogs.com/eqnedit.php?latex=(x,y)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(x,y)" title="(x,y)" /></a> about <a href="https://www.codecogs.com/eqnedit.php?latex=\frac{n}{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{n}{2}" title="\frac{n}{2}" /></a> horizontal line and then flip it again about <a href="https://www.codecogs.com/eqnedit.php?latex=\frac{m}{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{m}{2}" title="\frac{m}{2}" /></a> vertical line, you get point <a href="https://www.codecogs.com/eqnedit.php?latex=(m-x,n-y)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(m-x,n-y)" title="(m-x,n-y)" /></a> that is colored with the other color.

<p align="center">
  <img src="https://github.com/marie-yau/Algorithmic-Projects/blob/master/images/equationSymmetry.png" width="600" title="Github Logo">
</p>

## Is it possible to find out last node of each branch of the tree?
Yes. The last element of each branch depends on the parity of m and n. See table below.

<p align="center">
  <img src="https://github.com/marie-yau/Algorithmic-Projects/blob/master/images/tableLastElement.png" width="300" title="Github Logo">
</p>
