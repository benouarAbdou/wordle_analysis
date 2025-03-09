# Wordle Optimization Analysis

## Overview

This project uses mathematical analysis to optimize strategies for playing [Wordle](https://www.nytimes.com/games/wordle/), a popular word-guessing game where players have six attempts to identify a 5-letter word. By analyzing a dataset of **5,757 unique valid 5-letter words** from a local file (`5words.txt`), this Jupyter Notebook (`wordle.ipynb`) identifies patterns in letter frequencies, positional distributions, vowel-consonant structures, and common letter sequences. The goal is to determine the best starting words and gameplay tactics, grounded in data-driven insights as of March 09, 2025. Techniques include statistical frequency analysis, positional mapping, and n-gram identification, all aimed at maximizing success within Wordle’s constraints.

## Dataset
- **Source**: `5words.txt` (included in the repository)
- **Size**: **5,757 unique 5-letter words**, cleaned to ensure only alphabetic, unique entries are analyzed.
- **Significance**: This robust sample represents a wide range of potential Wordle solutions, providing a reliable basis for statistical conclusions.

## Key Findings

### Letter Frequencies
The top 5 letters account for over 42% of all letter occurrences, highlighting their importance in early guesses.

| Letter | Frequency (%) |
|--------|---------------|
| `s`    | 10.54         |
| `e`    | 10.45         |
| `a`    | 8.16          |
| `o`    | 6.65          |
| `r`    | 6.64          |

- **Insight**: `s` and `e` dominate, making them critical for initial Wordle guesses.

### Positional Letter Patterns
Letters vary significantly by position, with `s` anchoring the start and end of words.

| Position | Most Common Letter | Occurrences | Percentage (%) |
|----------|--------------------|-------------|----------------|
| 1        | `s`                | 724         | 12.58          |
| 2        | `a`                | 930         | 16.15          |
| 3        | `a`                | 605         | 10.51          |
| 4        | `e`                | 1,228       | 21.33          |
| 5        | `s`                | 1,764       | 30.64          |

- **Analysis**: `s` frequently appears at positions 1 and 5 (e.g., "sleep", "masts"), while `a` and `e` are prevalent in inner positions, reflecting common English word structures.

### Vowel-Consonant Distribution
The dataset favors balanced vowel-consonant patterns, with 2V3C being the most common.

| Pattern             | Word Count | Examples             |
|---------------------|------------|----------------------|
| 2 Vowels, 3 Consonants | 3,307   | sleep, quoth, doges  |
| 1 Vowel, 4 Consonants  | 1,974   | blabs, junks, masts  |
| 3 Vowels, 2 Consonants | 443     | abase, ounce, mania  |
| 0 Vowels, 5 Consonants | 24      | shyly, psych, lynch  |
| 4 Vowels, 1 Consonant  | 9       | queue, aurae, ouija  |

- **Observation**: The 2V3C pattern dominates (57% of words), suggesting Wordle solutions typically balance vowels and consonants.

### Top Starting Words
#### With Duplicates Allowed
These words leverage frequent letters like `s` and `e` in strong positional alignments.

| Word    | Score (%) |
|---------|-----------|
| esses   | 52.52     |
| asses   | 50.22     |
| eases   | 50.14     |
| seers   | 48.62     |
| seest   | 47.49     |

#### With Unique Letters
These test five distinct high-frequency letters, maximizing initial information.

| Word    | Score (%) |
|---------|-----------|
| arose   | 42.44     |
| raise   | 41.31     |
| arise   | 41.31     |
| aloes   | 41.31     |
| stoae   | 41.31     |

### Worst Starting Words
#### With Duplicates
These perform poorly due to rare letters like `z` and `j`.

| Word    | Score (%) |
|---------|-----------|
| fuzzy   | 9.75      |
| buzzy   | 10.28     |
| whizz   | 11.05     |
| fizzy   | 11.50     |
| jazzy   | 12.48     |

#### With Unique Letters
Rare letters (`j`, `q`, `z`) drag down these scores.

| Word    | Score (%) |
|---------|-----------|
| jumpy   | 13.42     |
| junky   | 13.71     |
| whump   | 14.61     |
| mujik   | 14.62     |
| humpf   | 14.81     |

- **Takeaway**: Avoid words with low-frequency letters (`z`, `j`, `q`) as they rarely appear in the dataset.

### Common Bigrams and Trigrams
#### Top Bigrams
Prevalent sequences often appear in word endings or cores.

| Bigram | Frequency | Example |
|--------|-----------|---------|
| es     | 433       | doges   |
| er     | 425       | sherd   |
| ed     | 352       | suede   |
| re     | 282       | faire   |
| in     | 273       | finny   |

#### Top Trigrams
These chunks highlight common structural patterns.

| Trigram | Frequency | Example |
|---------|-----------|---------|
| ing     | 52        | fling   |
| res     | 49        | lores   |
| lls     | 48        | yells   |
| ate     | 48        | fates   |
| ine     | 42        | vines   |

- **Significance**: Sequences like "es", "er", and "ing" are versatile and frequent, aiding in pattern recognition.

## Conclusions and Wordle Strategy
The analysis provides a clear, data-driven approach to excelling at Wordle:
- **Optimal Starting Words**: Start with "stare" (41.29%) or "arose" (42.44%) for unique-letter coverage, testing `s`, `a`, `r`, `e`, and `o` in frequent positions (e.g., `s` at 1 and 5, `a` at 2, `e` at 4). For duplicates, "esses" (52.52%) capitalizes on `s` and `e` dominance, though it risks redundancy.
- **Second Guess Tactics**: Use feedback to target untested frequent letters (e.g., `o`, `t`, `l`) and common sequences (e.g., "es", "ing"). For example, if "stare" reveals `s` and `e`, "loins" tests `o`, `i`, `n` and the "in" bigram.
- **Pattern Preference**: Favor 2V3C words (e.g., "sleep"), aligning with 57% of the dataset, over rare extremes like "fuzzy" (0V5C) or "queue" (4V1C) unless clues suggest otherwise.
- **Avoid Low-Value Words**: Skip words with `z`, `j`, `q`, or `f` (e.g., "jumpy", "fuzzy") due to their low frequency and poor positional fit.
- **Sequence Strategy**: Incorporate bigrams ("es", "er") and trigrams ("ing", "res") to narrow possibilities (e.g., "fling" for "ing").

This approach—starting with a high-information word like "stare" and adapting with frequent letters and patterns—systematically reduces the word pool, enhancing efficiency and success in Wordle.

## Usage
1. **Requirements**: Python 3.x with libraries: `matplotlib`, `seaborn`, `numpy`, `collections`, `re`.
2. **Running the Notebook**:
   - Place `5words.txt` in the same directory as `wordle.ipynb`.
   - Open in Jupyter: `jupyter notebook wordle.ipynb`.
   - Run all cells to generate analyses and visualizations (e.g., vowel heatmap).
3. **Customization**: Modify the dataset or scoring logic in the notebook to refine strategies further.

## Future Enhancements
- Add entropy-based word scoring to rank starters by information gain.
- Expand positional vowel analysis with a full heatmap in text form.
- Include interactive tools for real-time guess suggestions.

Explore the notebook for detailed code and visualizations, and use these insights to outsmart Wordle with math!
