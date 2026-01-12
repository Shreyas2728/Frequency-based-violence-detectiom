# Frequency-based-violence-detection
Frequency analysis for violence detection breaks down audio signals into features within the frequency domain, including Mel Frequency Cepstral Coefficients, spectral contrast, and Mel-spectrograms, for patterns related to violent sounds, including screams and hits. The features derived are dependent on tonal and pitch information, setting it apart from general audio, usually processed for analysis in a small window, for instance, 10 seconds, for real-time analysis. After detection, it sends an alert email with information such as timing and a snapshot.
​

Core Techniques
================
The frequency domain features, such as MFCCs, are given high importance in terms of performance for the classification task with accuracies going up to 97% when combined with the text analysis technique. The audio is segmented or windowed and tuned for the identification of the violence indicators. The deep learning models, such as CNN-LSTM, improve the analysis of the surveillance video.

​
Alert Integration Detection modules are used to classify audio as “violent” and automatically send silent mails to emergency contacts using SMTP protocols. These notifications contain information regarding incidents to enable swift action and are sometimes coupled with SMS. Such systems are used in smart homes or public surveillance systems and are designed to have
