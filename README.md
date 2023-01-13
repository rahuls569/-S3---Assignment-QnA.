# S4---Assignment-Part1

PART 1: Rewrite the whole excel sheet showing backpropagation. Explain each major step, and write it on Github. 
1. Use exactly the same values for all variables as used in the class
2. Take a screenshot, and show that screenshot in the readme file
3. The Excel file must be there for us to cross-check the image shown on readme (no image = no score)
4. Explain each major step
5. Show what happens to the error graph when you change the learning rate from [0.1, 0.2, 0.5, 0.8, 1.0, 2.0] 
6. Upload all this to GitHub and then write all the above as part 1 of your README.md file. 
7. Submit details to S4 - Assignment QnA. 

Response:

A Neural network is given in the following figure

![image](https://user-images.githubusercontent.com/79099957/212354784-d402ce6f-ef5e-408a-b660-fcb1a4b4cbc9.png)

In this figure, there are three layers: input layer, hidden layer and output layer. I1, I2 are inputs, a_o1 and a_o2 are outputs which are obtained from activation function of o1 and o2 respectively. Middle layer variables are a_h1 and a_h2. E1 and E2 are errors and E_total is the sum of E1 and E2. t1 and t2 are targets. 
So, first we calculate forward equations which are as follows:

![image](https://user-images.githubusercontent.com/79099957/212355310-0bd04f85-9d07-4cb1-bdee-192ae1b87a11.png)

Now gradient for weights are calculated: (Where d denotes partial differentiation)
First differentiation of E_total is calculated with respect to w5, w6, w8, w7 which are as follows:

![image](https://user-images.githubusercontent.com/79099957/212355599-0ecaefe1-336a-498c-883b-61e349820bb1.png)

For calculating the differentiation of E_total with respect to w1, w2, w3 and w4 are as follows:

![image](https://user-images.githubusercontent.com/79099957/212355798-abf60f31-0199-4746-81c4-85d38383753c.png)
![image](https://user-images.githubusercontent.com/79099957/212355856-5c3b0762-7748-45a6-b948-9cdd13267ada.png)
![image](https://user-images.githubusercontent.com/79099957/212355934-38ae82c1-3705-48c4-8b0b-64a05cf0dcd2.png)
![image](https://user-images.githubusercontent.com/79099957/212356040-4cda709a-73f6-451a-8456-c1dc7ed6f2d2.png)

Now we have made one excel file in which t1=0.01, t2=0.99, i1=0.05 and i2=0.1 is taken and weights are taken according to figure. 
For updating the weights, following equation is taken 
W_new= w_old – learning_rate*dE_total/dw_old
All calculations are given in the excel sheet. 
Learning Rate at 0.1

![image](https://user-images.githubusercontent.com/79099957/212356493-191a9d4b-8eef-4598-b0ec-53baa9aab53b.png)

Learning Rate at 0.2

![image](https://user-images.githubusercontent.com/79099957/212356611-c7a4f7f9-ab87-47fc-8567-d116fc8c5452.png)

Learning Rate at 0.5

![image](https://user-images.githubusercontent.com/79099957/212356705-7a985758-77c5-4658-8df1-4acdf5390c6c.png)

Learning Rate at 0.8

![image](https://user-images.githubusercontent.com/79099957/212356812-4d3de504-1343-46cb-b9aa-0d15fb383ddc.png)

Learning Rate at 1

![image](https://user-images.githubusercontent.com/79099957/212356971-1a469b19-274f-49d2-8aea-46e0d0147bfd.png)

Learning Rate at 2

![image](https://user-images.githubusercontent.com/79099957/212357059-462a7248-73e8-43a4-a85b-8b33a26830d4.png)

In above figures, it can be seen that as learning rate increases, the error reduces faster. 

