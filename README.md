=XmlStreamer=

oskar.thornblad@gmail.com

Contributions from: Valiton GmbH

Free for everyone for everything, attribution voluntary
------

==Usage:==
Extend the class and implement the processNode method.

==Example:==
```php
class SimpleXmlStreamer extends XmlStreamer {
	public function processNode($xmlString, $elementName, $nodeIndex) {
		$xml = simplexml_load_string($xmlString);
		$something = (string)$xml->Something->SomethingElse->ReadThis;
		echo "$nodeIndex: Extracted string '$something' from parent node '$elementName'\n";		
		return true;
	}
}

$streamer = new SimpleXmlStreamer("myLargeXmlFile.xml");
if ($streamer->parse()) {
	echo "Finished successfully";
} else {
	echo "Couldn't find root node";
}
```
