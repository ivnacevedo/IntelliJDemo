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
// Use Collectors.toList() for compatibility with Java 8 and later
            List<String> links = page.querySelectorAll("a").stream()
                    .map(link -> link.getAttribute("href"))
                    .collect(Collectors.toList());

            for (String link : links) {
                page.navigate(link);
                // Extract data from the page. Modify the selector as per your needs.
                String data = page.textContent("selector-for-your-data"); // Change the selector accordingly
                System.out.println(data);
            }




// Perform assertions
safeAssert(() -> assertThat(page.locator("selector-for-the-element")).hasText("Expected text"));
safeAssert(() -> assertThat(page.locator("another-selector")).isVisible());


    // Utility method for safe assertions
    private static void safeAssert(Runnable assertion) {
        try {
            assertion.run();
        } catch (AssertionError e) {
            System.out.println("Assertion failed: " + e.getMessage());
            // Optionally log the error or perform other actions
        }
    }
}


# Load the required assembly
[System.Reflection.Assembly]::LoadWithPartialName("System.Net.Mail") | Out-Null

# Set the email parameters
$smtpServer = "smtp.example.com"
$smtpPort = 587 # Adjust as needed
$smtpUser = "username@example.com"
$smtpPassword = "your_password"

$from = "sender@example.com"
$to = "recipient@example.com"
$subject = "Email Subject"
$body = "This is the email body."
$attachment = "C:\Path\To\File.pdf"

# Create a new email message
$message = New-Object System.Net.Mail.MailMessage
$message.From = $from
$message.To.Add($to)
$message.Subject = $subject
$message.Body = $body

# Add an attachment
$attachment = New-Object System.Net.Mail.Attachment($attachment)
$message.Attachments.Add($attachment)

# Create an SMTP client
$smtp = New-Object System.Net.Mail.SmtpClient($smtpServer, $smtpPort)
$smtp.Credentials = New-Object System.Net.NetworkCredential($smtpUser, $smtpPassword)
$smtp.EnableSsl = $true # Adjust as needed

# Send the email
try {
    $smtp.Send($message)
    Write-Output "Email sent successfully."
}
catch {
    Write-Error "Failed to send email: $($_.Exception.Message)"
}

```
