wikiquotes-api
==============

Javascript module for retrieving quotes from wikiquote.org via api calls. [See it in action!](http://natetyler.github.io)

#### queryTitles(titles, success, error)
Query based on "titles" parameter and return page id. If multiple page ids are returned, choose the first one. Query includes "redirects" option to automatically traverse redirects. All words will be capitalized as this generally yields more consistent results.

#### getSectionsForPage(pageId, success, error)
Get the sections for a given page. This makes parsing for quotes more manageable. Returns an array of all "1.x" sections as these usually contain the quotes. If no 1.x sections exists, returns section 1. Returns the titles that were used in case there is a redirect.

#### getQuotesForSection(pageId, sectionIndex, success, error)
Get all quotes for a given section.  Most sections will be of the format:
    `<h3> title </h3>
    <ul>
      <li> 
        Quote text
        <ul>
          <li> additional info on the quote </li>
        </ul>
      </li>
    <ul>
    <ul> next quote etc... </ul>`

The quote may or may not contain sections inside `<b />` tags.

For quotes with bold sections, only the bold part is returned for brevity (usually the bold part is more well known). Otherwise the entire text is returned. Returns the titles that were used in case there is a redirect.

#### getRandomQuote(titles, success, error)
Get a random quote for the given title search. This function searches for a page id for the given title, chooses a random section from the list of sections for the page, and then chooses a random quote from that section. Returns the titles that were used in case there is a redirect.

#### openSearch(titles, success, error)
Search using opensearch api.  Returns an array of search results.

#### capitalizeString(string)
Capitalize the first letter of each word. This is included as a utility function for `queryTitles` as capitalized words yield more consistent search results.
