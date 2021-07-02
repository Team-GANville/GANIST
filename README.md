# GANIST

Generating images similar to MNIST distribution by using Generative Adversarial Network

---

![logo](ganist.png)

---

## Methodology :

1. The GAN Architecture used here has two models
    * Generator : Generator is a 5 layered neural network trained to replicate the real  distribution from the input Noise. 
    * Discriminator : Discriminator is a 4 layer neural network that predicts the class of input data [image/text]. It is a classifier that discriminates real data from
      generated data.
2. Loss Function : The loss function used is BCElogit loss which is binary cross entropy combinedwith sigmoid activation.
3. Ex( log D(x) ) + Ez( log(1 – D(G(z))) ) -  This is the value function which discriminator tries to maximize and generator tries to minimize.

---

## Structure / Modules :

1. getdata() : Dataloader object to downlaod MNIST dataset .
2. noise_generator : Returns a vector of dimension ( num_of_images , z_dim ) for input of generator.
3. get_generator_block() : Returns a sequential layer which represents a single layer of generator model , dim = { input_dim , hidden_dim}.
4. Generator: Generator class which inherits nn.Module(), requires parameter (z_dim,img_dim,hidden_dim,no_of_images,device). Forward() function returns a generator nn.
              Output is of same dimension as the image in dataset.
5. get_discriminator_block : Returns a sequential layer which represents a single layer of discriminator model , dim = { img_dim , hidden_dim}.
6. Discriminator : Generator class which inherits nn.Module(), requires parameter (img_dim,hidden_dim,device). Forward() function returns a discriminator nn.
                   Output is binary ( 0/1 ) , which represents fake or real.
7. Loss_func() : Computes discriminator and generator loss using two functions :
                1. get_gen_loss : noise vector->Generate images gen() -> pass image to disc()-> bce(pred,arrays of 1) -> loss
                2. get_disc_loss : For discriminator loss of fake and real images is computed seperately using bce and then their average is taken.
8. Model : Create generator and discriminator object --> declare and initialize variables -> nested for loops for epoch and individual batches.

---

## Note :

1. While training generator , the discriminator has no effect on generator loss hence discriminator parameters are not considered . This is another way of saying the first        term in min-max function is ignored while generator training.
2. But for discriminator training , generator parameters are considered while training hence in-order to not affect generator parameters while discriminators training we
   detach the parameters. 
                  



              
              




