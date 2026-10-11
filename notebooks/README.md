# Session 1 notebooks

1. [Replicate basics](01_replicate_basics.ipynb): the short API introduction.
2. [Replicate scene prompts](01b_replicate_scene_prompts.ipynb): a second version of the basics notebook using a scene dictionary from Session 1's visual prompt craft exercise.
3. [Artistic Telephone](02_artistic_telephone.ipynb): iterate, compare, select and pass within your group.

## Open in Jupyter

Download the repository ZIP from GitHub (Code → Download ZIP), extract it, and open its `notebooks` folder in the course's existing Jupyter environment. Keep all `telephone_*.py` helpers beside the notebooks. GitHub's preview does not execute notebooks.

Use Python 3.10 or newer. Install the shared requirements in the active kernel:

```python
%pip install -r requirements.txt
```

Restart the kernel if needed. Telephone uses ipywidgets 8 for prompt fields, the model dropdown, file upload and attempt selection. Check that the controls appear when you open the notebook. A file-path fallback is supplied for uploads; the other controls require working widgets.

All student notebooks default to offline practice. The labelled diagram tests saving and transfer, makes no API calls, and does not respond to prompts.

## Replicate and live attempts

Use your individual account and the hidden token input. Never paste tokens into code or submissions. Type GENERATE to request a potentially paid attempt. Saving, comparison and export do not create predictions. Restart the kernel when finished.

The initial model is `black-forest-labs/flux-schnell`. Use the model list supplied for the activity. These examples request one square PNG.

Telephone uses the same prediction lifecycle as the basics notebook: look up a model version, create a prediction, wait for completion, then download its output. It records the resolved version and prediction ID. The basics notebook remains the short introduction and does not record those extra fields in its saved prompt file.

## Structured scene-prompt version

Use `01b_replicate_scene_prompts.ipynb` as an alternative to the plain basics walkthrough. Edit a `scene` dictionary, assemble and inspect a text prompt, then use the same generation/download steps. The dictionary is a writing aid, not another API schema. A snapshot of its fields is saved alongside the exact prompt and model settings in `outputs/scene_basics/<attempt>/prompt.json`.

For a revision, edit one field in section 3a and rerun 3a, 3b and sections 4 to 6. Each generation gets a separate output folder. Offline practice still draws the same labelled diagram; it does not visualise the scene prompt.

## Your Telephone workflow

- Set session name, group and seat once. Everyone uses the same class session name.
- Start a round and load the assigned incoming PNG in rounds 2 to 5.
- Edit the prompt, generate, then save and preview privately.
- Revise and repeat within the time and spending budget agreed in class.
- Refresh the comparison cell and choose any saved attempt for that round.
- Run **Save selected image for passing**. Download that PNG and upload it to the group's SWITCHdrive folder.

Every completed attempt has a separate local image and JSON record containing its exact prompt/settings snapshot. An earlier attempt can be selected after later attempts. Export does not use the current prompt-box text. Once a round has been exported, a different selection cannot overwrite it silently.

Incoming images are inspected locally, not sent as image-to-image inputs. The notebook validates the assigned filename; you still need to choose the correct group folder. Passing stays within six groups of five, retaining names such as `01.png`, `01_02.png`, and `01_02_03.png`.

Files are relative to Jupyter's working directory:

```text
outputs/
    basics/<attempt>/image.png and prompt.json
    scene_basics/<attempt>/image.png and prompt.json
    telephone/<session>/Group_A_S01/
        private/<attempt>/image.png and record.json
        handoff/Group_A/01.png
        practice_handoff/Group_A/01.png
        pending.json (only while a live prediction is pending)
```

Keep the private attempt folders for later comparison. Only the selected handoff PNG is uploaded during play. No direct SWITCHdrive integration or private messaging system is required.

## Hidden prompts and the final reveal

Export removes ordinary image metadata, then embeds a small JSON record in the lowest bits of RGB pixels. Only the selected attempt's own record is included. No cumulative history, secret key or ST3GG installation is needed. This discourages casual prompt reading; it is not encryption or tamper-proof storage.

Pass the original PNG without resizing, screenshots, image editing or JPEG conversion. Those operations can destroy the hidden record. Keep every round's PNG in the shared group folder.

At the end of the game, we will view each chain in order and reveal its prompts. Your group's selected PNGs contain the records needed for this, so you do not need to upload your private logs.

## Recovery

If waiting or downloading fails, retry Telephone's save cell. The existing prediction is reused. Do not create another paid attempt just to retry a download.

A live prediction ID and its snapshot are written to `pending.json`. After a kernel restart, use the same session/group/seat, reconnect, and run the documented recovery cell. It fetches the existing prediction. Confirmed failed/canceled predictions can be cleared with the supplied control. If a request failed before returning an ID, inspect Replicate before retrying.

After a normal restart, use the same identity and round, then refresh comparison to select a previously saved attempt without regenerating. Never delete or replace a passed image without coordinating with the instructor and next student.

## References

- [Replicate Python guide](https://replicate.com/docs/get-started/python/)
- [Official Python client](https://github.com/replicate/replicate-python)
- [FLUX.1 schnell inputs](https://replicate.com/black-forest-labs/flux-schnell/api)
- [File outputs](https://replicate.com/docs/topics/predictions/output-files)
