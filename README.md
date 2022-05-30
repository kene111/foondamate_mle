# foondamate_mle

This is the solution code to the machine learning engineering [task](https://careers.foondamate.com/machine-learning-engineer-remote/foondamate-ml-engineer-coding-challenge-001).


### Methods Used:

Two different approaches were used to provided a solution to the task.
1) Rule based approach.
2) sentence similarity.

### Repo Structure:
1) Machine_Learning_Engineering_Task_1_FoondaMate.ipynb : This notebook contains a combination of rule based approach and sentence similarty.
2) Machine_Learning_Engineering_Task_2_FoondaMate.ipynb : This notebook contains the rule based approach using the part of speech tagging.

### Method Explanation:

Explaining how the method in Machine_Learning_Engineering_Task_2_FoondaMate.ipynb notebook works first would make the approach in task one easier to understand.

1) Machine_Learning_Engineering_Task_2_FoondaMate.ipynb: The idea behind this approach is set to conditions to filter the sentences based on the POS tagging of 
each word in the sentence. During research, and trying to find out possible patterns that could be extracted. I noticed that sentences that could be classified 
under "Student wants to know if can share" class contained [modals](https://www.thoughtco.com/modal-auxiliary-term-1691397). In little words, modals are verbs 
that express necessity, uncertainty, possibility, or "permission". Depending on how the modal is used, the sentence could be a statement or seeking for permission.

examples of modals are : can, shall, would, may,  etc.

example of when a modal is used to make a sentence a statement:
1) I would share your email.
2) I shall share your email.
3) I can share your email.

example of when a modal is used to make a sentence seek permission:
1) can i share your email?
2) shall i share your email?
3) May i share your email?

Using the NLTK library, when analysing the pos tags for each word, when "i" is used before a modal it is a NN (Noun), when used after a modal, it is a VB (Verb).

Note: I decided to classify sentences that make a statement under the "Students want to know if can share" class, reason being that a statement could be challenged,
since it not yet done.

An example of what i mean is, assuming Mary recieves an email such as:
 * student: i shall share your email with my friends today.

Mary, the college student adviser could respond with :
 * ==> kindly hold on sharing my email for now, as there is an overflow of emails from students.
* or
 * ==> sure, go ahead.

Either way, Mary can still alter the outcome of the statement, as to a situation where the incoming email states that her email has already been shared i.e past tense.

For sentences that could be classified under "Student has shared" The essential keywords pos tags were mostly past tense of verbs VBD,VBN etc.

The approach in the notebook was to remove the words "I", "email","share",and "your" from the sentences leaving only the key words that could be used to differentiate 
what class a sentence could belong to.

This method tends to be a more generic approach as the conditions are set using the POS tags rather than the words themselves.


2) Machine_Learning_Engineering_Task_1_FoondaMate.ipynb: Similar to the method above, the key words that could be used to tell what class the sentence in an email could
belong to were hard coded. All the algorithm does is to check if these key words can be found in the sentences. Because these words are hard coded not all sentences would be
caught by the alogrithm, hence some sentences relating to the indvidual classes were stored seperately and their word embeddings were obtained. When a text/sentence that
didn't fit into any of the classes is found,  we obtain the emedding of the text and then find the sentence similarity between sentence and the stored sentences from both class.
We then find the overall mean, and compare. We take the highest mean value between the sentence and the classes and return the respective output.


[External Resources](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html)






