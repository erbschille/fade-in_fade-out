# fade-in_fade-out
Fade In/Fade Out task 

This is a mental imagery outcome measure--intended to be given both pre- and post-experiment. It largely replicates the task as described in Luhrmann, Nusbaum & Thisted, 2013 (described on page 165). This is a newly created version, coded in javascript with the assistance of Claude (model Sonnet 4.6 in June 2026).

**Collaborators or those interested in using this task should fork this repo. Please do not use our same link (it will mess with data collection)**

These are the instructions for the Fade In task: 

"Welcome to the Fade In task. During this task, you will be shown a series of blurry images/words. These images/words will become increasingly clear so that eventually you will be able to identify what you are seeing. You will have to indicate at what point you are able to identify the image/word that is being shown. On the following screens, you will view a series of 20 images/words shown one at a time. Once you know what the image/word is, press the spacebar. You will then see a space to enter text. Please type in the image/word that you have just seen. Finally, hit the enter key or click continue to proceed to the next picture."

These are the instructions for the Fade Out task: 

"Welcome to the Fade Out task. This task is similar to the Fade In task you just completed. However, during this task, you will be shown a series of images/words that will become increasingly blurry so that eventually you will no longer be able to identify what you are seeing. You will have to indicate at what point you are no longer able to see the image/word that is being shown. On the following screens, you will view a series of 20 images/words shown one at a time. Once you no longer see the image/word, press the spacebar. You will then see a transitional screen. This is just to give you a chance to rest before viewing the next image. Once you are ready to view the next image hit the spacebar or click continue to proceed."

The Fade In and Fade Out tasks use a set of 20 stimuli--10 images and 10 words. Half the words and images (5 each) are spiritual in nature, the other half are ordinary. 
Words: green, school, window, shoe, dog, spirit, universe, ancestor, goddess, energy 
Images: bike, tree, house, chair, cherries, infinity, dove, yinyang, cross, moon

#-----------------------------------

Here is a description of the CSV file automatically downloaded for each participant:

Every row is one trial. There are 40 rows per participant (20 fade-in + 20 fade-out). 
The columns are:
- participant_id, session_start — the ID entered at the start and the ISO timestamp when the experiment began. These are repeated on every row so the file is self-contained.
- stimulus_id, stimulus_type, stimulus_label — unique ID (e.g. w03, i01), whether it was a word or image, and the plain-text label (e.g. Christ, cherries).
- task_type, direction — fade_in/fade_out and in/out (redundant but convenient for filtering).
- trial_num — 1–20, the trial's position within its task block for that participant.
- frame_at_response — which of the 41 frames (0–40) the spacebar was pressed on. Frame 0 is the starting frame (maximum blur in fade-in, fully clear in fade-out).
- clarity_pct_at_response — the primary dependent variable, 0–100. 100 = fully clear, 0 = fully blurred. Lower means the participant responded at higher blur:
- blur_px_at_response — the exact CSS blur radius in pixels when spacebar was pressed. Useful if you want to re-run analyses at different blur scales.
- frames_shown, total_frames, saw_all_frames — how many frames were displayed, always 41 total, and a boolean flag for trials where the participant never pressed spacebar (the sequence ran to completion).
- response_text — what the participant typed in the fade-in text-entry screen. Empty string for fade-out trials.
- rt_ms — reaction time in milliseconds from the first frame appearing to spacebar press.

Consolidating across participants
Each file is named fade_task_{participant_id}_{timestamp}.csv, so they won't overwrite each other. 
