# Automating the Lecture Hall: A Python Tool for Background Note-Taking

In the age of digital multitasking, keeping up with lectures, meetings, or long voice memos while trying to get other work done is a constant struggle. We’ve all been there: trying to type out what a speaker is saying while simultaneously checking emails or debugging code.

Enter **Voice Notetaker**, a lightweight Python project designed to solve exactly this problem. It listens to voice input—whether from a microphone or system audio—and continuously appends transcribed text to a file, all while running quietly in the background.

Here is a look at how this tool works and how it can streamline your productivity workflow.

---

## The Concept: "Set It and Forget It"

The core philosophy of Voice Notetaker is unobtrusive operation. The repository description explicitly highlights that the tool "will work in background so you can do your other works".

Unlike complex dictation software that often requires your full attention or a specific GUI focus, this tool operates via the command line. You simply trigger the listening module, and it begins logging audio to a text file immediately.

## Getting Started

Because it is built on Python, setting it up is standard for anyone familiar with `pip`.

**Dependencies**
To get started, you need to install the requirements found in the repository:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

**A Note for Windows Users**
Audio drivers can be tricky on Windows. If you run into issues installing `PyAudio`, the project recommends using `pipwin` to handle the binary installation:

```bash
python -m pip install pipwin
python -m pipwin install pyaudio
```

---

## The Workflow: From Voice to Notes

The project operates in two distinct phases: **Listening** and **Cleaning**.

### Phase 1: The Listener
To start capturing audio, you run the `listen_lecture` module. By default, this script creates a file named with the current date (e.g., `temp_lecture_MMDDYYYY.txt`).

```bash
python -m voice_notetaker.listen_lecture
```

**Customizing the Experience**
One of the stronger features of Voice Notetaker is its adaptability to different environments. If you are in a quiet room or a noisy hall, you can adjust the microphone sensitivity using the energy threshold flag:

*   **High Sensitivity:** Lower values (e.g., `--energy-threshold 100`) pick up quieter voices.
*   **Standard Sensitivity:** The default is set to 300.

You can also specify exactly which language the Google Web Speech API should listen for using the `--lang` flag (defaulting to `en-US`).

### Phase 2: The Cleanup
Raw transcriptions are rarely pretty. They often contain timestamps and fragmented sentences that make reading difficult.

Voice Notetaker includes a specific utility to handle this. The `cleanup_lecture` module takes your raw timestamped file and transforms it into a readable document.

```bash
python -m voice_notetaker.cleanup_lecture temp_lecture_02092026.txt
```

**What the cleanup script actually does:**
1.  **Removes Timestamps:** Strips the metadata from the raw capture.
2.  **Groups Text:** It organizes consecutive speech into 30-second sliding windows, making the flow of information much more natural to read.
3.  **Joins Segments:** It stitches the text together with periods to create a cohesive narrative.

 The result is a new file (appended with `_clean`) that is ready for review.

---

## Why Use It?

While there are many AI transcription services available today, Voice Notetaker offers a distinct advantage for developers and power users: **control**.

You control the output file destination, the specific audio device index, and the timeout duration. It is a local-first approach to transcription that fits neatly into a terminal-based workflow.

Whether you are archiving a lecture or keeping a record of a brainstorming session, Voice Notetaker provides a simple, scripted way to turn audio into actionable text data.

*Check out the repository to learn more about the specific configurations and device settings. https://github.com/kauser-cse-buet/voice_notetaker*