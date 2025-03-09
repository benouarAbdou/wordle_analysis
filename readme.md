# Wordle Optimization Analysis

## Overview

This project uses mathematical analysis to optimize strategies for playing [Wordle](https://www.nytimes.com/games/wordle/), a popular word-guessing game where players have six attempts to identify a 5-letter word. By analyzing a dataset of **5,757 unique valid 5-letter words** from a local file (`5words.txt`), this Jupyter Notebook (`wordle.ipynb`) identifies patterns in letter frequencies, positional distributions, vowel-consonant structures, and common letter sequences. The goal is to determine the best starting words and gameplay tactics, grounded in data-driven insights as of March 09, 2025. Techniques include statistical frequency analysis, positional mapping, and n-gram identification, all aimed at maximizing success within Wordle’s constraints.

## Dataset
- **Source**: `5words.txt` (included in the repository)
- **Size**: **5,757 unique 5-letter words**, cleaned to ensure only alphabetic, unique entries are analyzed.
- **Significance**: This robust sample represents a wide range of potential Wordle solutions, providing a reliable basis for statistical conclusions.

## Key Findings

### Letter Frequencies
- **Top 5 Letters**:
  - `s`: 10.54%
  - `e`: 10.45%
  - `a`: 8.16%
  - `o`: 6.65%
  - `r`: 6.64%
- **Insight**: These letters account for over 42% of all occurrences, making them critical for early guesses.

### Positional Letter Patterns
- **Most Common Letters by Position**:
  - Position 1: `s` (724 occurrences, 12.58%)
  - Position 2: `a` (930 occurrences, 16.15%)
  - Position 3: `a` (605 occurrences, 10.51%)
  - Position 4: `e` (1,228 occurrences, 21.33%)
  - Position 5: `s` (1,764 occurrences, 30.64%)
- **Analysis**: `s` frequently anchors words at the start and end (e.g., "sleep", "masts"), while `a` and `e` dominate inner positions, reflecting common English word structures.

### Vowel-Consonant Distribution
- **Patterns and Counts**:
  - 2 Vowels, 3 Consonants: 3,307 words (e.g., "sleep", "quoth")
  - 1 Vowel, 4 Consonants: 1,974 words (e.g., "blabs", "junks")
  - 3 Vowels, 2 Consonants: 443 words (e.g., "abase", "ounce")
  - 0 Vowels, 5 Consonants: 24 words (e.g., "shyly", "psych")
  - 4 Vowels, 1 Consonant: 9 words (e.g., "queue", "ouija")
- **Observation**: The 2V3C pattern dominates (57% of words), indicating a preference for balanced structures in 5-letter words.

### Top Starting Words
- **With Duplicates Allowed**:
  - "esses" (52.52%), "asses" (50.22%), "eases" (50.14%), "seers" (48.62%), "seest" (47.49%)
  - These leverage frequent letters like `s` and `e` in strong positional alignments.
- **With Unique Letters**:
  - "arose" (42.44%), "raise" (41.31%), "arise" (41.31%), "aloes" (41.31%), "stoae" (41.31%)
  - These test five distinct high-frequency letters (`a`, `r`, `s`, `e`, `o`), maximizing initial information.

### Worst Starting Words
- **With Duplicates**:
  - "fuzzy" (9.75%), "buzzy" (10.28%), "whizz" (11.05%), "fizzy" (11.50%), "jazzy" (12.48%)
- **With Unique Letters**:
  - "jumpy" (13.42%), "junky" (13.71%), "whump" (14.61%), "mujik" (14.62%), "humpf" (14.81%)
- **Takeaway**: Words with rare letters (`z`, `j`, `q`) perform poorly due to their scarcity in the dataset.

### Common Bigrams and Trigrams
- **Top Bigrams**: "es" (433, e.g., "doges"), "er" (425, e.g., "sherd"), "ed" (352, e.g., "suede"), "re" (282, e.g., "faire"), "in" (273, e.g., "finny")
- **Top Trigrams**: "ing" (52, e.g., "fling"), "res" (49, e.g., "lores"), "lls" (48, e.g., "yells"), "ate" (48, e.g., "fates"), "ine" (42, e.g., "vines")
- **Significance**: These sequences are prevalent in word endings and cores, offering clues to common word families.

## Conclusions and Wordle Strategy
The analysis provides a clear, data-driven approach to excelling at Wordle:
- **Optimal Starting Words**: Begin with "stare" (41.29%) or "arose" (42.44%) for unique-letter coverage, testing `s`, `a`, `r`, `e`, and `o` in frequent positions (e.g., `s` at 1 and 5, `a` at 2, `e` at 4). For duplicates, "esses" (52.52%) capitalizes on `s` and `e` dominance, though it risks redundancy.
- **Second Guess Tactics**: Use feedback to target untested frequent letters (e.g., `o`, `t`, `l`) and common sequences (e.g., "es", "ing"). For example, if "stare" reveals `s` and `e`, "loins" tests `o`, `i`, `n` and the "in" bigram.
- **Pattern Preference**: Favor 2V3C words (e.g., "sleep"), which align with 57% of the dataset, over rare extremes like "fuzzy" (0V5C) or "queue" (4V1C) unless clues suggest otherwise.
- **Avoid Low-Value Words**: Skip words with `z`, `j`, `q`, or `f` (e.g., "jumpy", "fuzzy") due to their low frequency and poor positional fit.
- **Sequence Strategy**: Incorporate bigrams ("es", "er") and trigrams ("ing", "res") to quickly narrow down possibilities (e.g., "fling" for "ing").

This approach—starting with a high-information word like "stare" and adapting with frequent letters and patterns—systematically reduces the word pool, enhancing efficiency and success in Wordle.

## Usage
1. **Requirements**: Python 3.x with libraries: `matplotlib`, `seaborn`, `numpy`, `collections`, `re`. Install via `pip install -r 5words.txt`.
2. **Running the Notebook**:
   - Place `5words.txt` in the same directory as `wordle.ipynb`.
   - Open the notebook in Jupyter: `jupyter notebook wordle.ipynb`.
   - Run all cells to generate analyses and visualizations (e.g., vowel heatmap).
3. **Customization**: Modify the dataset or scoring logic in the notebook to refine strategies further.

## Future Enhancements
- Add entropy-based word scoring to rank starters by information gain.
- Expand positional vowel analysis with a full heatmap in text form.
- Include interactive tools for real-time guess suggestions.

Explore the notebook for detailed code and visualizations, and use these insights to outsmart Wordle with math!