#!python

import os

# The name of our program
TARGET='grib2c'

env = Environment\
(
    CFLAGS=['-O3'],
    CPPDEFINES={'USE_JPEG2000' : None, 'USE_PNG' : None},
    LINKFLAGS=['-s']
)

# Get the commmand line prefix and add it to the environment
# so we can access it with the "$" later on in this script
vars = Variables()
vars.Add( PathVariable( 'PREFIX', 'Installation Prefix', '/usr/local', PathVariable.PathIsDirCreate ) ) 
vars.Update(env)

# Explicitly define the sources, as there are extras in the folder
# that we do not want built
sources=(\
    'gridtemplates.c',
    'drstemplates.c',
    'pdstemplates.c',
    'gbits.c',
    'g2_unpack1.c',
    'g2_unpack2.c',
    'g2_unpack3.c',
    'g2_unpack4.c',
    'g2_unpack5.c',
    'g2_unpack6.c',
    'g2_unpack7.c',
    'g2_free.c',
    'g2_info.c',
    'g2_getfld.c',
    'simunpack.c',
    'comunpack.c',
    'pack_gp.c',
    'reduce.c',
    'specpack.c',
    'specunpack.c',
    'rdieee.c',
    'mkieee.c',
    'int_power.c',
    'simpack.c',
    'compack.c',
    'cmplxpack.c',
    'misspack.c',
    'jpcpack.c',
    'jpcunpack.c',
    'pngpack.c',
    'pngunpack.c',
    'dec_jpeg2000.c',
    'enc_jpeg2000.c',
    'dec_png.c',
    'enc_png.c',
    'g2_create.c',
    'g2_addlocal.c',
    'g2_addgrid.c',
    'g2_addfield.c',
    'g2_gribend.c',
    'getdim.c',
    'g2_miss.c',
    'getpoly.c',
    'seekgb.c'
)

headers=( 'grib2.h', )

# The installation directory
installDir = '${PREFIX}'

# Fully qualifiy the sources with the path name
absSources = map( lambda x: os.path.join( 'src', x ), sources )

# Fully qualifiy the sources with the path name
absHeaders = map( lambda x: os.path.join( 'src', x ), headers )

staticTarget = env.StaticLibrary(target=TARGET,source=absSources)
sharedTarget = env.SharedLibrary(target=TARGET,source=absSources)

# Build these targets by default
Default( staticTarget, sharedTarget )

# Add installer for libraries
libTarget = os.path.join( installDir, 'lib' )
env.Install( libTarget, [staticTarget,sharedTarget] )
ib = env.Alias( 'install-lib', libTarget )

# Add installer for headers
includeTarget = os.path.join( installDir, 'include' )
env.Install( includeTarget, source=absHeaders )
ih = env.Alias( 'install-include', includeTarget )

# Create an install alias
env.Alias( 'install', [ib, ih] )

