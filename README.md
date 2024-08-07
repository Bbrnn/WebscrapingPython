### Web Scraping Concept


### 1. **Requests Library**

- **Purpose**: `requests` is a popular Python library used to send HTTP requests to web servers and receive responses. It simplifies the process of making requests compared to using lower-level libraries like `urllib`.

- **Key Functions**:
  - `requests.get(url)`: Sends a GET request to the specified URL. This is often used to retrieve web pages.
  - `requests.post(url, data)`: Sends a POST request to the specified URL with optional data. Useful for forms and login submissions.
  - `response.text`: Contains the HTML content of the response as a string.
  - `response.raise_for_status()`: Raises an exception if the HTTP request returned an error status code, such as 404 or 500.

- **Example Usage**:
  ```python
  import requests

  response = requests.get('https://example.com')
  html_content = response.text
  ```

### 2. **BeautifulSoup Library**

- **Purpose**: `BeautifulSoup` is a library used for parsing HTML and XML documents. It provides Pythonic ways to navigate and search through the document tree, making it easier to extract data from complex HTML structures.

- **Key Functions**:
  - `BeautifulSoup(html_content, 'html.parser')`: Creates a BeautifulSoup object from the HTML content. `'html.parser'` is a built-in parser, but you can also use other parsers like `lxml` or `html5lib`.
  - `soup.find(tag, attributes)`: Finds the first occurrence of a tag with optional attributes.
  - `soup.find_all(tag, attributes)`: Finds all occurrences of a tag with optional attributes.
  - `element.get_text()`: Extracts and returns all text within an element.
  - `element['attribute_name']`: Retrieves the value of a specific attribute from an HTML tag.

- **Example Usage**:
  ```python
  from bs4 import BeautifulSoup

  soup = BeautifulSoup(html_content, 'html.parser')
  title = soup.title.get_text()  # Extracts the text within the <title> tag
  ```

### Putting It Together

In a typical web scraping workflow using `requests` and `BeautifulSoup`, you follow these steps:

1. **Send a Request**: Use `requests` to fetch the HTML content of the webpage.
   ```python
   import requests

   url = 'https://example.com'
   response = requests.get(url)
   html_content = response.text
   ```

2. **Parse the HTML**: Use `BeautifulSoup` to parse the HTML content and create a BeautifulSoup object.
   ```python
   from bs4 import BeautifulSoup

   soup = BeautifulSoup(html_content, 'html.parser')
   ```

3. **Extract Data**: Use BeautifulSoup’s methods to find and extract the desired data from the parsed HTML.
   ```python
   data = soup.find('tag_name', {'class': 'class_name'}).get_text()
   ```

4. **Handle Data**: Process or store the extracted data as needed.

### Example Scenario: Scraping a List of Countries

Here’s a practical example to put these concepts into action:

- **Goal**: Scrape a list of country names from a Wikipedia page.
- **Steps**:
  1. **Request the Page**: Use `requests` to get the HTML of the Wikipedia page.
  2. **Parse the HTML**: Use `BeautifulSoup` to parse the HTML and navigate the document.
  3. **Extract Data**: Locate the specific HTML table or list that contains country names and extract the data.

By understanding how to send requests and parse HTML, you can scrape a variety of web content. Always make sure to respect the website’s `robots.txt` file and terms of service when scraping.
