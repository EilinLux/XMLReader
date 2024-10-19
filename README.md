# XML Reader

This Python class (`XMLReader`) provides a way to read and extract data from XML files with a specific structure. It uses a YAML configuration file to define the elements to extract and handles nested structures.

## Features

* Reads and parses multiple XML files.
* Extracts data based on a YAML configuration file.
* Handles nested "tracker" elements recursively.
* Stores the extracted data in a pandas DataFrame.
* Provides basic error handling for file and XML parsing errors.

## Requirements

* Python 3.6 or higher
* `xml.etree.ElementTree` (built-in)
* `pandas`
* `pyyaml`

## Installation

1.  Install the required packages:

    ```bash
    pip install pandas pyyaml
    ```

## Configuration

Create a YAML configuration file (e.g., `config.yml`) to define the XML structure and the elements to extract. Here's an example:

```yaml
head:
  - element1
  - element2

tracker_element: tracker  # Name of the tracker element (default: 'tracker')

item_elements:
  - item1
  - item2
  - item3
```
* head: A list of element names to extract from the <head> section of the XML.
* tracker_element: The name of the element that contains the repeating data (default: tracker).
* item_elements: A list of element names to extract from each tracker element.
## Usage
```yaml Python
from xml_reader import XMLReader

# Create an XMLReader instance
reader = XMLReader(config_file="config.yml")

# Specify the XML filenames or a glob pattern
filenames = glob.glob("path/to/xml/files/*.xml")  # Or a list of filenames

# Read the XML files and get the data as a pandas DataFrame
df = reader.read_xml_files(filenames)

# Process the DataFrame
print(df)
```

Example XML Structure
The code expects an XML structure similar to this:
``` XML
<root>
  <head>
    <element1>value1</element1>
    <element2>value2</element2>
  </head>
  <tracker>
    <item1>value3</item1>
    <item2>value4</item2>
    <item3>value5</item3>
  </tracker>
  <tracker>
    <item1>value6</item1>
    <item2>value7</item2>
    <item3>value8</item3>
  </tracker>
</root>
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
