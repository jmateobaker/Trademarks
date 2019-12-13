import xml.etree.cElementTree as ET
import json

# Load Nintendo db or All pokemon db
db = 'E:\\trademark\\pokemon_trademarks_COMPLETE.xml'
#db = 'E:\\trademark\\pokemon_name_list.xml'

# Load it up
tree = ET.parse(db)
root = tree.getroot()

# List what you want
taglist = [
    'serial-number',
    'transaction-date',
    'case-file-header/filing-date',
    'case-file-header/registration-date',
    'case-file-header/abandonment-date',
    'case-file-header/status-date',
    'case-file-header/published-for-opposition-date',
    'case-file-header/renewal-date',
    'case-file-header/registration-date',
    'case-file-header/location-date',
    'classification/status-date',
    'first-use-anywhere-date',
    'first-use-in-commerce-date',
    'mark-identification',
    'party-name'
]

datalib = []

for r in root:
    datadict = {}
    for t in taglist:
        x = r.find('.//{}'.format(t))
        if x is not None:
            if "-date" not in t:
                datadict[t] = x.text
            elif x.text != "0":
               if x.text[-1] == "0":
                   datadict[t] = x.text[0:-1] + "1"
               else:
                   datadict[t] = x.text
    datalib.append(datadict)

# Save to file
with open('E:\\trademark\\pokemon_trademarks_COMPLETE.json', 'w') as jsonfile:
    json.dump(datalib, jsonfile, sort_keys=True, indent=4)
