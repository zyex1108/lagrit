Directory to hold LaGriT executable files.
Online release notes: http://lagrit.lanl.gov/release.shtml
Release notes and versions are also written in README.txt and Versions.txt

=======================================================================
As of November 2012 

LaGriT is now compiling with new exodus libraries (see dump/exo):
    http://sourceforge.net/projects/exodusii/files/
      Exodus II 5.22b
      HDF5 version 1.8.6
      netcdf-4.1.3
      Contact: Greg Sjaardema, Sandia National Laboratories, gdsjaar@sandia.gov

The build organization has been modified to allow the new exo libs.
Directory structure: 
   build_lagrit/
         bin/  
         build_lagrit/
                  lagrit/  
                     lib/  src/
                  lg_util/
                     lib/  src/
                  exodus/  
                     src/ lin32/ lin64/ mac32/ mac64/ run_lin32.sh* run_lin64.sh* run_mac64.sh*  


=======================================================================
LaGriT V3.100 Nov 2012 - added copyright in preparation for Release 3.1

Note: discovered metis libs are not working for 64 bit codes, 32 bit are fine.

changeset:   285:52e0c01f812f
tag:         tip
user:        Terry Miller <tamiller@lanl.gov>
date:        Fri Nov 16 09:37:21 2012 -0700
summary:     Commit tested LaGriT V3.100 Linux m64 date_compile: 2012/07/23
gfort 4.5

Date:   November 16 and 19, 2012 9:39:20 AM MST

Compiled and Passed test/level01:
-rwxr-xr-x 1 tam sft   22485691 Nov 16 10:33 lagrit_lin64_g_gfort4.5
-rwxr-xr-x 1 tam sft   15874141 Nov 19 12:50 lagrit_lin64_o_gfort4.5

-rwxr-xr-x 1 tam sft   19162251 Nov 19 12:50 lagrit_lin32_g_gfort4.5
-rwxr-xr-x 1 tam sft   14007039 Nov 19 12:50 lagrit_lin32_o_gfort4.5

-rwxr-xr-x 1 tam sft   14759432 Nov 16 14:56 lagrit_maci64_g_gfort4.6
-rwxr-xr-x 1 tam sft   12139488 Nov 19 13:13 lagrit_maci64_o_gfort4.6

*               *                                             *
*               *    Program:  LaGriT V3.100   Linux m64      *
*               *    date_compile: 2012/10/31   dev vers      *
*               *    Run Time: 2012/Nov 19  14:53:56          *
*               *    Manual:   http://lagrit.lanl.gov         *
*               *                                             *
*               * * * * * * * * * * * * * * * * * * * * * * * *

                               -----oOo-----
                           LaGriT V3 LACC-2012-084

============================================================
Version 3.006 Release for linux and mac with 64 and 32 bit
This is the version submitted to codes.lanl.gov for copyright release.
Once the copyright is sent, this will be recompiled into a new
version 3.1 for distribution by LANL Codes.

*               *                                             *                 
*               *    Program:  LaGriT V3.006   Linux m64      *                 
*               *    date_compile: 2012/07/26  gfort 4.5      *                

Now includes netcdf and exodus libs for writing exodus mesh 
files and reading and writing facesets.
Dump exodus files with/without facesets, fast/slow options:
Syntax:
  dump / exo / ifile / cmoname / facesets / on
  dump / exo / ifile / cmoname / facesets / off
  dump /exo / ifile / cmoname / facesets / on file1,file2,...filen
  dump /exo / ifile / cmoname / facesets / off file1,file2,...filen

Added line sort by nodes or elements for creating valid polygons 
that can be read and used by other routines. 
Syntax:
  sort / line_graph / cmo / ascending | descending / [key] / [nodes/elements]

Added option for massage to refine based on an attribute field. 
Syntax:
  massage / [bisection length/field name] / merge_length / toldamage / ...

Under development massage2 syntax for incremental refinement strategies.
Syntax in work: 
  massage2/ [file name] / [Target Length Scale]/[field name]/ &
     merge_length/toldamage/[tolroughness]/[ifirst,ilast,istride]/ ...

Code improvements related to recon 0 and recon 1 will 
result in slightly different but better connectivity results.

Memory and bug fixes related to 64 bit code changes.
Improved error catching for common routines.

============================================================
Version 3.001 Release (linux only)

Major changes to most parts of the code to enable 64 bit compile.
Added memory / print option as check for correct linking for 64 bit.
Added additional memory and error checking.

