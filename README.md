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
```
