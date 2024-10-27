this was the html file for test practise:

<!DOCTYPE html>
<html>
<head>
    <title>Quiz #3</title>
    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
    <!-- jQuery UI CSS for sortable and datepicker -->
    <link rel="stylesheet" href="https://code.jquery.com/ui/1.12.1/themes/base/jquery-ui.css">
</head>
<body>
    <div class="container mt-5">
        <h2>Quiz #3</h2>
        <form id="quizForm">
            <!-- Username Field -->
            <!-- Quiz Question -->
            <div class="form-group">
                <label for="quizQuestion-1">What is the meaning of life ? </label>
                <div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="quizQuestion" id="answer1" value="option1">
                        <label class="form-check-label" for="answer1">
                            42
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="quizQuestion" id="answer2" value="option2">
                        <label class="form-check-label" for="answer2">
                            რასაც გასცემ შენია რაც არა დაკარგულია
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="quizQuestion" id="answer3" value="option3">
                        <label class="form-check-label" for="answer3">
                            შტანგენფარგალი
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="quizQuestion" id="answer4" value="option4">
                        <label class="form-check-label" for="answer4">
                            -_-
                        </label>
                    </div>
                </div>
            </div>


            <div class="form-group">
                <label for="quizQuestion-2">Be or not To Be</label>
                <div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="quizQuestion-2" id="answer1" value="option1">
                        <label class="form-check-label" for="answer11">
                            Nope
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="quizQuestion-2" id="answer2" value="option2">
                        <label class="form-check-label" for="answer22">
                            BE 
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="quizQuestion-2" id="answer3" value="option3">
                        <label class="form-check-label" for="answer33">
                             May BE
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="quizQuestion-2" id="answer4" value="option4">
                        <label class="form-check-label" for="answer44">
                           Let it be
                        </label>
                    </div>
                </div>
            </div>


            <!-- Selectable Calendar -->
            <div id="calendar-container" class="form-group">
                <label for="calendar">Date</label>
                <input type="text" class="form-control" id="calendar" placeholder="Select a date">
            </div>

            <!-- Sortable List -->
            <div class="form-group">
                <label>Sortable Items</label>
                <ul id="sortable" class="list-group">
                    <li class="list-group-item">Lord of the Rings</li>
                    <li class="list-group-item">Game of thrones</li>
                    <li class="list-group-item">Breaking Bad</li>
                    <li class="list-group-item">Harry potter</li>
                    <li class="list-group-item">Marvel</li>
                    <li class="list-group-item">thrones</li>
                    <li class="list-group-item">Bad</li>
                </ul>
            </div>

            <!-- 3x3 Selectable Grid -->
            <div class="form-group">
                <label>Selectable Grid</label>
                <div class="d-flex flex-wrap" style="max-width: 300px;">
                    <!-- Grid items -->
                    <!-- Repeat the below div 9 times (3x3) -->
                    <div data-e2e="1" class="p-2 border m-1 grid-item" style="width: 30%; height: 100px;"></div>
                    <div data-e2e="2" class="p-2 border m-1 grid-item" style="width: 30%; height: 100px;"></div>
                    <div data-e2e="3" class="p-2 border m-1 grid-item" style="width: 30%; height: 100px;"></div>
                    <div data-e2e="4" class="p-2 border m-1 grid-item" style="width: 30%; height: 100px;"></div>
                    <div data-e2e="5" class="p-2 border m-1 grid-item" style="width: 30%; height: 100px;"></div>
                    <div data-e2e="6" class="p-2 border m-1 grid-item" style="width: 30%; height: 100px;"></div>
                    <div data-e2e="7" class="p-2 border m-1 grid-item" style="width: 30%; height: 100px;"></div>
                    <div data-e2e="8" class="p-2 border m-1 grid-item" style="width: 30%; height: 100px;"></div>
                    <div data-e2e="9" class="p-2 border m-1 grid-item" style="width: 30%; height: 100px;"></div>
                </div>
            </div>

            <button type="submit" class="btn btn-primary">Submit</button>
        </form>
    </div>





    <!-- jQuery Full Version -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

    <!-- jQuery UI -->
    <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>

    <!-- Bootstrap JS -->
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js"></script>

