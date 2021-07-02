# GANIST

Generating images similar to MNIST distribution by using Generative Adversarial Network

![logo](ganist.png)

## Methodology :

1. The GAN Architecture used here has two models
    * Generator : Generator is a 5 layered neural network trained to replicate the real  distribution from the input Noise. 
    * Discriminator : Discriminator is a 4 layer neural network that predicts the class of input data [image/text]. It is a classifier that discriminates real data from
      generated data.
2. Loss Function : The loss function used is BCElogit loss which is binary cross entropy combinedwith sigmoid activation.
3. Ex( log D(x) ) + Ez( log(1 – D(G(z))) ) -  This is the value function which discriminator tries to maximize and generator tries to minimize.

## Structure / Modules :

1. getdata() : Dataloader object to downlaod MNIST dataset .
2. noise_generator : Returns a vector of dimension ( num_of_images , z_dim ) for input of generator.
3. get_generator_block() : Returns a sequential layer which represents a single layer of generator model , dim = { input_dim , hidden_dim}.
4. Generator: Generator class which inherits nn.Module(), requires parameter (z_dim,img_dim,hidden_dim,no_of_images,device). Forward() function returns a generator nn.
5. get_discriminator_block : Returns a sequential layer which represents a single layer of discriminator model , dim = { input_dim , hidden_dim}.



              
              




