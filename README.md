table > tbody > tr:nth-child(2) > td:nth-child(2)
System.out.println("Is the text visible? " + page.locator("text=Your Specific String").isVisible());

page.locator("button").waitFor(new Locator.WaitForOptions().setState(WaitForSelectorState.VISIBLE)).click();

