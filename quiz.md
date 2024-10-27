for test we hadd this html file:
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form with Bootstrap and jQuery</title>
    <!-- Bootstrap CSS -->
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
    <!-- jQuery library -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
    <!-- Bootstrap JS -->
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
</head>
<body>

<div class="container mt-5">
    <h2>Custom Form</h2>
    <form id="customForm">
        <!-- Fields 1-8 -->
        <input type="email" id="email" class="form-control mb-2" placeholder="Email" required>
        <input type="password" class="form-control mb-2" id="password" placeholder="Password" required>

        <label for="gender">Gender</label>
        <select id="gender" data="test" class="form-control mb-2">
            <option>Select</option>
            <option>Male</option>
            <option>Female</option>
            <option>Other</option>
        </select>

        <!-- Field 9 -->
        
        <label for="dog-breeds">Which is the best dog breed?</label>
        <div class="list-group mb-2" for="dog-breeds">
            <a href="#" class="list-group-item list-group-item-action">Labrador Retriever</a>
            <a href="#" class="list-group-item list-group-item-action">German Shepherd</a>
            <a href="#" class="list-group-item list-group-item-action">Corgi</a>
            <a href="#" class="list-group-item list-group-item-action">Dalmatian</a>
            <a href="#" class="list-group-item list-group-item-action">Daschund</a>
            <!-- Add more dog breeds as needed -->
        </div>

        <label for="question">ვინ მოერევა ?</label>
        <div class="list-group mb-2" for="question">
            <a href="#" class="list-group-item list-group-item-action">კრატოსი</a>
            <a href="#" class="list-group-item list-group-item-action">ვან პანჩ მენი</a>
            <a href="#" class="list-group-item list-group-item-action">გივი სიხარულიძე</a>
            <a href="#" class="list-group-item list-group-item-action">ხვიჩა კვარაცხელია</a>
            <a href="#" class="list-group-item list-group-item-action">სარუმანი</a>
            <!-- Add more dog breeds as needed -->
        </div>

        <label for="question3">დავითვალოთ 12-მდე</label>
        <div class="list-group mb-2" for="question3">
            <a href="#" class="list-group-item list-group-item-action">1</a>
            <a href="#" class="list-group-item list-group-item-action">2</a>
            <a href="#" class="list-group-item list-group-item-action">3</a>
            <a href="#" class="list-group-item list-group-item-action">4</a>
            <a href="#" class="list-group-item list-group-item-action">5</a>
            <a href="#" class="list-group-item list-group-item-action">6</a>
            <a href="#" class="list-group-item list-group-item-action">7</a>
            <a href="#" class="list-group-item list-group-item-action">8</a>
            <a href="#" class="list-group-item list-group-item-action">9</a>
            <a href="#" class="list-group-item list-group-item-action">10</a>
            <a href="#" class="list-group-item list-group-item-action">11</a>
            <a href="#" class="list-group-item list-group-item-action">12</a>
            <!-- Add more dog breeds as needed -->
        </div>


        <label for="question2">რატომ არის ეს ინპუტი მეოთხედ?</label>
        <div class="list-group mb-2" for="question2">
            <a href="#" class="list-group-item list-group-item-action">მჭირდებოდა</a>
            <a href="#" class="list-group-item list-group-item-action">მეტი ინპუტი</a>
            <a href="#" class="list-group-item list-group-item-action">ვერტიკალური სქროლი რომ გამოჩენილიყო</a>
            <a href="#" class="list-group-item list-group-item-action">ხო სხვა ვერ მოვიფიქრე</a>
            <a href="#" class="list-group-item list-group-item-action">ვერაფერი</a>
            <!-- Add more dog breeds as needed -->
        </div>

        <div class="mb-4">
            <label>Drag the box and drop it into the other box:</label>
            <div class="d-flex justify-content-around">
                <div id="dragBox" class="box" draggable="true">Drag me</div>
                <div id="dropBox" class="box">Here</div>
            </div>
        </div>
        

        <!-- Field 11 -->
        <div class="form-check mb-2">
            <input type="checkbox" class="form-check-input" id="terms">
            <label class="form-check-label" for="terms">Is this the best quiz you've ever written?</label>
        </div>
        <div id="successMessage" style="display:none;">Thank you for your feedback!</div>

        <!-- Submit Button -->
        <button type="submit" class="btn btn-primary">Submit</button>
    </form>
</div>