<script>
    $(function() {
        // jQuery UI datepicker
        $("#calendar").datepicker();

        // jQuery UI sortable list
        $("#sortable").sortable();

        // Selectable grid
        $('.grid-item').click(function() {
            $(this).toggleClass('bg-primary');
        });
    });
</script>

</body>
</html>




we put it in the folder and run new console with this command: npm init playwright@latest
in the tests folder create new. for running tests use npx playwright test --ui

this is my test code:
const { test } = require('@playwright/test');

test('quiz', async ({ page }) => {
    await page.goto('C:/Users/105an/Downloads/pup/quiz_4 (1).html');
    // Question 1: Select the second option and the option with digits (42)
    await page.locator('div.form-group:first-of-type input[value="option2"]').check();
    await page.locator('div.form-group:first-of-type input[value="option1"]').check();
    await page.waitForTimeout(3000);



    // Question 2: Hover over "May" option and the last option, then select all options in sequence
    
    // Locate the option that contains text "MAY" using an XPath selector
    const containsMay = page.locator('//form[@id="quizForm"]//div[@class="form-group" and position()=2]//div//div//label[contains(text(), "May")]');
    await containsMay.hover();
    await page.waitForTimeout(1000);

    // Locate the last option using a CSS selector
    const lastOption = page.locator('form > div.form-group:nth-of-type(2) > div > div:last-child input');
    await lastOption.hover();
    await page.waitForTimeout(1000);


    for (let i = 1; i <= 4; i++) {
        await page.locator(`form > div.form-group:nth-of-type(2) > div > div:nth-child(${i}) > input`).click();
    }


      // Calendar: Select January 1, 2025
    await page.locator('#calendar-container').click();
    await page.locator('[data-handler="next"]').click({ clickCount: 3 });
    await page.locator('//a[text()="1"]').click();
    await page.waitForTimeout(1000);



    // Move "Breaking Bad" to the top using a CSS selector
    let breaking_bad = page.locator('ul#sortable li:nth-child(3)');
    let first_item = page.locator('ul#sortable li:nth-child(1)');
    await breaking_bad.dragTo(first_item);

    // Move "Lord of the Rings" to the top using an XPath selector
    let lord_of_the_rings = page.locator('//ul[@id="sortable"]//li[contains(text(), "Lord of the Rings")]');
    await lord_of_the_rings.dragTo(first_item);

    // Move "Marvel" to the end of the list using a Text selector
    let marvel = page.locator('text="Marvel"');
    let last_item = page.locator('ul#sortable li:last-child');
    await marvel.dragTo(last_item);




    // Click on the first three items in the grid
    for (let i = 1; i <= 3; i++) {
        await page.locator(`div.form-group:nth-of-type(5) > div > div:nth-child(${i})`).click();
    }

        await page.locator(`div.form-group:nth-of-type(5) > div > div:nth-child(${2})`).click();

    // Click on every odd-numbered index (5, 7, 9) to form an "X" pattern except alreay blue 1-3
    for (let i = 5; i <= 9; i += 2) {
        await page.locator(`div.form-group:nth-of-type(5) > div > div:nth-child(${i})`).click();
    }

    // Re-click all odd-numbered items (1, 3, 5, 7, 9) to toggle their states
    for (let i = 1; i <= 9; i += 2) {
        await page.locator(`div.form-group:nth-of-type(5) > div > div:nth-child(${i})`).click();
    }

    // Click all even-numbered items (2, 4, 6, 8) 
    for (let i = 2; i <= 8; i += 2) {
        await page.locator(`div.form-group:nth-of-type(5) > div > div:nth-child(${i})`).click();
    }

    // Step 5: Check every element; if it’s not blue, click it
    for (let i = 1; i <= 9; i++) {
        const cell = page.locator(`div.form-group:nth-of-type(5) > div > div:nth-child(${i})`);
        const isBlue = await cell.evaluate(node => node.classList.contains('bg-primary'));
        
        // Click the cell if it’s not blue
        if (!isBlue) {
            await cell.click();
        }
    }

    // clicking submit
    await page.locator('button[type="submit"]').click();
})
