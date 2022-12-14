# Semantic Answer Type Prediction

## Paper

Read our paper DAT (2).pdf

## How to run

Required packages can be found in the `requirements.txt` file.

```bash
pip install -r requirements.txt
```

To prepare for Part 1 run the file [`src/round1_prep.py](./src/round1_prep.py). This will preprocess the questions and train the ML predictor.

```bash
python src/round1_prep.py
```

To create the entity representation the following files should be extracted from the dbpedia dump and be placed in the [`Data/Dbpedia/`](./Data/dbpedia/) folder.

- `dbpedia_2016.nt`
- `instance_types_en.ttl`
- `long_abstracts_en.ttl`
- `redirects_en.ttl`
- `disambiguations_en.ttl`
- `article_categories_en.ttl`

To preprocess the files and prepare the index the [`src/DBpedia.py`](./src/DBpedia.py) file should be run. It can be run using the following command.

```bash
python src/DBpedia.py
```

After the data has been preprocessed the baseline can be run using the command:

```bash
python src/predictor.py
```

The completed predictions can be found in the following file:  [`Data/baseline_predictions.json`](./Data/baseline_predictions.json)

The scoring can be obtained by running the following command:

```bash
python Data\smart-dataset-master\evaluation\dbpedia\evaluate.py --type_hierarchy_tsv=Data\smart-dataset-master\evaluation\dbpedia\dbpedia_types.tsv --ground_truth_json=Data\smart-dataset-master\datasets\DBpedia\smarttask_dbpedia_test.json --system_output_json=Data/baseline_predictions.json
```