This version includes the ability to read and write Exodus files.
See COPYRIGHT statements at end of this file.



============================================================
Version 2.200 Release

*               *                                             *                 
*               *    Program:  LaGriT V2.200   Linux m32      *                 
*               *    date_compile: 2010/11/22                 *     

This is the last major release before code is changed for 64 bit work.

dump/fehm, dump/zone_outside
Write outside area vectors based on voronoi instead of median connections.

cmo/addatt/voronoi_varea
create node attributes xn_varea, yn_varea, zn_varea indicating triangle face directions.

interpolate/
Changed interpolate to "find" more points on edges
this will permit nodes to find a nearest edge or point and be
"inside" the triangle for extreme small or large numbers where
epsilon values are difficult to evaluate correctly.
Fixed bug that sometimes saved wrong candidate number not associated
with the value that was used. Can happen where multiple candidates
are found for the sink node, and where the first is not used. 

extract/surfmesh
Now creates attributes to hold element local face numbers of 3D input
mesh that occur on either side of output mesh face, idface0 and idface1.
Now copies user-created node-based attributes from source.

dump 2 and 3 token for avs, lagrit, gmv


============================================================
Version 2.106 Release


*               *    Program:  LaGriT V2.106   Linux m32      *
*               *    date_compile: 2010/06/29                 *


New code wrappers include  
cmo/attribute_union
read for 3 tokens 
compute / linear_extrapolate
grid2grid/ tree_to_fe 
grid2grid/ quadtotri4 

Added error checking to associated routines 

============================================================
Version 2.105 Release
Minor update to LaGriT library with enhancements to the pset routine
and adding ccoef attributes when writing stor files.

*               * * * * * * * * * * * * * * * * * * * * * * * *                 
*               *                                             *                 
*               *    Program:  LaGriT V2.105   Linux m32      *                 
*               *    date_compile: 2010/05/25                 *                 
*               *    Run Time: 2010/05/26  08:24:46           *                 
*               *    Manual:   http://lagrit.lanl.gov         *                 
*               *                                             *                 
*               * * * * * * * * * * * * * * * * * * * * * * * *             

includes linux, maci, and sun
 

============================================================
Version 2.100 Release
This is a major update to LaGriT and the lg_util library. 
Major changes have been made in the core memory management routines to allow 
development for a 64 bit release.  These changes will be invisible to most users 
but allows better reporting of errors and memory usage for useful diagnostic information.

NOTE: SUNOS has been updated to Studio 11 
      you must use libs for Studio 10 or higher running on OS 8 or higher
      use % source /n/env/local.sunwspro.11


*               * * * * * * * * * * * * * * * * * * * * * * * *                 
*               *                                             *                 
*               *    Program:  LaGriT V2.100   Linux m32      *                 
*               *    date_compile: 2009/08/03                 *                 
*               *    Run Time: 2009/08/14  10:31:26           *                 
*               *    Manual:   http://lagrit.lanl.gov         *                 
*               *                                             *                 
*               * * * * * * * * * * * * * * * * * * * * * * * *                


lin = Linux with Absoft 10.0 32bit Fortran 95 9.0
Linux rainier 2.6.9-55.0.2.ELlargesmp #1 SMP Tue Jun 12 18:09:16 EDT 2007 x86_64 x86_64 x86_64 GNU/Linux

maci = MAC OSX on intel with Absoft 10.2 
Darwin sundog.lanl.gov 9.7.0 Darwin Kernel Version 9.7.0: Tue Mar 31 22:52:17 PDT 2009; root:xnu-1228.12.14~1/RELEASE_I386 i386

mac = MAC OSX with Absoft 9.5
Darwin darmok.lanl.gov 9.7.0 Darwin Kernel Version 9.7.0: Tue Mar 31 22:54:29 PDT 2009; root:xnu-1228.12.14~1/RELEASE_PPC Power Macintosh

sun = Solaris 10 with Studio 11 
SunOS flow 5.10 Generic_137137-09 sun4u sparc SUNW,Sun-Fire-880

--

SunOS SUNWspro forte 7 no longer supported
voronoi 5.9 Generic_122300-02 sun4u sparc SUNW,Sun-Blade-1000 
sgi, sgi32, and sgi64 IRIX64 are no longer supported but included

===============================================================
VERSION 2.004

