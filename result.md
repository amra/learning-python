Task results

# Basic 01 - Hello world

```python
print("Hello world")
```

# Basic 02 - Read file
```python
f = open("files/everything-is-awesome.txt", "r")
print(f.readline())
```

# Basic 03 - Count lines

```python
f = open("files/everything-is-awesome.txt", "r")
count = 0
for line in f:
    count += 1
print("count: " + str(count))
```

# XML 01 - Find surnames
In the example replace `'.//record[firstname="John"]'` with `'.//record[surname="Doe"]'`

So the result is:
```python
import xml.etree.ElementTree as ET

root = ET.parse('./files/people.xml').getroot()
filtered = root.findall('.//record[surname="Doe"]')
for element in filtered:
    print(ET.tostring(element).decode('utf-8'))
```

# XML 02 - List surnames only

```python
import xml.etree.ElementTree as ET

root = ET.parse('./files/people.xml').getroot()
filtered = root.findall('.//record/surname')

for element in filtered:
    print(ET.tostring(element, method="text").decode('utf-8'))
```

