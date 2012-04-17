intersection
============
    
    var intersection = require('intersection');
    var seg2 = {start:{x:-1,y:2}, end:{x:5,y:2}};
    var seg3 = {start:{x:1,y:-1}, end:{x:4,y:4}};

    intersection.intersect(seg2,seg3); 
    // {x:2.8,y:2}

.intersect(a,b)
===============

.intersect(a,b) takes two line segments a and b and returns their point of intersection.
Returns false if they are collinear or parallel.

.describe(a,b)
=========================

.describe(a,b) takes two line segments a and b and returns a 
report about thier co-linearity, if they are parallel, and the intersection
if defined.

    var segA = {start:{x:3,y:0},end:{x:3,y:4}};

    // colinear with segA
    var segA_1 = {start:{x:3,y:-2},end:{x:3, y:9}};

    // parallel but not colinear with seg1
    var segA_2 = {start:{x:1, y:-1}, end:{x:1, y:5}};

    intersection.describe(segA,segA_1);
    // {colinear:true, parallel:true,intersection:undefined}

    intersection.describe(segA,segA_2);
    // {colinear:false, parallel:true,intersection:undefined}

    intersection.describe(segA,segB);
    // {colinear:false, parallel:false, intersection:{x:2.8,y:2}


.isParallel(a,b)
================

Returns true if a and b are parallel line segments, false otherwise.

.isCollinear(a,b)
================

Returns true if a and b are collinear line segments, false otherwise.
Collinear segments means the segments lie on the same line.

Notes
=====
    
.intersect returns false if the two segments are co-linear or parallel.


Notes II
========
    
Intersection utilizes the fast cross-product method as outlined by Ronald Grahm
in "Graphics Gems I".

Test Results and Benchmarks
===========================

From nodeunit test/test.js

    nodeunit test.js 

    test.js
    ✔ descriptionTest
    ✔ basicTest
    ✔ safeIntersectionTest
    ✔ testReadmeExamples

    OK: 13 assertions (21ms)



TODO
====

There is a speed boost outlined by Mukesh Prasad in "Graphics Gems II" utilizing a same-side sign test.
