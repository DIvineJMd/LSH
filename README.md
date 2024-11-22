
## LSH-Based Text Similarity 

This project implements a Locality-Sensitive Hashing (LSH) model to identify the top-5 most similar text samples for each input text. The goal is to mimic a given ground truth JSON file (`items.json`) containing the top-5 similar data samples for each input sample. The model uses MinHash signatures and LSH for efficient similarity computation, while also applying feature engineering to improve performance.

---

## Project Structure

- **`ids.txt`**  
  Contains unique IDs for each data sample, with one ID per line.

- **`texts.txt`**  
  Contains corresponding textual data for each ID, with one text sample per line.

- **`items.json`**  
  A ground truth file mapping each data sample ID to a list of its top-5 most similar data samples.

---

## How It Works

1. **Preprocessing**  
   - Cleans and filters the input data (`texts.txt`) to remove empty or invalid lines.
   - Strips whitespace and ensures alignment between `ids` and `texts`.

2. **Feature Engineering**  
   - Converts text samples into TF-IDF vectors using `TfidfVectorizer`.
   - Splits each text into shingles (word-level tokens).

3. **MinHash Signatures**  
   - Generates MinHash signatures for each text sample to enable efficient similarity estimation.

4. **Locality-Sensitive Hashing (LSH)**  
   - Uses the MinHashLSH algorithm to group similar text samples into candidate pairs efficiently.

5. **Top-5 Prediction**  
   - Queries the LSH structure to retrieve the top-5 most similar text samples for each input.

6. **Evaluation**  
   - Compares the predicted top-5 samples with the ground truth (`items.json`) to compute an intersection score.
   - Calculates descriptive statistics of the intersection scores.

7. **Visualization**  
   - Generates a histogram and box plot of the intersection scores to visualize the model's performance.

---

## Prerequisites
# Running the Project
-- 1. Prepare the Input Files
Ensure the following files are available in the same directory as the script:

ids.txt
texts.txt
items.json
-- 2. Run the Script
Use the following command to execute the script:

3. Outputs
Performance Statistics: Prints statistics of intersection scores using pandas.describe().
## Visualizations:
A histogram of intersection scores.
A box plot of intersection scores.
## Expected Output
# Sample Performance Statistics:

count    148928.000000
mean          0.000470
std           0.021675
min           0.000000
25%           0.000000
50%           0.000000
75%           0.000000
max           1.000000
dtype: float64
## Sample Visualizations:
Histogram: Shows the distribution of intersection scores.
Box Plot: Displays the spread and outliers of intersection scores.
Debugging and Common Issues
Mismatch Between ids and texts
If there is a mismatch in the number of lines between ids.txt and texts.txt, the script:

Logs the difference in lengths.
## Identifies problematic lines for debugging.
Empty or Invalid Lines
The script filters out empty or whitespace-only lines in texts.txt to avoid alignment issues.

## Notes
The performance of the LSH model depends heavily on feature engineering, such as the choice of shingles and TF-IDF preprocessing.
The evaluation score ranges between 0 and 5, where 5 indicates a perfect match with the ground truth.
Files Generated
Intersection Scores Statistics: A pandas series describing intersection scores.
Histogram and Box Plot: Visualization of model performance.


Install the required Python packages before running the code:

```bash
pip install pandas scikit-learn datasketch matplotlib
