PIPIT from the Command-line
============================

To use PIPIT from the command-line just use the ``pipit-shuffle`` command. There are 3 required inputs for this command that *must be input in the following order*.

1. The sequence to be shuffled
2. The number of the starting residue of the region of the sequence to either shuffle **which is default** or hold constant **if inverse is specified** (more on that later)
3. The number of the ending residue of the region of the sequence to either shuffle **which is default** or hold constant **if inverse is specified**

Example - 

.. code-block:: bash

    $ pipit-shuffle SSSSMSEGSHPRKTNDDQAN 5 15
    $ ['SSSSMPERNTSKSGHDDQAN']

Importantly, the region specified *to be shuffled* will include the residues specified as the start of the region and the end. So in this example, residues 1, 2, 3, and 4 as well as 16, 17, 18, 19, and 20 will be constant whereas residues 5-15 can be shuffled.

Additonal flags
----------------

``-n`` or ``--number`` will allow you to specify the number of sequence blocks to break up the shuffled region into. *NOTE* - If the number of blocks specified is not compatible with the length of the region to be shuffled, a warning will be printed letting you know. However, the sequences will still be generated, and the leftover residues will be added to the minimal number of blocks such that the total number of residues equals the length of the region to be shuffled.
``-i`` or ``--inverse`` will make it so that the region you specify will be held constant and the regions outside of the specified region will be shuffled.
``-s`` or ``--save`` will allow you to save the output sequences as a .csv file as opposed to simply printing to the terminal.
``-name`` or ``--file_name`` will allow you to specify the name of the output .csv file. If a name is not specified, the default name will be pipit_NNNNNNNNNN.csv where NNNNNNNNNN is ten random numbers and letters. The random letters and numbers help avoid situations where files are accidentally overwritten
``-path`` or ``--output_path`` will allow you to specify the path to which to save the generated .csv file. By default, the file will be saved to the current directory.
``-names`` or ``--seq_names`` will give the generated sequences arbitrary names. The original sequence will be called 'original', and each subsequent sequence will be called sequence_variant# where # is a number starting at 1 that increases per variant generated. If names are not used, the top sequence (or first sequence) is always the original.

**Examples**

Specifying sequence number where the region to be shuffled is divisible by the number of sequence blocks

.. code-block:: bash

    $ pipit-shuffle ACDEFGHIKLMNPQRSTVWY 5 16 -n 2
    $ ['ACDEIFKGLHMNPQRSTVWY', 'ACDEFGHIKLRMQSNPTVWY']

Specifying sequence number where the region to be shuffled is **NOT** divisible by the number of sequence blocks

.. code-block:: bash

    $ pipit-shuffle ACDEFGHIKLMNPQRSTVWY 5 15 -n 2
    $ Warning: specified number of blobs does not result in equal number of residues per blob.
    $ ['ACDEHLKFGIMNPQRSTVWY', 'ACDEFGHIKLQPNRMSTVWY']

Using the inverse flag

.. code-block:: bash

    $ pipit-shuffle ACDEFGHIKLMNPQRSTVWY 5 15 -i
    $ ['ADECFGHIKLMNPQRSTVWY', 'ACDEFGHIKLMNPQRYVWTS']

When using the inverse flag, each side of the sequence is treated as a sequence block. So in this example, the first sequence shown after the command is used has the first 4 residues shuffled whereas the second sequence has the last 5 residues shuffled. Importantly, the coordinates for teh residues to keep constant include the number specified, so in this example residues 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, and 15 are not shuffled.
