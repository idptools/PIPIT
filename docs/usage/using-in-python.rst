PIPIT in Python
================

PIPIT can also be used within Python. After installing PIPIT, first you need to import PIPIT - 
 
.. code-block:: python

    import pipit
    from pipit import shuffle

Shuffling sequences in Python
------------------------------

To shuffle sequences in Python, use the seq function - 

.. code-block:: python

    shuffle.seq(sequence, start, end)

Where sequence is the sequence you want to shuffle, start is the starting residue number you want to shuffle and end is the number of the final residue you want to shuffle.

**Example**

.. code-block:: python

    shuffle.seq('ACDEFGHIKLMNPQRSTVWY', 5, 15)
    'ACDEHFNMQGLPRKISTVWY'

Additional functionality
-------------------------

**Specifying number of sequnce blocks to shuffle**

If you want to break up your shufled region into multiple discrete shuffled blocks, simply specify 

.. code-block:: python

    shuffle.seq(sequence, start, end, number_blocks=N)

where N is some integer number that is less than the length of the sequence to be shuffled.

**Example***

.. code-block:: python

    shuffle.seq('ACDEFGHIKLMNPQRSTVWY', 5, 16, number_blocks=2)
    ['ACDEIKHFLGMNPQRSTVWY', 'ACDEFGHIKLRQMPSNTVWY']

*Note* - now that multiple sequences are generated, the sequences are returned as a list of strings as opposed to a single string.

**Important** - if the length of the region to be shuffle dis not divisible by the number of blocks specified, a warning will be printed to the user. However, the sequences will still be generated, and the leftover residues will be added to the minimal number of blocks such that the total number of residues equals the length of the region to be shuffled.

Example:

.. code-block:: python

    shuffle.seq('ACDEFGHIKLMNPQRSTVWY', 5, 15, number_blocks=2)
    Warning: specified number of blobs does not result in equal number of residues per blob.
    ['ACDEKFIHGLMNPQRSTVWY', 'ACDEFGHIKLPRMQNSTVWY']

**Specifying a region to keep constant**

If you want to specify a region to *NOT SHUFFLE* as opposed to a region to shuffle (which is the default behavior for PIPIT), simply set inverse=True

Example:

.. code-block:: python

    shuffle.seq('ACDEFGHIKLMNPQRSTVWY', 5, 15, inverse=True)
    ['ECADFGHIKLMNPQRSTVWY', 'ACDEFGHIKLMNPQRVYWST']

When using the inverse flag, each side of the sequence is treated as a sequence block. So in this example, the first sequence shown after the command is used has the first 4 residues shuffled whereas the second sequence has the last 5 residues shuffled. Importantly, the coordinates for teh residues to keep constant include the number specified, so in this example residues 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, and 15 are not shuffled.

**Saving sequences as an output .csv file**

If you want to sve your sequences, you can set save=True. This will result in your sequenecs being saved as a .csv file.

Example:

.. code-block:: python

    shuffle.seq('ACDEFGHIKLMNPQRSTVWY', 5, 15, inverse=True, save=True)

By default, file name will be pipit_NNNNNNNNNN.csv where NNNNNNNNNN is ten random numbers and letters. The random letters and numbers help avoid situations where files are accidentally overwritten. Additionally, the default is to save the file to the current working directory.

**Specifying the file name**

You can specify the name of the generated file by setting output_name="name_of_cool_file". You can add the .csv extension, otherwise PIPIT will add it for you.

Example:

.. code-block:: python

    shuffle.seq('ACDEFGHIKLMNPQRSTVWY', 5, 15, inverse=True, save=True, output_name='my_shuffled_seqs')

**Specifying the output path**

Specifying output path can be done by setting output_path equal to the path to where to save the .csv file. 

Example:

.. code-block:: python

    shuffle.seq('ACDEFGHIKLMNPQRSTVWY', 5, 15, inverse=True, save=True, output_path='/Users/me/Desktop/cool_sequence_folder')

**Removing arbirary sequence names from the generated .csv file**

By default when using PIPIT from Python, the sequences will be arbitrarily named. The original sequence will be called 'original', and each subsequent sequence will be called sequence_variant_# where # is a number starting at 1 that increases per variant generated. If names are not used, the top sequence (or first sequence) is always the original. This can be done by setting seq_names=False

Example:

.. code-block:: python

    shuffle.seq('ACDEFGHIKLMNPQRSTVWY', 5, 15, inverse=True, save=True, seq_names=False)


Copyright (c) 2021, Holehouse Lab - 
Washington University School of Medicine