New mac compile on intel version of MAC OS X
*               * * * * * * * * * * * * * * * * * * * * * * * *                 
*               *                                             *                 
*               *    Program:  LaGriT V2.004   Darwin intel   *                 
*               *    date_compile: 2009/02/02                 *                 
*               *    Run Time: 2009/02/04  08:42:07           *                 
*               *    Manual:   http://lagrit.lanl.gov         *                 
*               *                                             *                 
*               * * * * * * * * * * * * * * * * * * * * * * * *        


New mac compile allows debug version to run on intel and powerpc
Still reporting memory issues running on mac notebook 
-rwxr-xr-x  1 tam  pf     16454372 Nov 12 10:04 lagrit_mac_g
*               * * * * * * * * * * * * * * * * * * * * * * * *                 
*               *                                             *                 
*               *    Program:  LaGriT V2.004   Darwin         *                 
*               *    date_compile: 2008/11/05                 *                 
*               *    Run Time: 2008/11/12  10:07:46           *                 
*               *    Manual:   http://lagrit.lanl.gov         *                 
*               *                                             *                 
*               * * * * * * * * * * * * * * * * * * * * * * * *                 


-rwxr-xr-x  1 tam radiusd  6764016 Oct 22 08:12 lagrit_mac_o*
-rwxr-xr-x  1 tam radiusd 13419232 Oct 22 08:12 lagrit_mac_g*
-rwxr-xr-x  1 tam radiusd 11114912 Oct 21 14:50 lagrit_sun_o*
-rwxr-xr-x  1 tam radiusd 35258368 Oct 21 14:50 lagrit_sun_g*
-rwxr-xr-x  1 tam radiusd  9411367 Oct 21 13:50 lagrit_lin_o*
-rwxr-xr-x  1 tam radiusd 13933505 Oct 21 13:49 lagrit_lin_g*
-rwxr-xr-x  1 tam radiusd  7649544 Oct 21 13:17 lagrit_sgi_o*
-rwxr-xr-x  1 tam radiusd 11586984 Oct 21 13:17 lagrit_sgi_g*
-rwxr-xr-x  1 tam radiusd  7649544 Oct 21 12:40 lagrit_sgi32_o*
-rwxr-xr-x  1 tam radiusd 11586984 Oct 21 12:40 lagrit_sgi32_g*

*               * * * * * * * * * * * * * * * * * * * * * * * *                 
*               *                                             *                 
*               *    Program:  LaGriT V2.004   Linux          *                 
*               *    date_compile: 2008/10/21                 *                 
*               *    Run Time: 2008/10/22  08:46:51           *                 
*               *    Manual:   http://lagrit.lanl.gov         *                 
*               *                                             *                 
*               * * * * * * * * * * * * * * * * * * * * * * * *                 

===============================================================
VERSION 2.003

-rwxr-xr-x  1 tam radiusd  9396172 Oct 21 12:39 lagrit_lin_o*
-rwxr-xr-x  1 tam radiusd  6755824 Oct 21 12:40 lagrit_mac_o*
-rwxr-xr-x  1 tam radiusd  7649544 Oct 21 12:40 lagrit_sgi32_o*
-rwxr-xr-x  1 tam radiusd 11103024 Oct 21 12:40 lagrit_sun_o*
-rwxr-xr-x  1 tam radiusd 13918626 Oct 21 12:39 lagrit_lin_g*
-rwxr-xr-x  1 tam radiusd 13412960 Oct 21 12:40 lagrit_mac_g*
-rwxr-xr-x  1 tam radiusd 11586984 Oct 21 12:40 lagrit_sgi32_g*
-rwxr-xr-x  1 tam radiusd 35217408 Oct 21 12:40 lagrit_sun_g*

*               * * * * * * * * * * * * * * * * * * * * * * * *                 
*               *                                             *                 
*               *    Program:  LaGriT V2.003   Linux          *                 
*               *    date_compile: 2008/05/15                 *                 
*               *    Run Time: 2008/10/21  12:57:11           *                 
*               *    Manual:   http://lagrit.lanl.gov         *                 
*               *                                             *                 
*               * * * * * * * * * * * * * * * * * * * * * * * *                 



===============================================================
VERSION 2.001

Initial optimized set:
-rwxrwxrwx   1 tam       9360587 Oct 18 11:13 lagrit_lin_o*
-rwxrwxrwx   1 tam       6702048 Oct 18 12:01 lagrit_mac_o*
-rwxrwxrwx   1 tam      11527448 Oct 18 10:51 lagrit_sun_o*