<script>
    $(document).ready(function(){

        const dragBox = document.getElementById('dragBox');
        const dropBox = document.getElementById('dropBox');



        dragBox.addEventListener('dragstart', function(e) {
            e.dataTransfer.setData('text/plain', e.target.id);
        });

        dropBox.addEventListener('dragover', function(e) {
            e.preventDefault();
        });

        dropBox.addEventListener('drop', function(e) {
            e.preventDefault();
            const draggedElementId = e.dataTransfer.getData('text');
            if (draggedElementId === 'dragBox') {
                dropBox.textContent = 'Dropped!';
                dropBox.classList.add('dropped');
                dragBox.style.visibility = 'hidden';
            }
        });


        // Update score value
        $("#score").on("input", function() {
            $("#scoreValue").text($(this).val());
        });

        // Highlight dog breed on click
        $(".list-group-item").click(function(e) {
            e.preventDefault();
            $(this).toggleClass('active');
        });

        // Display success message after 3 seconds when checkbox is checked
        $("#terms").change(function() {
            if($(this).prop("checked")) {
                setTimeout(function() {
                    $("#successMessage").slideDown();
                }, 3000);
            } else {
                $("#successMessage").slideUp();
            }
        });

        // Redirect on form submission
        $("#customForm").submit(function(event){
            event.preventDefault();
            window.location.href = "https://www.youtube.com/watch?v=dQw4w9WgXcQ&ab_channel=RickAstley";
        });

        let isDragging = false;
        let sliderWidth = $(".slider-container").width();
        let handleWidth = $(".slider-handle").width();
        let maxValue = 5;
        let tickInterval = 1;

        // Generate ticks
        for (let i = 0; i <= maxValue; i += tickInterval) {
            let leftPosition = (i / maxValue) * (sliderWidth - handleWidth);
            let tick = $("<span>").css("left", leftPosition + "px");
            $(".slider-ticks").append(tick);
        }

        $(".slider-handle").mousedown(function(e) {
            isDragging = true;
        });

        $(document).mouseup(function() {
            isDragging = false;
        });

        $(document).mousemove(function(e) {
            if (isDragging) {
                let mouseX = e.pageX - $(".slider-container").offset().left;
                let newLeft = mouseX - (handleWidth / 2);

                if (newLeft < 0) {
                    newLeft = 0;
                } else if (newLeft > sliderWidth - handleWidth) {
                    newLeft = sliderWidth - handleWidth;
                }

                $(".slider-handle").css("left", newLeft + "px");

                // Update value
                let value = Math.round((newLeft / (sliderWidth - handleWidth)) * maxValue);
                $(".slider-value").text(value);
            }
        });


    });
</script>

<style>
    .box {
        width: 100px;
        height: 100px;
        border: 2px solid #333;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: move;
    }
    #dragBox {
        background-color: #f0f0f0;
    }
    #dropBox {
        background-color: #e0e0e0;
    }
    .dropped {
        background-color: #90EE90 !important;
    }



    .slider-container {
    position: relative;
    width: 300px;
    height: 20px;
    background-color: #e0e0e0;
}

.slider-track {
    position: absolute;
    width: 100%;
    height: 5px;
    top: 50%;
    transform: translateY(-50%);
    background-color: #a0a0a0;
}

.slider-handle {
    position: absolute;
    width: 20px;
    height: 20px;
    top: 50%;
    transform: translateY(-50%);
    background-color: #333;
    cursor: pointer;
}

.slider-ticks span {
    position: absolute;
    width: 1px;
    height: 10px;
    background-color: #666;
    top: 50%;
    transform: translateY(-50%);
}

.slider-value {
    display: inline-block;
    margin-left: 320px;
    text-align: center;
    font-weight: bold;
}

</style>

</body>
</html>

this was my test code:
import { test as baseTest } from '@playwright/test';

baseTest('test_Ani_Kelaptrishvili', async ({ page }) => {

    await page.goto('file:///C:/CU/auto_test_Kelaptrishvili/index.html');

    // Enter email and password
    const emailInput = page.locator('//input[@id="email"]');
    const passwordInput = page.locator('#password');
    await emailInput.fill('A_kelaptrishvili@gmail.com');
    await passwordInput.fill('12345678');

    // Select Last element
    const lastFormElement = page.locator('#customForm > :nth-last-child(1)');
    await lastFormElement.hover();

    // Select Any option
    const genderDropdown = page.locator('#gender');
    await genderDropdown.selectOption({ index: 1 });

    // Using loop select every element
    const listItems = page.locator('.list-group-item');
    await listItems.first().waitFor();

    const allElements = await listItems.all();
    for (let index = 0; index < allElements.length; index++) {
        const currentItem = allElements[index];
        await currentItem.click();
        const itemText = await currentItem.innerText();
        console.log(`Clicked Item ${index + 1}: ${itemText}`);
    }

    // Select any element using text selector
    const textSelectorElement = page.locator('text=Dalmatian');
    await textSelectorElement.click();

    // Drag one box to second
    const dragSource = page.locator('#dragBox');
    const dropTarget = page.locator('#dropBox');
    await dragSource.dragTo(dropTarget);

    // Click on Checkbox
    const termsCheckbox = page.locator('#terms');
    await termsCheckbox.click();

    // Click Submit
    const submitButton = page.locator('button[type="submit"]');
    await submitButton.click();
});
