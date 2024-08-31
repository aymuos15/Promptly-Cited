# Zero-Shot citation generation for Large Language Models in academic papers

In small context settings (currently 5 papers of 4 pages each) -- can we make llms provide answers with citations?

## Motivation

- Nothing like this has been done before. [Please do send material if there is.]

## To Run (using [Ollama](https://ollama.com/))

1. Follow this [Gist](https://gist.github.com/aymuos15/fc1d084f2da9ddb2f3588d4d856cfa1b) to setup Ollama locally.

2. Run all on `ollama.ipynb`

## Basic Methodology Summary:

#### Dataset:
1. Get Latex Zipz
2. Unzip and Make them into indiviual folders.

#### Preprocessing:

3. Get all files from the folder.
4. Remove all non .tex files.
5. Remove all the latex commands.
6. Merge all files into one and then remove all subdirectories.
        - (Optional) Here we have cut the papers a 1000 characters each from back and front.
7. Make a dictionary of Paper Name (taken from folder) [Key] and Paper Content [Value]

#### Inference 1: (Single Paper Wise)
8. With The prompt, `inference` it for each paper
9. Collect those responses in a nice way

#### Inference 2: (All relevant paper wise)
10. Create the prompt based on output of inference 1.
11. Ask it for the answer to your question summed up so it can account for multiple papers having answers to the same thing.

#### Inference 3: (Follow up! Asking Quetions on the collected Inference)
12. Make a prompt based on the above collected material and run inference

## Dataset Creation
1. Unzip all the `.tar` files into `\dataset`. It should look like:

```dataset
├── Paper 1 Folder containing all files.
├── Paper 2 Folder containing all files.
├── ... Paper N ...
```

That's it!

## To-Do's (and Limitations)
- [] (Limitation) Test for more number of papers
- [] Figure out a way to generate a nice baseline?
- [] If we scale and fail, convert this in to a few-shot problem?
- [] (Limitation_ Only works for tex downloads from arxiv. How to solve that?

# Acknowledgement.

HUGE THANKS TO [CEREBRAS AI](https://cerebras.ai/) for giving us free credits on their inference accelarator platform.