Initial debug set:
-rwxrwxrwx   1 tam      13953260 Oct 18 11:13 lagrit_lin_g*
-rwxrwxrwx   1 tam      16501004 Oct 18 12:01 lagrit_mac_g*
-rwxrwxrwx   1 tam      35241984 Oct 18 10:51 lagrit_sun_g*

Dated set:
-rwxrwxrwx   1 tam      13953260 Oct 18 11:13 lagrit_lin_g_071018*
-rwxrwxrwx   1 tam       9360587 Oct 18 11:13 lagrit_lin_o_071018*
-rwxrwxrwx   1 tam      16501004 Oct 18 12:01 lagrit_mac_g_071018*
-rwxrwxrwx   1 tam       6702048 Oct 18 12:01 lagrit_mac_o_071018*
-rwxrwxrwx   1 tam      35241984 Oct 18 10:51 lagrit_sun_g_071018*
-rwxrwxrwx   1 tam      11527448 Oct 18 10:51 lagrit_sun_o_071018*

Initial Program Header:

*               * * * * * * * * * * * * * * * * * * * * * * * *                 
*               *                                             *                 
*               *    Program:  LaGriT V2.001   Linux          *                 
*               *    Compiled: 2007/10/18                     *                 
*               *    Run Time: 2007/11/20  11:48:35           *                 
*               *    Manual:   http://lagrit.lanl.gov         *                 
*               *                                             *                 
*               * * * * * * * * * * * * * * * * * * * * * * * *                 
 
                               -----oOo-----                                    
LaGriT Copyright: This program was prepared by Los Alamos National Security, LLC
at Los Alamos National Laboratory (LANL) under contract No. DE-AC52-06NA25396   
with the U.S. Department of Energy (DOE). All rights in the program are reserved
by the DOE and Los Alamos National Security, LLC. Permission is granted to the  
public to copy and use this software without charge, provided that this Notice  
and any statement of authorship are reproduced on all copies. Neither the       
U.S. Government nor LANS makes any warranty, express or implied, or assumes     
any liability or responsibility for the use of this software.                   
                               -----oOo-----                                    

LaGriT can read and write exodus files by way of external libraries.
The following copyrights are included for the purpose of binary distribution.
LaGrit does not distribute these libraries or their source.

                               -----oOo-----                                    

exodusii-5.09/exodusii/COPYRIGHT
Copyright (c) 2005 Sandia Corporation. Under the terms of Contract
DE-AC04-94AL85000 with Sandia Corporation, the U.S. Governement
retains certain rights in this software.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are
met:

    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.

    * Redistributions in binary form must reproduce the above
      copyright notice, this list of conditions and the following
      disclaimer in the documentation and/or other materials provided
      with the distribution.  

    * Neither the name of Sandia Corporation nor the names of its
      contributors may be used to endorse or promote products derived
      from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
"AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

                               -----oOo-----                                    

netcdf-4.1.3/COPYRIGHT
Copyright 1993-2004 University Corporation for Atmospheric Research/Unidata

Portions of this software were developed by the Unidata Program at the 
University Corporation for Atmospheric Research.

Access and use of this software shall impose the following obligations
and understandings on the user. The user is granted the right, without
any fee or cost, to use, copy, modify, alter, enhance and distribute
this software, and any derivative works thereof, and its supporting
documentation for any purpose whatsoever, provided that this entire
notice appears in all copies of the software, derivative works and
supporting documentation.  Further, UCAR requests that the user credit
UCAR/Unidata in any publications that result from the use of this
software or in any product that includes this software, although this
is not an obligation. The names UCAR and/or Unidata, however, may not
be used in any advertising or publicity to endorse or promote any
products or commercial entity unless specific written permission is
obtained from UCAR/Unidata. The user also understands that
UCAR/Unidata is not obligated to provide the user with any support,
consulting, training or assistance of any kind with regard to the use,
operation and performance of this software nor to provide the user
with any updates, revisions, new versions or "bug fixes."

THIS SOFTWARE IS PROVIDED BY UCAR/UNIDATA "AS IS" AND ANY EXPRESS OR
IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL UCAR/UNIDATA BE LIABLE FOR ANY SPECIAL,
INDIRECT OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING
FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT,
NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION
WITH THE ACCESS, USE OR PERFORMANCE OF THIS SOFTWARE.

