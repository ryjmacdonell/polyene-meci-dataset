Polyene MECI dataset
====================
A dataset of optimized minima and minimum-energy conical intersections of
polyenes (ethylene, 1,3-butadiene, 1,3,5-hexatriene and 1,3-cyclohexatriene)
and their amino- and cyano-substituted derivatives.

Usage
-----
All data is organized in json files. The data is all contained in
all_poly.json, and each directory contains a json file
with a subset of the data for convenience. The molecule directories also
contain xyz files with geometry labels.

Most of the data was calculated at using MR-CIS/6-31G* with a small active
space. It is sufficient for describing the localized MECI electronic structure,
and can be used as guess geometries for larger calculations.

Structure
---------
The json files are organized as follows:

- [bkb-label]: a unique label for the backbone with the prefix 'x'
    - bkb-name: the backbone molecule name
    - bkb-ncarbon: the number of carbons in the backbone
    - mols: molecules corresponding to the backbone
        - [mol-label]: a unique label for the molecule
            - name: the molecule name
            - formula: the molecule empirical formula
            - sub: the substituent ("none" if no substituents)
                - label: the substituent label
                - name: the substituent name
                - position: the position of the substituent on the backbone
            - lot: the level of theory
                - label: a label for the level of theory
                - method: the electronic structure method
                - basis: the atomic orbital basis set
                - nelec: the number of electrons in the CAS
                - ncas: the number of orbitals in the CAS
                - nstate: the number of CASSCF states
            - opts: optimized geometries
                - [opt-label]: a unique label for the geometry
                    - name: the name of the optimized geometry
                    - type: the geometry type (min: minimum, et: ethylenic MECI, kd: kinked-diene MECI)
                    - n-ind: the central carbon index for pyr/tr MECIs
                    - db-ind: the carbon index doubly-bonded to n
                    - sb-ind: the carbon index single-bonded to n
                    - energy: the state energies in a.u.
                    - atm: the atom labels
                    - xyz: the atom cartesian coordinates in a.u.
                    - h01: the nonadiabatic coupling vector in a.u.
                    - g01: the gradient difference vector in a.u.
                    - ih-charges: iterative Hirshfeld charges in e

Note on charges
---------------
Iterative Hirshfeld charges of MECIs were calculated by displacing the molecule
by 1 pm along g01 to separate the states, then selecting the state whose
character corresponds to S1 of butadiene approaching the MECI. If the
state characters remained unresolved, h01 was used instead.

Author
------
Ryan J. MacDonell, Dec. 2019
