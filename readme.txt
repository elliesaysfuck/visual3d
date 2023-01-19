Hi!
This is Ellie. I've been working with Visual3D for the past weeks and here are the pipelines that 
I was able to write so that any calibration recording can be used to create a working model of the 
lower body and then apply it to any recording.

The problem that I found when creating the model and using it was that when exporting the recording 
(in my case from Optitrack), the markers would have the prefix of the asset built in the recording
program. This would make impossible for the movement recording to be moved by any model that was not
recorded with the same asset.

So, I wrote some pipeline commands so that the process is automatized and I'll proceed to explain the 
files with what they do and what steps should you follow.

create_any_model_and_use_it_with_any_recording.v3s: This is the file that has it all. If you just want
to sart working with your recordings, this is the file that you should use. 

	What it does: 
		-It first opens the standing file, the one used for calibrating the model, and
		erases the prefix I've talked about earlier that came from the asset. For example, if your 
		markers are named "asset1:rasis", it will change them to "rasis". 
		-Then closes the file and reopnes it as 
		the calibration file. 
		-It will then include the mass and height with a pop-up window, setting these 
		and other values for the model. Then it will create the bones (segments) and joints 
		(landmarks) of the model. 
		-The model is then saved to the folder of your choice and then it uses it to assign it to 
		the recording that you want to analize, which has already been cleaned from the prefix from 
		the asset.

	Steps to follow:
		-Execute the pipeline
		-Choose standing file to remove its prefixes (this will change the file and save it like that,
		so it is recommended to make a copy)
		-Choose modified standing file for calibration
		-Enter subject mass and height
		-The model has been created
		-Save the created model in the folder of your choice and name it
		-Select the saved model
		-Select the recording you want to analize (this will modify the file so making a copy is 
		advised) and in the pop-up window check the mark left to the of that recording then press ok
		-Discard the new pop-up window (it should show no errors nor warnings) and the pipeline workshop
		in the "Signals and Events" in the top right text box select the recording you want to see
		-A skeleton should show up and if you press the play button it should start to move

clean_prefix_from_recording.v3s: This file will help you erase the prefix that the asset creates by default. 
This is done to both the walking file and the calibration one so that both can be freely used.
	
	Steps to follow:
		-Execute the pipeline
		-Select the file you want to modify
		-Manually save the file

create_model_without_prefix.v3s: This file will create a working model with a standing recording without the 
prefixes. This modelo can be then used with any recording without prefixes.

	Steps to follow:
		-Execute the pipeline
		-Select the clean standing file
		-Manually save the file

use_clean_model_with_clean_recording.v3s: This file will use a clean model to provide with movement a clean
recording.

	Steps to follow:
		-Execute the pipeline
		-Select model
		-Select recording to analyze
		-Assign the model to the recording
		-In the "Signals and Events" in the top right text box select the recording you want to see

create_model_from_any_recording.v3s: This file erases the prefixes from the standing trial and creates the model
from that.

	Steps to follow:
		-Execute the pipeline
		-Select standing trial to erase the prefixes
		-Select standing trial to buil the model
		-Save the model

use_clean_model_with_any_recording.v3s: This file assigns a model without the prefixes to any recording to make it 
move.

	Steps to follow:
		-Execute the pipeline
		-Select model
		-Select recording to erase its prefixes
		-Assign model to the recording
		-In the "Signals and Events" in the top right text box select the recording you want to see