# **Transfer Learning Based Performance Evaluation Model**
This work demonstrates how the transfer learning can be used to develop a performance evaluation model in wireless networks with less amount of training data when the wireless environments change. The data used is a time-series data, which is obtained from Telia mobile network operator present in Norway. The data is available for a single day, as of 01/02/2021. It comprises of two categories. (i) Metadata, and (ii) Performance data. Metadata consists of four features, namely: measurement time stamps ``ts``, node (probe) identifier ``node_id``, metadata key/variable ``metadata_key``, metadata value ``metadata_value``. There are four metadata_keys, namely: ``Cid`` - Identifier of the base-station that the probe is camping on; ``Mode`` - Radio access technology: 4G/LTE - 6, 3G - 5, 2G - 2; Reference Signal Received Power ``RSRP``; Reference Signal Received Quality ``RSRQ``; Received Signal Strength Indicator ``RSSI``. Note- The metadata values are collected once per minute. 



# **Requirements:**
* Time-Series Data Modelling 
* Transfer learning
* Recurrent Neural Network
* TensorFlow
* Python

## **License**
* The project is licensed under the GNU General Public License v3.0.
* You may obtain a copy of the License at https://www.gnu.org/licenses/gpl-3.0.en.html



