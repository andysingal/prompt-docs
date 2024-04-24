Overfitting, a common problem in machine learning, occurs when a model fits the training data too closely, learning its noise and outliers rather than the underlying pattern. As a result, the model performs well on the training data but poorly on unseen or test data. While it is ideal to prevent overfitting, it’s often not possible to completely eliminate it. Instead, we aim to reduce or minimize overfitting as much as possible.

The most successful techniques for reducing overfitting revolve around collecting more high-quality labeled data. However, if collecting more labeled data is not feasible, we can augment the existing data or leverage unlabeled data for pretraining.

### Common Methods

#### Collecting More Data
One of the best ways to reduce overfitting is to collect more (good-quality) data. We can plot learning curves to find out whether a given model would benefit from more data. To construct a learning curve, we train the model to different training set sizes (10 percent, 20 percent, and so on) and evaluate the trained model on the same fixed-size validation or test set
<img width="698" alt="Screenshot 2024-04-24 at 1 05 59 PM" src="https://github.com/andysingal/prompt-docs/assets/20493493/89c8f655-da4b-45f6-b4d6-a7c5996cec8a">


#### Data Augmentation
Data augmentation refers to generating new data records or features based on existing data. It allows for the expansion of a dataset without additional data collection.

Data augmentation allows us to create different versions of the original input data, which can improve the model’s generalization performance. Why? Augmented data can help the model improve its ability to generalize, since it makes it harder to memorize spurious information via training examples or features—or, in the case of image data, exact pixel values for specific pixel locations

#### Note: 
The most successful approaches against overfitting include regularization techniques like dropout and weight decay. As a rule of thumb, models with a larger number of parameters require more training data to generalize well. Hence, decreasing the model size and capacity can sometimes also help reduce overfitting. Lastly, building ensemble models is among the most effective ways to combat overfitting, but it comes with increased computational expense.

- Dropout reduces overfitting by randomly setting some of the activations of the hidden units to zero during training.
- In early stopping, we monitor the model’s performance on a validation set during training and stop the training process when the performance on the validation set begins to decline
- Classic bias-variance theory suggests that reducing model size can reduce overfitting. (Another common approach to obtaining smaller models is knowledge distillation. The general idea behind this approach is to transfer knowledge from a large, more complex model (the teacher) to a smaller model (the student).)
<img width="639" alt="Screenshot 2024-04-24 at 1 25 29 PM" src="https://github.com/andysingal/prompt-docs/assets/20493493/0db7660f-8a72-4d3e-ad30-82296aad10c6">

- Ensemble methods combine predictions from multiple models to improve the overall prediction performance. However, the downside of using multiple models is an increased computational cost.

<img width="680" alt="Screenshot 2024-04-24 at 1 31 45 PM" src="https://github.com/andysingal/prompt-docs/assets/20493493/d63c278e-62db-4b81-ab1d-1407c80d759e">
