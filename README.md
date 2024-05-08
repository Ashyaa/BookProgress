# BookProgress
A Small Python script to track book progress as a "To Do" task in Habitica.

## How it works
This script uses the [Habitica V3 API](https://habitica.com/apidoc/) to automate the book progress tracking in [Habitica](https://habitica.com/).

The script itself expects a single integer representing the page number of the last read page.

If it does not exist already, it creates a new "To Do" task with a check list representing the progress in the percentiles. It then updates the task with a description in the form `Pages read / total number of pages **(percentile)**`.

When the progress reaches `100%`, the task is marked as completed automatically.

## How to use

Ensure that you have `pyyaml` and `docopt` available:

```bash
pip install --user docopt icecream pyyaml requests
```

Then run the script:

```bash
./book_progress <current_page>
```

## Configuration
The script relies on a YAML configuration file named `config.yml` that should exist alongside the script. A template file is provided in the repository: `config_base.yml`.

The YAML fields are self-explanatory, except the `author_id`: this field is the internal ID used in the Habitica API to identify users. It is used in this script only to create the the [X-Client header](https://habitica.fandom.com/wiki/Guidance_for_Comrades#X-Client_Header) required in HTTP request headers.

If you ever clone this repository, please replace the `author_id` in the configuration file by yours.