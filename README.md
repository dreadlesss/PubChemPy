Convert between molecular names and SMILES
===
Search the smiles by name or search the name by smiles using pubchempy.
For more information: http://pubchempy.readthedocs.io

## 1.Install the Pubchempy
[Pubchempy](http://pubchempy.readthedocs.io) is a python wrapper for the PubChem PUG REST API.
The original codes are placed in the directory named "pubchempy"
Two simple ways to install the pubchempy:
```python
>>> pip install pubchempy
>>> conda install -c mcs07 pubchempy
```

## 2.Search the SMILES by name/CAS
Search the SMILES of Glucose
```python
>>> from pubchempy import get_compounds
>>> results = get_compounds('Glucose', 'name')
>>> print(results)
[Compound(79025), Compound(5793), Compound(64689), Compound(206)]
>>> print(results[0].isomeric_smiles)
>>> C([C@@H]1[C@H]([C@@H]([C@H]([C@H](O1)O)O)O)O)O
```
Search by CAS
```python
>>> results = get_compounds('81982-32-3', 'name')
>>> results
[Compound(71253)]
>>> print(results[0].isomeric_smiles)
'CNS(=O)(=O)C1=C(C=C(C(=C1)C(=O)NCC2CCCN2CC=C)OC)N'
```

## 3.Search the synonyms/iupac_name by SMILES
```python
>>> c = get_compounds('C1=CC2=C(C3=C(C=CC=N3)C=C2)N=C1', 'smiles')
>>> c
[Compound(1318)]
>>> c[0].iupac_name
'1,10-phenanthroline'
>>> c[0].synonyms
['1,10-phenanthroline',
 'o-phenanthroline',
 '66-71-7',...]
```

## 3.Search by cid
```python
>>> from pubchempy import Compound
>>> c = Compound.from_cid(5090)
>>> print(c.isomeric_smiles)
CS(=O)(=O)C1=CC=C(C=C1)C2=C(C(=O)OC2)C3=CC=CC=C3
```

# Other ways to convert between molecular names and SMILES

[PubChem Identifier Exchange Service](https://pubchemdocs.ncbi.nlm.nih.gov/identifier-exchange-service):

ID exchange service support by pubchem.

[ChemPy](https://github.com/bjodah/chempy):

A package written in Python.

[openmolecules](http://www.openmolecules.org/name2structure.html):

This page lets you easily convert compound names, IUPAC names, SMILES codes and CAS numbers into chemical structures.

[ChemAxon](https://docs.chemaxon.com/display/docs/Name_to_Structure.html):

Convert name to structure by toolkits of ChemAxon.

[chemspipy](https://github.com/mcs07/ChemSpiPy):

Python wrapper for the ChemSpider API.
