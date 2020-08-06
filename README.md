## Form validation with JQuery and JQuery Validate Plugin.

#### Step: 1
Add these two script at top of your HTML file.

JQuery CDN link
- `<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>`

JQuery Validate CDN link
- `<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-validate/1.19.1/jquery.validate.min.js"></script>`

#### Step: 2

- Create a form in your HTML file. Give your form an id, jquery will capture your form with that id.
- Every input field should have a `name` attribute. Like `<input type="email" name="email>`
- Input fields will be captured by their name.
- Finally create an input with type submit. Like `<input type="submit" value="Submit Form">`

### Step: 3

- Now we will write the function in JS file or in HTML with script tag (at bottom) that will catch validation errors.

```js
$(function() {
  $("#loginForm").validate({
    rules: {
      email: {
        required: true,
        email: true,
      },
      password: {
        required: true,
        minlength: 5,
      }
    },

    messages: {
      email: {
        required: "Please enter a valid email address.",
      },
      password: {
        required: "Please provide a password.",
        minlength: "Password is too short. Minimum length is 5."
      }
    },

    submitHandler: function(form) {
      form.submit();
    }
  })
})
```

- JQuery captures our form with it's id, `${"#loginForm"}`. Replace this with your form id.
- Validate function takes an object as argument. That object has 3 keys.
- First is rules, here you define your validation rules. Like which input fields should pe present (with required) and what should be their length (with minlength and maxlength). Here input is captured by their names.
- Next key is `messages` here you have to define your custom error message. The message which will appear when validation will fail.
- Third and last key is `submitHandler` whose value is a function which detects when the form is submitted and shows error message if any.
- That's it. Your form validation is ready.

### Step: 4

- If you want to (OffCourse you want) to style your error messages. Then in CSS file just write your css style form `error` class.
- JQuery creates new element to show error message with class name `error`.

```css
form .error {
  color: red;
}
```

###### And that's how you validate your form with JQuery.
