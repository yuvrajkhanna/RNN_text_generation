# RNN_text_generation

**I am trying to generate new text by feeding text data to a single layered LSTM model using KERAS**<br/>



**EXPLANATION**<br/>
import needed libraries<br/>
![](images/1.png)

open your data in lower form means no captial characters(C->c,M->m etc...)
![](images/2.png)

store all the used characters in chars in sorted form<br/>
![](images/3.png)

create dictionary of chars to their ids and vice-versa
![](images/4.png)

In your dataset your input [1] is first 100 words then 101th is your output<br/>
then [2] is 2-101 words and its output 102nd word and goes on....
![](images/5.png)

we reshape it it like that so we can feed them to our model<br/>
![](images/6.png)

our Y_train is numeric form. convert it to vector form by using to_categorical.
eg. 3 --> (0,0,0,1,0,0,0,0,0,0) 
![](images/7.png)

now for our model we 1st use **LSTM** layer whose 1st parameter is its output size.<br/>
there is input then there is hidden unit then there is output.it is size of that output vector<br/>
**do no confuse it with no of hidden units its not that its size of output**<br/>
it is one that connects to dense layer,so in our case dense layer would be 256->10 neural net<br/>
also dropout is to reduce chance of overfitting<br/>
![](images/8.png)

once our model is ready we compile it by choosing a optimizer,loss function if necessary choose a learning rate reduction method as well<br/>
![](images/9.png)

Train the model<br/>
![](images/10.png)

now get a random integer with max as size of your dataset<br/>
choose that as your 1st line of your generated data.<br/>
![](images/11.png)

reshape it so you can feed it into your model<br/>
![](images/12.png)

now predict a character from those 100 chars you took randomly<br/>
store it in that random variable now you have 101 chars use last 100 chars repeat the process as much as you like<br/>
there you have it generated data<br/>
![](images/13.png)

since your output right now is in categorical(one hot vector) reshape it so we can convert it into numeric format<br/>
![](images/14.png)

convert it into numeric form by taking maximum of your output<br/>
![](images/15.png)

still they are numeric not characters so we convert them into characters.<br/>
![](images/16.png)

as they are stored in array format we need to first convert them into string format so we can read it.<br/>
![](images/17.png)

read your generated data<br/>
**you can change \n by next line**
![](images/18.png)


it may seems generated text as gibberish but as we can see it has learn many words and trying to form sentences as data set was quite small too so thats that if it was quite big one it can aswell form paragraphs plus model was very small aswell we can always try **stacked LSTM**.<br/>

if this helped please share :)
