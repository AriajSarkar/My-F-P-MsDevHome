<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<title>Light And Dark Mode Toggle </title>
    <script src="https://code.iconify.design/1/1.0.4/iconify.min.js"></script>
    <link rel="stylesheet" type="text/css" href="style.css">
    <style>
        body{
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: var(--background-color);
    color: var(--text-color-normal);
        }
        :root {
            --text-color-normal: black;
            --text-color-inverse: white;
            --background-color: white;
        }

        [data-theme="dark"] {
            --text-color-normal: white;
            --text-color-inverse: black;
            --background-color: black;
        }
        .toggle-checkbox{
            position: absolute;
            opacity: 0;
            cursor: pointer;
            height: 0;
            width: 0;
        }
        .toggle-slot{
            position: relative;
            height: 10em;
            width: 20em;
            border-radius: 10em;
            background-color: #5d4618;
            box-shadow: 0px 10px 25px #615f5f;
            transition: background-color 250ms;
        }
        .toggle-checkbox:checked ~ .toggle-slot{
            background-color: #000000;
        }
        .toggle-button{
            transform: translate(11.75em,1.75em);
            position: absolute;
            height: 6.5em;
            width: 6.5em;
            border-radius: 50%;
            background-color: #ffbb52;
            box-shadow: inset 0px 0px 0px 0.75em #b38e57;
            transition: background-color 250ms,border-color 250ms,transform 1500ms cubic-bezier(.26,2,.46,.71);
        }
        .toggle-checkbox:checked ~ .toggle-slot .toggle-button{
        background-color: #958f8f;
        box-shadow: inset 0px 0px 0px 0.75em rgb(86, 81, 81);
        transform: translate(1.75em,1.75em);

        }
        .sun-icon{
            position: absolute;
            height: 6em;
            width: 6em;
            color: #ffbb52;
        }
        .sun-icon-wrapper{
            position: absolute;
            height: 6em;
            width: 6em;
            opacity: 1;
            transform: translate(2em ,2em) rotate(15deg);
            transform-origin: 50% 50%;
            transition: opacity 150ms,transform 1500ms cubic-bezier(.26,2,.46,.71)
        }
        .toggle-checkbox:checked ~ .toggle-slot .sun-icon-wrapper{
        opacity: 0;
        transform: translate(3em,2em) rotate(0deg);
        }
        .moon-icon{
            position: absolute;
            height: 6em;
            width: 6em;
            color: white;
        }
        .moon-icon-wrapper{
            position: absolute;
            height: 6em;
            width: 6em;
            opacity: 0;
            transform: translate(11em ,2em) rotate(0deg);
            transform-origin: 50% 50%;
            transition: opacity 150ms,transform 1500ms cubic-bezier(.26,2,.46,.71)
        }
        .toggle-checkbox:checked ~ .toggle-slot .moon-icon-wrapper{
        opacity: 1;
        transform: translate(12em,2em) rotate(-15deg);
        }
    </style>
</head>
<body>
<label>
	<input type="checkbox" name="checkbox" class="toggle-checkbox" />
	<div class="toggle-slot">
		<div class="sun-icon-wrapper">
			<div class="iconify sun-icon" data-icon="feather-sun" data-inline="false"> </div>
		</div>
		<div class="toggle-button"></div>
			<div class="moon-icon-wrapper">
			<div class="iconify moon-icon" data-icon="feather-moon" data-inline="false"> </div>
			</div>
	</div>
</label>
<script>
    // Get the checkbox
let checkbox = document.querySelector('.toggle-checkbox');
// Listen for changes
checkbox.addEventListener('change', function() {
    // Check if the checkbox is checked
    // If it is, set theme to dark
    // If not, set theme to light
    if(this.checked) {
        document.documentElement.setAttribute('data-theme', 'dark');
    } else {
        document.documentElement.setAttribute('data-theme', 'light');
    }
});
</script>
</body>
</html>
