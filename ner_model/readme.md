To create our training and validation data,  I extracted candidate sentences from the PDF data. 
I used a reg ex pattern to match string values of 3-6 letters follewed by several numbers, such as USNM 2334521. 
Then I saved the sentence containing the potential specimens in a csv to be used in the next step.
Many of these candidates were not specimens, but a combination of postal codes, grant number, genome sequencing and equipment numbers.
<br>
The references and the body of the paper needed to be parsed separately because of the structure of the extracted json. 
<p>
<li>1_ExtractingCandidatesBody.ipynb</li>
<li>2_ExtractingCandidatesRef.ipynb</li></p>
<br>
After extracting candidates, I used an annotation application called Prodigy to note which candidates were or were not specimens.
I ran Prodigy from the command line, and annotated 2251 candidates. The resulting annotated data would be used to train and validate our model. 
To use the annotations to train the model, I had to convert the jsonl data into a format compatible with spaCy v3.4.
<p>
<li>3_Convert Training and Validation Data.ipynb</li></p>
<br>

As part of training this model, we utilized word vectors, which were created using sample text from the original research papers. 
The word vectors would weight the commonly used words, giving the model more context clues when searching for specimens. 
<li>4_Create Word Vectors.ipynb</li>
<br>
To train the model, first I created a blank spacy model "01".
In the command line, I incorporated the config file from the first model, the word vectors created in the previous step, and the training data to train a new model, "02". 
<p><li>5_Train Model.ipynb</li></p>

<br>
Lastly, I used the trained ner model on all 1300 publications to extract specimen citations.
<p><li>6_Running the Model.ipynb</li></p>
