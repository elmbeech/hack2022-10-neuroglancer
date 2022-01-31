# hack2022-10-neuroglancer
Challenge 10: 3D Volume Visualization through Neuroglancer

Recently, wide field microscopes are increasingly used to collect optical sections of human tissue, allowing to reconstruct multiplex volumetric image data. 3D images have been generated by high-resolution optical sectioning of selected fields of view. The volumetric data can enable novel biological analysis regarding tissue anatomy and morphology. However, there are only a few tools (mostly proprietary) that can handle the size and multiplex structure of these datasets. Challenge participants will extend an open-source volume visualization tool developed by Google (Neuroglancer: https://github.com/google/neuroglancer) to handle multiplex volumetric image data in OME tiff format, typically used in digital histopathology.



JT: list more packages and come up with a concrete task description. Link to the datasets: [Synapse.org](https://www.synapse.org/#!Synapse:syn26848775).

* [Neuroglancer](https://github.com/google/neuroglancer)
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
```
pip install tiffile
```
Loading an image and printing the shape:
```
import tiffile
# tifffile.imread() returns a numpy array 
image = tifffile.imread("<awesome_name>.tiff")
print(image.shape)

(z, c, y, x)
```
