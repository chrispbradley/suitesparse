#-----------------------------------------------------------------------------
# compile the CCOLAMD demo
#-----------------------------------------------------------------------------

default: ccolamd_example ccolamd_l_example

include ../../SuiteSparse_config/SuiteSparse_config.mk

I = -I../Include -I../../SuiteSparse_config

C = $(CC) $(CF) $(I)

LIB2 = ../../SuiteSparse_config/libsuitesparseconfig.a $(LIB)

library:
	( cd ../../SuiteSparse_config ; $(MAKE) )
	( cd ../Lib ; $(MAKE) )

#------------------------------------------------------------------------------
# Create the demo program, run it, and compare the output
#------------------------------------------------------------------------------

dist:

ccolamd_example: ccolamd_example.c library
	$(C) -o ccolamd_example ccolamd_example.c ../Lib/libccolamd.a $(LIB2)
	- ./ccolamd_example > my_ccolamd_example.out
	- diff ccolamd_example.out my_ccolamd_example.out

ccolamd_l_example: ccolamd_l_example.c library
	$(C) -o ccolamd_l_example ccolamd_l_example.c ../Lib/libccolamd.a $(LIB2)
	- ./ccolamd_l_example > my_ccolamd_l_example.out
	- diff ccolamd_l_example.out my_ccolamd_l_example.out

#------------------------------------------------------------------------------
# Remove all but the files in the original distribution
#------------------------------------------------------------------------------

clean:
	- $(RM) $(CLEAN)

purge: distclean

distclean: clean
	- $(RM) ccolamd_example ccolamd_l_example
	- $(RM) my_ccolamd_example.out my_ccolamd_l_example.out
	- $(RM) -r *.dSYM
