The Misalignment Museum in San Francisco has an exhibit that consists of a clown doll speaking back to visitors in a clone of their voice, demonstrating the ease of voice cloning. This exhibit sometimes fails due to noisy background environments. Additionally, the exhibit relies on an external API, potentially storing recordings of children's voices externally. By experimenting with various methods for noise reduction, we propose a new pipeline that will do voice cloning locally on a Macbook with better performance in noisy environments and at lower cost to the museum. We accomplish this by processing the incoming sound files using DeepFilterNet, then converting a pre-trained model to sound like the target voice using OpenVoice.

We used the Microsoft Scalable Noisy Dataset for our work. This dataset comes with code to combine the noiseless speech files with the noise files. Using this code, we generated 1 hour of speech for five different speakers. These subsets can be found in separate folders under [speaker_data](https://github.com/annalittle/CS224sProject/tree/main/speaker_data). 

We then used the second speaker, a Male voice, to test out our pipeline. The [audio input](https://github.com/annalittle/CS224sProject/blob/main/MaleSpeakerWithAirportAnnouncementsOverlayedInput.wav) we begin with consists of this speech overlayed with [airport announcements noise](https://github.com/annalittle/CS224sProject/blob/main/AirportAnnouncementsNoise-NoiseOnly.wav). With this noisy input, we used OpenVoice to generate a [simple output, which sounded very staticky and unclear](https://github.com/annalittle/CS224sProject/blob/main/BaselineGeneratedOutput.wav). We also generated a [longer output, a sentence with a lot of emotion](https://github.com/annalittle/CS224sProject/blob/main/BaselineGeneratedOutputFanficVersion.wav) so that we could test the emotion conveyed in the voice clone.

To improve on this baseline, we first began by using spectral gating to remove background noise from the sample. This resulted in a ["cleaned" input](https://github.com/annalittle/CS224sProject/blob/main/PostSpectralGatingInput.wav) that sounded almost identical to the baseline. The [generated voice clone]() also sounded almost identical to the baseline.

We then used DeepFilterNet to remove background noise. This resulted in an [input audio file that sounded like no noise had ever been added](https://github.com/annalittle/CS224sProject/blob/main/PostDeepFilterNetInput.wav). The [generated voice clone](https://github.com/annalittle/CS224sProject/blob/main/PostDeepFilterNetGeneratedOutput.wav) was a remarkable improvement over the baseline. 



