# Cambodia Gazetteer

Cambodia geographical index in JSON format.

## Structure of Data

- The `provinces.json` file is the list of all provinces in Cambodia.
- The `provinces` directory contain all detail data of each province.

## Getting Province Detail Data

In file `provinces.json`:

```json
...
{
    "id": "banteay_meanchey",
    "code": "01",
    "local": "ខេត្តបន្ទាយមានជ័យ",
    "english": "Banteay Meanchey Province",
    "number_of_district": "2",
    "number_of_commune": "7",
    "number_of_village": "0"
}
...
```

As you can see, there is an `id` field, you can use this field to get
province detail.

Here are the URL example:

```shell script
# Get list of provinces
curl '.../main/provinces.json'

# Get detail of a province with id 'banteay_meanchey'
curl '.../main/provinces/banteay_meanchey.json
```

## Province Detail JSON Structure

```json
[
    # First level is district ស្រុក, ក្រុង, ខណ្ឌ
    {
        "type": "ស្រុក",
        ...
        # Second level are the list of communes ឃុំ, សង្កាត់
        "communes": [
            {
                "type": "ឃុំ",
                ...
                # The third level are the list of village ភូមិ
                "villages": [
                    {
                        "type": "ភូមិ",
                        ...
                    }
                ]
            }
        ]
    }
]
```

## Using GitHub to Serve JSON

You can use the GitHub raw file function to download JSON file so that you
don't have to create your own API.

Example using cURL:

```shell script
curl 'https://raw.githubusercontent.com/NorakGithub/cambodia-gazetteer/main/provinces.json'
```

## References

- [http://db.ncdd.gov.kh/gazetteer/view/index.castle](http://db.ncdd.gov.kh/gazetteer/view/index.castle)

## MIT License

Copyright (c) 2023 Khemanorak Khat

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
