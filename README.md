<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PVR - NasheDi Cinema GC</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #0f0f0f;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .container {
            text-align: center;
            background: #1a1a1a;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(255, 0, 0, 0.2);
            border: 1px solid #333;
        }

        h1 {
            color: #e50914; /* Netflix/PVR Red */
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        p {
            color: #888;
            margin-bottom: 30px;
        }

        .stars {
            display: flex;
            flex-direction: row-reverse;
            justify-content: center;
        }

        .stars input {
            display: none;
        }

        .stars label {
            font-size: 50px;
            color: #444;
            cursor: pointer;
            transition: color 0.2s ease;
            padding: 0 5px;
        }

        /* Hover aur Checked effects */
        .stars label:hover,
        .stars label:hover ~ label,
        .stars input:checked ~ label {
            color: #ffcc00; /* Gold color */
            text-shadow: 0 0 15px rgba(255, 204, 0, 0.5);
        }

        #status {
            margin-top: 20px;
            font-weight: bold;
            font-size: 1.2rem;
            height: 25px;
        }

        .btn-reset {
            margin-top: 20px;
            background: transparent;
            border: 1px solid #444;
            color: #888;
            padding: 5px 15px;
            cursor: pointer;
            border-radius: 5px;
        }

        .btn-reset:hover {
            color: white;
            border-color: white;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>PVR</h1>
        <h2 style="color: #fff; margin-top: -10px;">NasheDi Cinema GC</h2>
        <p>Rate your experience tonight:</p>

        <div class="stars">
            <input type="radio" id="star5" name="rating" value="5"><label for="star5">★</label>
            <input type="radio" id="star4" name="rating" value="4"><label for="star4">★</label>
            <input type="radio" id="star3" name="rating" value="3"><label for="star3">★</label>
            <input type="radio" id="star2" name="rating" value="2"><label for="star2">★</label>
            <input type="radio" id="star1" name="rating" value="1"><label for="star1">★</label>
        </div>

        <div id="status"></div>

        <button class="btn-reset" onclick="resetRating()">Clear Rating</button>
    </div>

    <script>
        const stars = document.querySelectorAll('input[name="rating"]');
        const status = document.getElementById('status');

        stars.forEach(star => {
            star.addEventListener('change', () => {
                let val = star.value;
                if(val == 5) status.textContent = "Full Nashe! ⭐⭐⭐⭐⭐";
                else if(val == 4) status.textContent = "Badiya Tha! ⭐⭐⭐⭐";
                else if(val == 3) status.textContent = "Theek-Thak! ⭐⭐⭐";
                else if(val == 2) status.textContent = "Mazaa nahi aaya! ⭐⭐";
                else status.textContent = "Bilkul bakwas! ⭐";
                
                status.style.color = "#ffcc00";
            });
        });

        function resetRating() {
            stars.forEach(s => s.checked = false);
            status.textContent = "";
        }
    </script>

</body>
</html>
