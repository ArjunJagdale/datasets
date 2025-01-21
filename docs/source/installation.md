# Installation

Before you start, you'll need to setup your environment and install the appropriate packages. 🤗 Datasets is tested on **Python 3.7+**.

<Tip>

If you want to use 🤗 Datasets with TensorFlow or PyTorch, you'll need to install them separately. Refer to the [TensorFlow installation page](https://www.tensorflow.org/install/pip#tensorflow-2-packages-are-available) or the [PyTorch installation page](https://pytorch.org/get-started/locally/#start-locally) for the specific install command for your framework.

</Tip>

## Virtual environment

You should install 🤗 Datasets in a [virtual environment](https://docs.python.org/3/library/venv.html) to keep things tidy and avoid dependency conflicts.

Create and navigate to your project directory.

```bash
mkdir ~/my-project
cd ~/my-project
```

Start a virtual environment inside your directory. You can use python or [uv](https://docs.astral.sh/uv/) (refer to [Installation](https://docs.astral.sh/uv/getting-started/installation/) for installation instructions), a fast Rust-based Python package and project manager.

<hfoptions id="install">
<hfoption id="uv">

```bash
uv venv my-env
source my-env/bin/activate
```

</hfoption>
<hfoption id="python">

```bash
python -m venv .env
source ./env/bin/activate
```

</hfoption>
</hfoptions>

Once you've created your virtual environment, you can install 🤗 Datasets in it.

## pip

The most straightforward way to install 🤗 Datasets is with pip or uv.

<hfoptions id="pip">
<hfoption id="uv">

```bash
uv pip install datasets
```

</hfoption>
<hfoption id="pip">

```bash
pip install datasets
```

</hfoption>
</hfoptions>

Run the following command to check if 🤗 Datasets has been properly installed:

```bash
python -c "from datasets import load_dataset; print(load_dataset('squad', split='train')[0])"
```

This command downloads version 1 of the [Stanford Question Answering Dataset (SQuAD)](https://rajpurkar.github.io/SQuAD-explorer/), loads the training split, and prints the first training example. You should see:

```python
{'answers': {'answer_start': [515], 'text': ['Saint Bernadette Soubirous']}, 'context': 'Architecturally, the school has a Catholic character. Atop the Main Building\'s gold dome is a golden statue of the Virgin Mary. Immediately in front of the Main Building and facing it, is a copper statue of Christ with arms upraised with the legend "Venite Ad Me Omnes". Next to the Main Building is the Basilica of the Sacred Heart. Immediately behind the basilica is the Grotto, a Marian place of prayer and reflection. It is a replica of the grotto at Lourdes, France where the Virgin Mary reputedly appeared to Saint Bernadette Soubirous in 1858. At the end of the main drive (and in a direct line that connects through 3 statues and the Gold Dome), is a simple, modern stone statue of Mary.', 'id': '5733be284776f41900661182', 'question': 'To whom did the Virgin Mary allegedly appear in 1858 in Lourdes France?', 'title': 'University_of_Notre_Dame'}
```

## Audio

To work with audio datasets, you need to install the [`Audio`] feature as an extra dependency:

```bash
pip install datasets[audio]
```

<Tip warning={true}>

To decode mp3 files, you need to have at least version 1.1.0 of the `libsndfile` system library. Usually, it's bundled with the python [`soundfile`](https://github.com/bastibe/python-soundfile) package, which is installed as an extra audio dependency for 🤗 Datasets.
For Linux, the required version of `libsndfile` is bundled with `soundfile` starting from version 0.12.0. You can run the following command to determine which version of `libsndfile` is being used by `soundfile`:

```bash
python -c "import soundfile; print(soundfile.__libsndfile_version__)"
```

</Tip>


## Vision

To work with image datasets, you need to install the [`Image`] feature as an extra dependency:

```bash
pip install datasets[vision]
```

## source

Building 🤗 Datasets from source lets you make changes to the code base. To install from the source, clone the repository and install with the following commands:

```bash
git clone https://github.com/huggingface/datasets.git
cd datasets
pip install -e .
```

Again, you can check if 🤗 Datasets was properly installed with the following command:

```bash
python -c "from datasets import load_dataset; print(load_dataset('squad', split='train')[0])"
```

## conda

🤗 Datasets can also be installed from conda, a package management system:

```bash
conda install -c huggingface -c conda-forge datasets
```
