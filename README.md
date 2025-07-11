# Yale_Analysis


Today i want to present an Image analysis project. The project is based on Extended Yale B Dataset https://www.kaggle.com/datasets/jensdhondt/extendedyaleb-cropped-full . The project aim was to investigate compression methods and to discover hidden patterns in data. Also to demonstrate some math properties of SVD

What i did was:
Loading images data and performing a Wavelets transformation on each image. Keeping only 1% of wavelets coefficient. As we can see in the images, we still preserved much of the quality even with an aggressive truncation. Wavelet transform is one of the most powerful compression methods. Also i reshaped the transformed wavelets matrix into a column vector and stacked them horizontally , to form a big (mxn)*n_images matrix. (where m*n is the pixel count per image and n_images is the total number of images).

Plotted the graph for the cumulative sum of principal components where we can identify which principal components to pick and where to truncate. I chose 2 for simplicity. 
We can see that the growth rate of explained variance of components slowly decay, indicating that we can explain the data with less components.

The interpretation for PCA on images is that we can represent a big dataset by projecting data onto a lower-dimensional subspace spanned by the most important principal components ('eigenfaces'), which capture the primary modes of variation within the dataset.

Then we show the average face and the column vector of the pca transformed face. They are very similar. This is because the average face is strongly linked to the first principal component, being that the first PCA component captures the most variance.

I performed a Kmeans cluster identification process by plotting the silhouette score for different K values and then choosing the k that maximize silhouette score. In this case it’s 3.

I plotted the PCA transformed data along with label colors to distinguish between clusters.
Then I wanted to investigate the image meaning of every cluster in the pca space. For PCA1 (first row) the first cluster represented eyes and contour, the second cluster was the left half of the pca face, and the third cluster was the right part of the face.

Then i showed the difference about an image and a mean subtracted image. Also i re loaded all images into a matrix (by reshaping each image into a column vector). This time i used SVD to isolate U sigma and V transpose because i wanted to show eigenfaces. 
Eigenfaces are basic images that when linearly combined form the face of a person or an image.

Lastly, I showed that it’s possible to reconstruct a dog image by computing avg_face and then summing up U @ U.t @ dog_image_matirx. This is possible because U is a unitary matrix such that U @ U.t = I the identity matrix. So if we approximate I with increasingly number of singular value it is possible to build a dog image reconstruction with the image face subspace. 
