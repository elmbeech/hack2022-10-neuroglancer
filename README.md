# hack2022-10-neuroglancer

Recently, wide field microscopes are increasingly used to collect optical sections of human tissue, allowing to reconstruct multiplex volumetric image data. 3D images have been generated by high-resolution optical sectioning of selected fields of view. The volumetric data can enable novel biological analysis regarding tissue anatomy and morphology. However, there are only a few tools (mostly proprietary) that can handle the size and multiplex structure of these datasets. Challenge participants will extend an open-source volume visualization tool developed by Google (Neuroglancer: https://github.com/google/neuroglancer) to handle multiplex volumetric image data in OME tiff format, typically used in digital histopathology.

# Task description
In this challenge your tasks are

**1. Download and read the data**
  * You can download the data [here](https://www.synapse.org/#!Synapse:syn26848775)
  * try to load the data using [this code snippet]()
**2. Visualizing single channels including segmentations**
  * how do you need to transform the OME-TIFF data format to load it into Neuroglancer
  * can you convert OME-TIFF files into the [neuroglancer precomputed format](https://github.com/google/neuroglancer/tree/master/src/neuroglancer/datasource/precomputed) with multiresolution volumes and/or meshes
  * is direct [volume rendering](https://en.wikipedia.org/wiki/Volume_rendering) an option? See this [issue](https://github.com/google/neuroglancer/issues/186).

**3. Visualizing multiple channels simultaneously including segmentations**
  *  can you load two volumes at the same time using different data layers? 
  *  how many volumes could you render simultaneously? 


# Installation
Here, we provide a list of open-source software tools you might find usefull. Feel free to also consider other software libraries. 
* [Neuroglancer python interface](https://github.com/google/neuroglancer/blob/master/python/README.md)
* [CloudVolume](https://github.com/seung-lab/cloud-volume)
* [Igneous](https://github.com/seung-lab/igneous)

# Datasets
We provide you with three datasets which all contain the same channels but feature different interesting biological findings. The datasets are available via [Synapse.org](https://www.synapse.org/#!Synapse:syn26848775).
Each dataset or cube has the dimensions 100 slices x 29 channels x 1080 x 1080. All but the last channel are different markers. The last channel is a instance segmentation mask computed from the DNA1 channel.

Channel Descriptions:
1. DNA1
2. PD1
3. TLR3
4. SOX10
5. DNA2
6. CD163
7. CD3D
8. PDL1
9. DNA3
10. CD4
11. ICOS
12. HLADPB1
13. DNA4
14. CD8A
15. CD68
16. GZMB
17. DNA5
18. CD40L
19. LAG3
20. HLAA
21. DNA6
22. SQSTM
23. VIN
24. TIM3
25. DNA7
26. LAMP1/CD107A
27. PDL1_2
28. PD1_2
29. Nuclei Segementation Masks

# How to load the data
you can load the data using the tiffile library in python.
install it via:
```python
pip install tiffile
```
Loading an image and printing the shape:
```python
import tiffile
# tifffile.imread() returns a numpy array 
image = tifffile.imread("<awesome_name>.tiff")
print(image.shape)

(z, c, y, x)
```
