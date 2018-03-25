# Style-Transfer
Since deep learning came on stage and new
architectures started to emerge, it showed incredible results in various
fields. One of them is art. This project shows how deep learning can be applied
to redraw the picture in the style of famous painters. Basically, any style can
be chosen, it does not have to be a painter. For this project, as a test
picture I have chosen Van Gogh’s starry night. 


First of all, we need to understand how we
make the computer “see”. We use special type of neural nets called
convolutional neural nets. It was proven that at the current time, it is the
best technology for image processing. Basically, each layer of convolutional
network learns specific representation of an image. By that I mean, the very
first layer learns lines, the second one learns edges, the third learns shapes
and at the final layer the net builds the abstract representation of an image
and learns certain features from there. We can later use this kind of network
to classify stuff, without hand coding anything or choosing the right features,
because convnets will do that for us. One more thing that makes them so cool is
that they are spatially invariant, it does not matter in what position or angle
it sees a cat, it will know it is a cat.


Now, let's get back to the project. Essentially, everything it does is
performing complex optimization algorithm. If we want to redraw the picture in
the style of Van Gogh, we have to make so that the content of our target image
will be preserved but it will look like if Van Gogh has drawn it. To achieve
that we have to define so called loss function. Loss function calculates the
difference between the output that we got and the target output. For style
transfer, we will need 2 loss functions, one for content and one for style. The
content loss is pretty straight-forward, we are just going to calculated the Euclidean
distance between feature representations of our content image and our generated image. For style loss, it is a
little bit trickier. You see, it is not that easy to define, what “style” is.
The main breakthrough of this project, in my opinion, is that it succeeded to
do it. Let me try to explain it as simple as I can.  The creators of this algorithm defined style
as a gram matrix. Gram matrix of a certain matrix can be obtained by
multiplying a matrix by its transpose.
This matrix represents which features are correlated. For instance, in starry
night, the part of an image that is blue gets swirly, these two features,
colour blue and swirliness are correlated. We calculate style loss function by
calculating the difference between Gram matrices of our generated image and our
style reference image. Finally, we multiple each of them by appropriate weights
and sum them to get total loss function. The task now is to minimize this loss
function.


Now take a look at the code, analyze it
and play around with parameters to see how it affects the final result. Here what
I got after training it on the picture of my amazing friend.



![content_trial](https://user-images.githubusercontent.com/36106772/37877400-5b403d4a-3063-11e8-95f6-bbdc87a0be50.jpg)
![styletransferredimage](https://user-images.githubusercontent.com/36106772/37877401-64eba8fc-3063-11e8-9b50-348f2b8eb55c.jpg)
