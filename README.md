# QUIPforLAMMPS
Interface between QUIP (http://www.libatoms.org) and LAMMPS (http://lammps.sandia.gov/) MD codes

Syntax:
pair_style quip

Examples:

pair_style      quip
pair_coeff      * * gap_example.xml "Potential xml_label=GAP_2014_5_8_60_17_10_38_466" 14
pair_coeff      * * sw_example.xml "IP SW" 14

Description:

Style quip provides an interface for calling potential routines from the QUIP
package. QUIP is built separately, and then linked to LAMMPS. The most recent
versionof the QUIP package can be downloaded from GitHub:
https://github.com/libAtoms/QUIP. The interface is chiefly intended to be used
to run Gaussian Approximation Potentials (GAP), which are described in the
following publications: Bartok_2010 and Bartok_PhD, see below.

A QUIP potential is specified by the filename which contains the parameters of
the potential in XML format, the initialisation string, and the map of atomic
numbers.

GAP potentials can be obtained from the Data repository section of
http://www.libatoms.org/, where the appropriate initialisation strings are also
advised. The map of atomic numbers must match the map in the LAMMPS data file
and the potential must be capable of describing the interactions of the given
atom types.

Two examples are provided in the examples/USER/quip directory.


Mixing, shift, table, tail correction, restart, rRESPA info:

This pair style does not support the pair_modify mix, shift, table, and tail options.

This pair style does not write its information to binary restart
files, since it is stored in potential files.  Thus, you
need to re-specify the pair_style and pair_coeff commands in an input
script that reads a restart file.

This pair style can only be used via the pair keyword of the
run_style respa command.  It does not support the inner, middle, outer keywords.

Restrictions:

QUIP potentials are parametrised for real units and therefore LAMMPS must also
be run with real units.

Publications:

Bartok_2010: AP Bartok, MC Payne, R Kondor, and G Csanyi, Physical Review Letters 104, 136403 (2010)
Bartok_PhD: A Bartok-Partay, PhD Thesis, University of Cambridge, 2010
