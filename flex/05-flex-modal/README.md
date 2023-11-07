# A common 'modal' style
This one is another very common pattern on the web. The solution to this one is _simple_... but it might not be immediately obvious to you. You'll need to edit the HTML a bit to get everything where it needs to be.

### A hint
Depending on how you approach this one, you might need to revisit the `flex-shrink` property to keep a flex item from getting smashed.

## Desired outcome

![desired outcome](./desired-outcome.png)

### Self Check

- The blue icon is aligned to the left.
- There is equal space on either side of the icon (the gaps between the icon and the edge of the card, and the icon and the text, are the same).
- There is padding around the edge of the modal.
- The header, text, and buttons are aligned with each other.
- The header is bold and a slightly larger text-size than the text.
- The close button is vertically aligned with the header, and aligned in the top-right of the card.




Below is first attempt, long method. All looked fine at the end but the problem was with the right x and center text being in two separate flexboxes, text couldn't overflow under x
/*<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Modal</title>
  </head>
  <body>
    <div class="modal">
      <div class="icon">!</div>
      <div class="header">Are you sure you want to do that?</div>
      <div class="close-button">✖</div>
      <div class="text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Pariatur excepturi id soluta, numquam minima rerum doloremque eveniet aspernatur beatae commodi. Cupiditate recusandae ad repellendus quidem consectetur sequi amet aspernatur cumque!</div>
      <button class="continue">Continue</button>
      <button class="cancel">Cancel</button>
    </div>
  </body>
</html>

@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

html, body {
  height: 100%;
}

body {
  font-family: Roboto, sans-serif;
  margin: 0;
  background: #aaa;
  color: #333;
  /* I'll give you this one for free lol */
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  background: white;
  width: 480px;
  border-radius: 10px;
  box-shadow: 2px 4px 16px rgba(0,0,0,.2);
  padding: 15px;
  display: flex;
  gap: 10px;
}

.icon {
  color: royalblue;
  font-size: 26px;
  font-weight: 700;
  background: lavender;
  width: 42px;
  height: 42px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.close-button {
  background: #eee;
  border-radius: 50%;
  color: #888;
  font-weight: 400;
  font-size: 16px;
  height: 24px;
  width: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
}

button {
  padding: 8px 16px;
  border-radius: 8px;
}

button.continue {
  background: royalblue;
  border: 1px solid royalblue;
  color: white;
}

button.cancel {
  background: white;
  border: 1px solid #ddd;
  color: royalblue;
}

.header {
  font-weight: bold;
  font-size: 18px;
}

.information {
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding-top: 2px;
  margin: 3px;
}

Below is the second attempt, this time the visual was very good, almost identical I would say but it was very fiddly with lots of selectors with few declarations. Did not take into consideration hint here

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>Modal</title>
  </head>
  <body>
    <div class="modal">
      <div class="container">
        <div class="icon">!</div>
      </div>
      <div class="container info">
        <div class="top">
          <div class="header">Are you sure you want to do that?</div>
         <div class="close-button">✖</div>
        </div>
        <div class="text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Pariatur excepturi id soluta, numquam minima rerum doloremque eveniet aspernatur beatae commodi. Cupiditate recusandae ad repellendus quidem consectetur sequi amet aspernatur cumque!</div>
        <div class="bottom">
          <button class="continue">Continue</button>
          <button class="cancel">Cancel</button>
        </div>
      </div>
    </div>
  </body>
</html>

@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

html, body {
  height: 100%;
}

body {
  font-family: Roboto, sans-serif;
  margin: 0;
  background: #aaa;
  color: #333;
  /* I'll give you this one for free lol */
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  background: white;
  width: 480px;
  border-radius: 10px;
  box-shadow: 2px 4px 16px rgba(0,0,0,.2);
  display: flex;
  padding: 15px;
  gap: 15px;
}

.container {
  display: flex;
  flex-direction: column;
}

.top {
  display: flex;
}

.icon {
  color: royalblue;
  font-size: 26px;
  font-weight: 700;
  background: lavender;
  width: 42px;
  height: 42px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.close-button {
  background: #eee;
  border-radius: 50%;
  color: #888;
  font-weight: 400;
  font-size: 16px;
  height: 24px;
  width: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
}

button {
  padding: 8px 16px;
  border-radius: 8px;
}

button.continue {
  background: royalblue;
  border: 1px solid royalblue;
  color: white;
}

button.cancel {
  background: white;
  border: 1px solid #ddd;
  color: royalblue;
}

.header {
  flex: auto;
  font-weight: bold;
  font-size: 18px;
  padding-top: 2px;
}

.info {
  gap: 12px;
}

.text {
  padding-bottom: 5px;
}