# Deep-Learning-CNN-Fish-Monitoring
Fish migration monitoring from audio detection with CNNs

### Objective

Research project for IMT Mines Ales with Elie Lambeaux and Thomas Guerin from the promo Data Science and AI. The objective was to monitor fish migration thanks to the specific sound, called "bull", made during the spawning by using deep learning algorithms. The main challenge was dealing with highly unbalanced data

The paper about this project was published at AudioMostly21 and is availble here. [Paper CNNs AM21] (https://www.google.com/url?sa=t&source=web&cd=&ved=2ahUKEwiCpZ-KooOCAxUdhIkEHeZGCsUQFnoECBIQAQ&url=https%3A%2F%2Fimt-mines-ales.hal.science%2Fhal-03330991%2Fdocument&usg=AOvVaw3DDunrR_71MJVEUdG2kTlX&opi=89978449)


### Data

Several recordings were recorded and annotated by the MRM association. The annotations contain information about when a bull call occurs, including the start and end times. The data is confidential and has not been published.

As you can see in the graph, the duration of a bull call is quite short, lasting less than 10 seconds.
![Boxplot bull](Boxplot_par_site_et_annee.png)



### Processing and mel-spectrogram
The strategy was to divide each of the 20 recordings, totaling 68 hours of audio, into small segments. Since the length of a bull call was usually less than 15 seconds, the segment length was set to 15 seconds, resulting in a total of 47,000 segments.

The second step in the preprocessing involved transforming each audio segment into a mel-spectrogram. This mel-spectrogram contained all the frequencies and intensities present in the 15-second audio segment.

As you can see, the data was highly unbalanced, with many segments having no bull calls and very few containing bull calls. 
![unbalanced data](grpahs/Barplot_prop_bull_no_bull.png)


### Modeling
Once our long audio data had been transformed into 47,000 mel-spectrograms associated with labels indicating the presence or absence of bull calls, modeling could begin. Two CNN models, AlexNet and VGG16, were selected. You can check the notebooks and codes to see their architectures. Each model was customized to better suit the data, particularly addressing the unbalanced proportion between "no bull" and "bulls" segments.

![models](graphs/model.png)

### Results
The average recall was around 90%, which is quite impressive. The primary objective was to identify bull calls, with an emphasis on not missing any bull calls, as all detected bull calls would later be reviewed by fish spawning experts.