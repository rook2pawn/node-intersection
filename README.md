intersection
============
    
    var intersection = require('intersection');
    var seg2 = {start:{x:-1,y:2}, end:{x:5,y:2}};
    var seg3 = {start:{x:1,y:-1}, end:{x:4,y:4}};

    intersection.intersect(seg2,seg3); 
    // {x:2.8,y:2}

.descriptionSegments(a,b)
=========================

.descriptionSegments(a,b) takes two line segments a and b and returns a 
report about thier co-linearity, if they are paralell, and the intersection
if defined.

    var segA = {start:{x:3,y:0},end:{x:3,y:4}};

    // colinear with segA
    var segA_1 = {start:{x:3,y:-2},end:{x:3, y:9}};

    // parallel but not colinear with seg1
    var segA_2 = {start:{x:1, y:-1}, end:{x:1, y:5}};

    intersection.descriptionSegments(segA,segA_1);
    // {colinear:true, parallel:true,intersection:undefined}

    intersection.descriptionSegments(segA,segA_2);
    // {colinear:false, parallel:true,intersection:undefined}

    intersection.descriptionSegments(segA,segB);
    // {colinear:false, parallel:false, intersection:{x:2.8,y:2}


Notes
=====
    
.intersect returns false if the two segments are co-linear or parallel.


Notes II
========
    
Intersection utilizes the fast cross-product method as outlined by Ronald Grahm
in "Graphics Gems I".

TODO
====

There is a speed boost outlined by Mukesh Prasad in "Graphics Gems II" utilizing a same-side sign test.
