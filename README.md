# S5000FmessageReader
&nbsp;&nbsp;&nbsp;&nbsp; Python class for reading S5000F&reg; message XML files. Returns a header with most of the file configurations and the lead's data is available as a Numpy array or a Pandas data frame.

## Dependencies
&nbsp;&nbsp;&nbsp;&nbsp; This reader needs the following libraries to parse the XML files:

- xmltodict (To read and create a dictionary from the XML file)
- numpy (To save the data from the leads into an array)
- pandas (To save the data from the leads into a structured data frame)
- xlwt (To save the lead data in a Excel file)

## Usage
&nbsp;&nbsp;&nbsp;&nbsp; The GEMuseXMLReader can be used in two different approaches:

- as a converter
- as a python class for accessing the data
----
### &nbsp;&nbsp;&nbsp;&nbsp; Converting XML file


&nbsp;&nbsp;&nbsp;&nbsp; The S5000FmessageReader can be called in the command line to convert the XML into a CSV, JSON, Excel, Numpy object, or all. Paired with the converted file is a JSON with the header information.

```
python3 S5000FmessageReader.py 'filename.XML' [arguments]
``` 
#### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Arguments

- [-csv [CSV]] - Convert the XML to a CSV. Output filename is optional.
- [-pcsv [PCSV]] - Convert the XML to a CSV (Pandas formated). Output filename is optional.
- [-ops [OPS]] - Convert the XML to a txt compatible with PLUX's opensignals. Output filename is optional.
- [-x [EXCEL]] - Convert the XML to a Excel. Output filename is optional.
- [-np [NUMPY]] - Convert the XML to a Numpy. Output filename is optional.
- [-json [JSON]] - Convert the XML to a JSON. Output filename is optional.
- [-all [ALL]] - Convert the XML to a CSV, Excel, Numpy and JSON. Output filename is optional.
----
### &nbsp;&nbsp;&nbsp;&nbsp; Python class

&nbsp;&nbsp;&nbsp;&nbsp; The S5000FmessageReader can be also be imported by another python script and used to converted the XML files, providing the data in either a Numpy array or a Panda data frame.

```python
import S5000FmessageReader

GEMuseData = GEMuseXMLReader('filename.XML')

GEMuseData.header ## Header containing the patient, device and acquisition session parameters

GEMuseData.dataObject ## Dictionary containing the data separated by lead

GEMuseData.dataFrame ## Panda's data frame containg the acquisition data

GEMuseData.dataArray ## Numpy matrix containing the acquisition data
``` 

## S5000F message

&nbsp;&nbsp;&nbsp;&nbsp; The S5000F message is structured as follows:

* Message
    * Header
        * message identifier
        * message date
        * message time
        * message status
        * message type
        
    * Content
        * to be completed

    * Trailer
        * Message sender
        * Message receiver
        * Message context
        * Message remarks
        * Message classification


* Could be more than one.

