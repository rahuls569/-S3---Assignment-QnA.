Part 2: Refer to this code: COLABLINK
WRITE IT AGAIN SUCH THAT IT ACHIEVES
99.4% validation accuracy
Less than 20k Parameters
You can use anything from above you want. 
Less than 20 Epochs
Have used BN, Dropout, a Fully connected layer, have used GAP. 

Response: 
In this assignment, a Neural network is defined which uses Batch normalization, dropout a fully connected layer, and Global average pooling. The network is shown as 

class Net(nn.Module):
    def __init__(self):
        super(Net, self).__init__()
        self.conv1 = nn.Conv2d(1, 8, 3, padding=1) # 1 input channel, 8 output channels, 3x3 kernel size, 1 padding
        self.bn1 = nn.BatchNorm2d(8) # batch normalization for 8 channels
        self.conv2 = nn.Conv2d(8, 16, 3, padding=1) # 8 input channels, 16 output channels, 3x3 kernel size, 1 padding
        self.bn2 = nn.BatchNorm2d(16) # batch normalization for 16 channels
        self.pool1 = nn.MaxPool2d(2, 2) # 2x2 max pooling
        self.conv3 = nn.Conv2d(16, 16, 3, padding=1) # 16 input channels, 16 output channels, 3x3 kernel size, 1 padding
        self.bn3 = nn.BatchNorm2d(16) # batch normalization for 16 channels
        self.conv4 = nn.Conv2d(16, 32, 3, padding=1) # 16 input channels, 32 output channels, 3x3 kernel size, 1 padding
        self.bn4 = nn.BatchNorm2d(32) # batch normalization for 32 channels
        self.pool2 = nn.MaxPool2d(2, 2) # 2x2 max pooling
        self.conv5 = nn.Conv2d(32, 64, 1, padding=1) # 32 input channels, 64 output channels, 1x1 kernel size, 1 padding
        self.bn5 = nn.BatchNorm2d(64) # batch normalization for 64 channels
        self.conv6 = nn.Conv2d(64, 64, 1, padding=1) # 64 input channels, 64 output channels, 1x1 kernel size, 1 padding
        self.bn6 = nn.BatchNorm2d(64) # batch normalization for 64 channels
        self.conv7 = nn.Conv2d(64, 10, 1, padding=1) # 64 input channels, 10 output channels, 1x1 kernel size, 1 padding
        self.gap = nn.AdaptiveAvgPool2d((1,1)) # Global Average Pooling
        self.dropout1 = nn.Dropout(p=0.25) # dropout probability of 0.25
        self.dropout2 = nn.Dropout(p=0.25) # dropout probability of 0.25
        self.dropout3 = nn.Dropout(p=0.25) # dropout probability of 0.25
        self.fc = nn.Linear(10, 10) # fully connected layer, 10 input, 10 output

    def forward(self, x):
        x = self.pool1(F.relu(self.bn2(self.conv2(F.relu(self.bn1(self.conv1(x)))))))
        x = self.dropout1(x)
        x = self.pool2(F.relu(self.bn4(self.conv4(F.relu(self.bn3(self.conv3(x)))))))
        x = self.dropout2(x)
        x = F.relu(self.bn6(self.conv6(F.relu(self.bn5(self.conv5(x))))))
        x = self.dropout3(x)
        x = F.relu(self.conv7(x))
        x = self.gap(x)
        x = x.view(-1, 10)
        x = self.fc(x)
        return F.log_softmax(x)
        
  In the above network, dropout is used after the second layer, fourth layer, and sixth layer. Batch normalization is used after each convolution layer except the last convolution layer. After the seventh layer, Global average pooling is used. after that, the fully connected layer is used.
  
  In this network, less than 20k parameters are used
  
![image](https://user-images.githubusercontent.com/79099957/212399165-5f26d615-ebee-4446-b644-4489767c53fd.png)

 For validation accuracy, 19 epoch is used. The accuracy is given as
 loss=0.33131274580955505 batch_id=468: 100%|██████████| 469/469 [01:52<00:00,  4.16it/s]

Test set: Average loss: 0.2858, Accuracy: 9260/10000 (92.6%)

loss=0.10861426591873169 batch_id=468: 100%|██████████| 469/469 [01:46<00:00,  4.41it/s]

Test set: Average loss: 0.1584, Accuracy: 9551/10000 (95.5%)

loss=0.2127656489610672 batch_id=468: 100%|██████████| 469/469 [01:43<00:00,  4.51it/s]

Test set: Average loss: 0.0939, Accuracy: 9717/10000 (97.2%)

loss=0.0997663363814354 batch_id=468: 100%|██████████| 469/469 [01:52<00:00,  4.17it/s]

Test set: Average loss: 0.1406, Accuracy: 9523/10000 (95.2%)

loss=0.12740914523601532 batch_id=468: 100%|██████████| 469/469 [01:45<00:00,  4.45it/s]

Test set: Average loss: 0.0821, Accuracy: 9737/10000 (97.4%)

loss=0.06519751250743866 batch_id=468: 100%|██████████| 469/469 [01:44<00:00,  4.49it/s]

Test set: Average loss: 0.0991, Accuracy: 9684/10000 (96.8%)

loss=0.12295011430978775 batch_id=468: 100%|██████████| 469/469 [01:45<00:00,  4.45it/s]

Test set: Average loss: 0.0536, Accuracy: 9834/10000 (98.3%)

loss=0.10014616698026657 batch_id=468: 100%|██████████| 469/469 [01:43<00:00,  4.52it/s]

Test set: Average loss: 0.0511, Accuracy: 9844/10000 (98.4%)

loss=0.08804547041654587 batch_id=468: 100%|██████████| 469/469 [01:45<00:00,  4.46it/s]

Test set: Average loss: 0.0490, Accuracy: 9850/10000 (98.5%)

loss=0.0172394048422575 batch_id=468: 100%|██████████| 469/469 [01:46<00:00,  4.40it/s]

Test set: Average loss: 0.0559, Accuracy: 9826/10000 (98.3%)

loss=0.0842280164361 batch_id=468: 100%|██████████| 469/469 [01:44<00:00,  4.50it/s]

Test set: Average loss: 0.0456, Accuracy: 9838/10000 (98.4%)

loss=0.06229675933718681 batch_id=468: 100%|██████████| 469/469 [01:46<00:00,  4.40it/s]

Test set: Average loss: 0.0583, Accuracy: 9796/10000 (98.0%)

loss=0.06283388286828995 batch_id=468: 100%|██████████| 469/469 [01:45<00:00,  4.44it/s]

Test set: Average loss: 0.0508, Accuracy: 9837/10000 (98.4%)

loss=0.00676104286685586 batch_id=468: 100%|██████████| 469/469 [01:45<00:00,  4.47it/s]

Test set: Average loss: 0.0384, Accuracy: 9875/10000 (98.8%)
  
for achieving this accuracy, we have changed the learning rate 
optimizer = optim.SGD(model.parameters(), lr=0.1, momentum=0.9)
  

