# **Transfer Learning Based Performance Evaluation Model**
This work demonstrates how the transfer learning (TL) can be used to develop a performance evaluation model in wireless networks with less amount of training data when the wireless environments change. The data used is a time-series data, which is obtained from Telia mobile network operator present in Norway. The data is available for a single day, as of 01/02/2021. It comprises of two categories. (i) Metadata, and (ii) Performance data.\ 
  Metadata consists of four features, namely: measurement time stamps ``ts``, node (probe) identifier ``node_id``, metadata key/variable ``metadata_key``, metadata value ``metadata_value``. There are four metadata_keys, namely: ``Cid`` - Identifier of the base-station that the probe is camping on; ``Mode`` - Radio access technology: 4G/LTE - 6, 3G - 5, 2G - 2; Reference Signal Received Power ``RSRP``; Reference Signal Received Quality ``RSRQ``; Received Signal Strength Indicator ``RSSI``. Note- The metadata values are collected once per minute.\ 
  Performance data consists of four features, namely: measurement time stamps ``ts``; node (probe) identifier ``node_id``; packet loss percentage ``packet_loss``; and average round trip delay ``rtt_avg``. Note- The performance data is collected at every 5 minutes interval.\

## **Baseline Model**
To develop baseline model for each node which has mode = 6 (There are 70 nodes of this type.), we prepared dataframe for each node with input comprising rsrp1,.....,rsrp5, rsrq1,....,rsrq5, rssi1,....rssi5 and output comprising rtt_avg value at each 5th minute interval. In other words, the input to the RNN is node identifiers, for example, rsrp, rsrq, and rssi for each node in a batch and the output is the average round-trip delay (rtt avg). 
  The dataframe of each node comprises of 288 rows (= 24 hours x 60 minutes/5) and 16 columns (15 for inputs and 1 for output rtt_avg). We save the dataframe of each node in .csv file in order to build baseline model.
  Since the data is containing time-stamps, so we are training a Recurrent Neural Network (RNN) for each node. We normalize the dataset by having zero mean and scaling to unit variance. The same RNN structure is used for the training of each node (total 70 nodes here). 
  Note- RNN is a type of neural network in which the output from previous step is fed as input to the current step. The ``hidden state`` in RNN remembers some information about a sequence. RNN has a ``memory`` which remembers all information about what has been calculated.
  
 ## **Performing Transfer learning using Baseline model of each Node**
After training RNN for each node and obtaining baseline model for each node, we perform TL in order to obtain test MSE and number of epochs. Out of 70 nodes, we will keep/assume the first node as the baseline model and perform TL by transferring the baseline model to the remaining 69 nodes and train the RNN and save test MSE and number of epochs. In the same fashion, we keep/assume the second node as the baseline model and perform TL by transferring this baseline model to the remaining 69 nodes and train the RNN and save test MSE and number of epochs. This process continues until the last 70th node becomes the baseline model and transferred to the remaining 69 nodes to train RNN and save test MSE and number of epochs. This results in 4761 (69 nodes x 69 model transferred) combinations. 

In each scenario of TL, the RNN is trained with different splits of training and testing data. With each split of data, we optimise the MSE and store the test MSE corresponding to TL and number of training epochs to use it further for the similarity between two nodes.

# **Requirements:**
* Time-Series Data Modelling 
* Transfer learning
* Recurrent Neural Network
* TensorFlow
* Python

## **License**
* The project is licensed under the GNU General Public License v3.0.
* You may obtain a copy of the License at https://www.gnu.org/licenses/gpl-3.0.en.html



