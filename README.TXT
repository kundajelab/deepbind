DEEPBIND v0.1
-------------

The deepbind command-line executable can be used to score DNA/RNA sequences
according to any RBP/TF model listed in the DeepBind web repository:

   http://tools.genes.toronto.edu/deepbind

For each input sequence, the deepbind executable scores each subsequence
of a pre-determined length (e.g. 20) and returns only the maximum score over
all positions.


EXAMPLE
-------

To generate predictions with DeepBind, you need two things:

  1) a list of model IDs, and
  2) a list of DNA/RNA sequences.

The file example.ids contains 4 example model IDs, one
on each line, reproduced here:

   D00210.001 # RBFOX1 (RNAcompete)
   D00120.001 # MBNL1 (RNAcompete)
   D00410.003 # GATA3 (SELEX)
   D00328.003 # CTCF (SELEX)

The file example.seq contains 4 example sequences, which
were chosen such that the nth sequence scores highly for
the nth model. The file example.seq is reproduced here:

   AGGUAAUAAUUUGCAUGAAAUAACUUGGAGAGGAUAGC
   AGACAGAGCUUCCAUCAGCGCUAGCAGCAGAGACCAUU
   GAGGTTACGCGGCAAGATAA
   TACCACTAGGGGGCGCCACC

To generate 16 predictions (4 models, 4 sequences), run
the deepbind executable as follows:

   % deepbind example.ids < example.seq
   D00210.001   D00120.001   D00410.003   D00328.003
    7.345649    -0.152710    -0.763340    -0.026180
   -0.159393     3.663924    -0.196943    -0.026180
   -0.143584     0.357632     5.885349    -0.026180
   -0.161033    -0.081444    -0.379695    17.682623

To see details of each ID, use the --dump-info flag:

   % deepbind --dump-info example.ids
   ID          Protein  Type  Species       Family   Class  Experiment  ...
   D00210.001  RBFOX1   RBP   Homo sapiens  RRM             RNAcompete  ...
   D00120.001  MBNL1    RBP   Homo sapiens  Znf             RNAcompete  ...
   D00410.003  GATA3    TF    Homo sapiens  GATA            SELEX       ...
   D00328.003  CTCF     TF    Homo sapiens  znfC2H2         SELEX       ...
