numerAI_1 - 
	This model uses pytorch and uses numerai dataset_V4
	I first split the training data into train and test datasets
	I use all 1191 features and only the main target
	I then create a pytorch model with layers:
		NumeraiV4(
  			(linear_layer_stack): Sequential(
    			(0): Linear(in_features=1191, out_features=64, bias=True)
    			(1): ReLU()
    			(2): Linear(in_features=64, out_features=32, bias=True)
    			(3): ReLU()
    			(4): Linear(in_features=32, out_features=16, bias=True)
    			(5): ReLU()
    			(6): Linear(in_features=16, out_features=1, bias=True)
  			)
			)

	The model uses Mean Square Error loss function and Adam optimizer

	The model is then trained through 10 epochs, saving the weights which correspond
	to the model with the smallest loss

	The model is then used to evaluate the test group and the numerai score and correlation
	with the target are calculated

	
	Shortcomings and Future Work
	The model is overtrained to and predicts ~0.5 for all inputs. This is because the classes
	in the input class are highly disproportionate, skewed to 0.5.
	In the next interation, I will introduce class balancing function to alleviate this