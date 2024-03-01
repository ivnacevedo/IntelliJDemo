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

```
