# Input-Pipeline
# 🏗️ Scalable Data Engineering: TensorFlow Input Pipelines

In real-world Deep Learning, data is often too massive to load into RAM all at once. This repository explores the **tf.data API**, demonstrating how to build high-performance input pipelines that load, transform, and feed data to a model efficiently using **streaming** and **lazy evaluation**.

---

## 🛠️ The Data Engineering Stack
* **Framework:** TensorFlow (tf.data)
* **Language:** Python
* **Key Operations:** Filter, Map, Shuffle, Batch, and Prefetch.

---

## 🧠 Core Concepts Implemented

### 1. From Tensors to Datasets
* **`from_tensor_slices`:** Converted standard Python lists and NumPy arrays into `tf.data.Dataset` objects.
* **Lazy Evaluation:** Demonstrated that `tf.data` doesn't process data immediately; it creates a "plan" (pipeline) that only executes when you iterate through it.

### 2. The Transformation Pipeline
I implemented a multi-stage pipeline to clean and prepare data:
* **Filtering:** Removing invalid data points (e.g., negative values in a sales dataset).
* **Mapping:** Applying custom functions (like `scale`) to normalize images or transform features across the entire dataset.
* **Shuffling:** Ensuring the model doesn't "memorize" the order of data, which is vital for proper generalization.
* **Batching:** Grouping individual data points into sets of 32 or 64 for efficient GPU computation.



### 3. Handling Image Data
* **Path to Image:** Used the pipeline to take a list of file paths, read the raw bytes from disk, decode them into JPEG/PNG, and resize them on the fly.
* **Memory Management:** By streaming images from the disk instead of loading them all at once, this pipeline allows for training on datasets containing millions of images on standard hardware.

---

## 📈 Why use tf.data?
* **Efficiency:** Traditional `for-loops` in Python are slow. `tf.data` uses C++ multithreading under the hood.
* **Prefetching:** While the GPU is training on **Batch 1**, `tf.data` is already preparing **Batch 2** in the background, eliminating the "bottleneck" effect.
* **Scalability:** Easily switch from local files to cloud storage (like Google Cloud Storage or S3) without changing the core logic.

[Image showing the prefetching mechanism in TensorFlow where CPU and GPU work in parallel]

---

## 🚀 How to Run

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/Manaswi9123/Python-DataScience-Fundamentals.git](https://github.com/Manaswi9123/Python-DataScience-Fundamentals.git)

2. **Install Dependencies:**
        pip install tensorflow
   
3. **Execute:**
      Open Input pipeline.ipynb in Jupyter or VS Code. Run the cells to see how a list of sales numbers or a directory of           flower images is transformed into a high-performance stream.
