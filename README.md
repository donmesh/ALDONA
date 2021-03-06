# ALDONA
Code for ALDONA: A Hybrid Solution for Sentence-Level Aspect Based Sentiment Analysis using a Lexicalized Domain Ontology and Neural Attention Model

All software is written in PYTHON3 (https://www.python.org/) and makes use of the TensorFlow framework (https://www.tensorflow.org/).

## Installation Instructions:
### Download required files:
1. Download ontology: https://github.com/KSchouten/Heracles/tree/master/src/main/resources/externalData
2. Download SemEval2016 Dataset: http://alt.qcri.org/semeval2016/task5/index.php?id=data-and-tools
3. Download GloVe Embeddings: http://nlp.stanford.edu/data/glove.42B.300d.zip

### Setup Environment

1. Download and install PYTHON3.

2. Install the required packages from the requirements.txt file by running the following command in a command line: pip install -r requirements.txt

3. Download and unzip ALDONA.zip

4. Place the ontology.owl in the Ontology folder

5. Place glove.42B.300d.txt in Data/Glove

6. Place EN_REST_SB1_TEST.xml.gold in Data/Test_data

7. Place ABSA16_Restaurants_Train_SB1_v2.xml in Data/Train_data

### Run Software
1. Configure the main file to the required configuration (MAIN.py)
2. Run the program from the command line by the following command: python MAIN.py

## Software explanation:
The environment contains the following main file that can be run: MAIN.py
- MAIN.py: the main program to choose data generation options, hyper-parameters and to run specified models
- MAIN_Data_Generator.py: the centralized program to read raw data and transform into the required formats. It incorporates the following programs:
    - Data_Processer.py: program to extract raw data and transform it into vectors
        - Data_Reader.py: program to extract raw data
    - GloVe.py: program to transform GloVe vectors to the required format and create a list of all available words
        - Word_Embeddings.py: transform data vectors into embeddings
        - Visualization.py: program to visualize data
- Optimization.py: the central program to run any model optimization
    - ALDONA_Classification.py: Tensorflow implementation of ALDONA algorithm
        - Neural_Attention_Model.py: Neural Network part of ALDONA
    - Baseline_Models.py: Tensorflow implementation of the baseline models
- Attention_Modules.py: Tensorflow implementation of position and context attention modules
- Algebra_Operators.py: matrix-tensor and tensor-tensor multiplication definitions
- Data_Neural.py: program to create left-context/aspect/right-context data
- Ontology_Reader.py: PYTHON3 implementation for the ontology reasoner

## Directory explanation:
- Codes: folder containing all .py files
- Data: folder with all data files
    - Glove: directory for GloVe word embedding vectors ("glove.42B.300d.txt"). Two new files ("glove.42B.300d.txt.word2vec" and "glove.42B.300d_keys.txt") will be generated by MainData() in MAIN_Data_Generator.py
    - Numpy: directory for data (.npy format) which will be generated in the process
    - Test_data: directory for the input test file ("EN_REST_SB1_TEST.xml.gold"). It can be changed if xml structure remains the same.
    - Train_data: directory for the input train file ("ABSA16_Restaurants_Train_SB1_v2.xml"). It can be changed if xml structure remains the same.
- Ontology: directory for "ontology.owl"
- Results: directory for results stored in .csv format