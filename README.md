```
FrameLocator frame = page.frameLocator("#test");
Locator rows = frame.getByRole("table").last().locator("role=row");

int rowCount = rows.count();
for (int i = 0; i < rowCount; i++) {
    Locator cells = rows.nth(i).locator("role=cell");
    int cellCount = cells.count();
    for (int j = 0; j < cellCount; j++) {
        String cellText = cells.nth(j).textContent();
        System.out.println(cellText);
    }
    System.out.println("----- End of Row " + (i + 1) + " -----");
}


// Assuming you have a Playwright Page object
Locator rows = page.locator("role=row");
for (int i = 0; i < rows.count(); i++) {
    Locator cells = rows.nth(i).locator("role=cell");
    for (int j = 0; j < cells.count(); j++) {
        String cellText = cells.nth(j).textContent();
        System.out.println(cellText);
    }
}


String[] tableHeaders = page.locator("yourTableSelector > thead > tr:first-child > th").allInnerTexts();

            // Print out the table headers
            System.out.println("Table Headers:");
            for (String header : tableHeaders) {
                System.out.println(header);
            }



// Example: Extract href attributes from all links on the page
List<String> links = page.querySelectorAll("a").stream()
                    .map(link -> link.getAttribute("href"))
                    .toList();

            List<String> extractedData = new ArrayList<>();
            for (String link : links) {
                page.navigate(link);
                // Extract data from the page. Modify the selector as per your needs.
                String data = page.textContent("selector-for-your-data"); // Change the selector accordingly
                extractedData.add(data);
            }

            // Process the extracted data
            extractedData.forEach(System.out::println);

```
