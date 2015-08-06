# deepbind
I have put my modified version of the deepbind code here.

Here are the changes that I have made from the original deepbind code:
* The original code did not score the last position in the sequence.  I have fixed this bug.
* The original code checks every model to see if the reverse complement should be scored.  If it should, it gets the reverse complement of the sequence and scores it.  As a result, it gets the reverse complement of the sequence separately for every model.  I have changed it to assume that the reverse complement should be scored and get the reverse complement of the sequence before iterating through the models.
* I have added an --all-scores option that prints the score at every position instead of the maximum score across the sequence.  At each position, it prints the maximum of the score for the sequence and its reverse complement.
* I have added a --class-prob option that gets the probability of each sequence being a TF-binding site for each model instead of printing the output of the fully-connected layer for each model.  It does this by running the output of the fully-connected layer through a sigmoid.
