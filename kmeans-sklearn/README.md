# KMeans via sklearn (Python2)

Two clustering examples using [sklearn](https://scikit-learn.org/stable/).

It is assumed you already have a Binaris account. If you don't have an account yet, worry not, signing up is painless and takes just 2 minutes. Visit [Getting Started](https://dev.binaris.com/tutorials/python/getting-started/) to find concise instructions for the process.

## Deploying with pip packages

To deploy a Binaris function that depends on `pip` packages we need to rely on the [Bob tool](https://github.com/binaris/bob). Bob is simple script, which greatly reduces the hassle of building platform-specific python packages. This is accomplished by building the dependencies against the same architecture used by Binaris functions, this way you can guarantee your dependencies will work at runtime.

Outlined below are the steps needed to build with Bob and then subsequently deploy your own kmeans functions.

1. Install Bob somewhere accessible 

    ```bash
    git clone https://github.com/binaris/bob.git
    ```

2. Navigate to the "kmeans-sklearn" directory (the same directory this README is in) and run

    ```bash
    /path/to/bob/build.sh 2
    ```

    > Note: The first run of Bob builds a Docker image and may take a while

3. Deploy your functions

    ```bash
    bn deploy public_kmeans_image_quant_py2
    # or
    bn deploy public_kmeans_simple_py2
    ```

As a final note, keep in mind that you only need to run Bob again if you add or remove pip packages. Changes to the function code itself only require another `bn deploy`.

## Try it out

Visit the URL printed by deploy (for `public_kmeans_image_quant_py2`) in your browser and add the image URL you want to run kmeans on. The optional query param `num_colors` can also be used to modify the number of clusters kmeans used to quantify your image.

_Example URL_

https://run.binaris.com/v2/run/0123456789/public_kmeans_image_quant_py2?image_url=https://i.imgur.com/HLmmVIg.jpg&num_colors=16