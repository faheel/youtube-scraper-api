# YouTube scraper API

A web API that scrapes a YouTube video's data and returns it as JSON

## Setup

1. Create a Python 3 virtual environment using [Pipenv](https://github.com/pypa/pipenv):
   ```bash
   pipenv --three
   ```
2. Activate the virtual environment and install the dependencies:
   ```bash
   pipenv shell
   pipenv install --dev
   ```

### Start the server

With the virtual environment activated, run the following from the root directory of the project:

```bash
python -m scraper.api
```

The server should then be available at http://127.0.0.1:5000.

## API

### Requests

The API accepts GET requests at the `/scrape` endpoint with the following parameters:

* #### `id`
  ID of the YouTube video whose data is to be scraped.

#### Example URLs

* `http://127.0.0.1:5000/scrape?id=YdwOL08NfxQ`
* `http://127.0.0.1:5000/scrape?id=n-DTjpde9-0`


### Responses

* #### Successful response
  When data is successfully scraped for the given video ID.

  #### Status code
  200

  #### Format
  ```python3
  {
      "id": string,
      "title": string,
      "upload_date": string,
      "duration": string,
      "description": string,
      "thumbnail_url": string,
      "genre": string,
      "is_paid": boolean,
      "is_unlisted": boolean,
      "is_family_friendly": boolean,
      "uploader": {
          "channel_id": string,
          "name": string,
          "thumbnail_url": string,
          "is_verified": boolean
      },
      "statistics": {
          "views": number,
          "likes": number,
          "dislikes": number
      }
  }
  ```

* #### Error response
  When no video corresponding to the given video ID is found.

  #### Status code
  404

  #### Format
  ```python3
  {
      "error": string
  }
  ```

## License

This project is licensed under the terms of the [MIT license](LICENSE).
