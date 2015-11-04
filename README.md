# g2clib
<pre>
                                                           August 06, 2013
                                                           W/SIB:VUONG


g2clib Library.

This library contains "C" decoder/encoder
routines for GRIB edition 2.  The user API for the GRIB2 routines
is described in file "grib2c.doc".

This "C" source code conatins many uses of the C++
comment style "//".  Please make sure you include the
appropriate compiler option in the CFLAGS variable in the
makefile to allow the use of "//" comment indicators.


We have added support for PNG and JPEG2000 image compression
algorithms within the GRIB2 standard.  If you would like
to compile this library to utilize these GRIB2 Templates,
make sure that -DUSE_PNG and -DUSE_JPEG2000 are specified
in the DEFS variable in the makefile.  You will also need
to download and install the external libraries listed below,
if they are not already installed on your system.

If you do not wish to bother with the external libs and
don't need PNG and JPEG2000 support, you can remove the
-DUSE_PNG and -DUSE_JPEG2000 flags from the DEFS variable 
in the makefile.


-------------------------------------------------------------------------------

     External Libraries:

libjasper.a - This library is a C implementation of the JPEG-2000 Part-1 
              standard (i.e., ISO/IEC 15444-1).  This library is required
              if JPEG2000 support in GRIB2 is desired.  If not, remove
              the -DUSE_JPEG2000 option from the DEFS variable 
              in the makefile.

              Download version jasper-1.900.1 from the JasPer Project's
              home page, http://www.ece.uvic.ca/~mdadams/jasper/.
        
              More information about JPEG2000 can be found at 
              http://www.jpeg.org/JPEG2000.html.

libpng.a      This library is a C implementation of the Portable Network
              Graphics PNG image compression format.  This library is required
              if PNG support in GRIB2 is desired.  If not, remove
              the -DUSE_PNG option from the DEFS variable
              in the makefile.
              
              If not already installed on your system, download version 
              libpng-1.2.44 from http://www.libpng.org/pub/png/libpng.html.

              More information about PNG can be found at 
              http://www.libpng.org/pub/png/.

libz.a        This library contains compression/decompression routines
              used by libpng.a for PNG image compression support. 
              This library is required if PNG support in GRIB2 is desired.  
              If not, remove the -DUSE_PNG option from the DEFS variable
              in g2lib/makefile.

              If not already installed on your system, download version 
              zlib-1.2.6 from http://www.gzip.org/zlib/.
</pre>
