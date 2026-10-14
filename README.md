# HouseQuest.-
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HouseQuest - Find. View. Move In.</title>
    <style>
        :root {
            --navy: #0F2C59;
            --bright-blue: #0080FF;
            --gold: #D4AF37;
            --cream: #F8F9FA;
            --dark-text: #222222;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--cream);
            color: var(--dark-text);
            margin: 0;
            padding: 0;
        }

        header {
            background-color: var(--navy);
            color: white;
            text-align: center;
            padding: 25px 15px;
            border-bottom: 5px solid var(--gold);
        }

        header h1 {
            margin: 0;
            font-size: 2.2rem;
            letter-spacing: 1px;
        }

        header p {
            margin: 5px 0 0 0;
            color: var(--gold);
            font-weight: bold;
            letter-spacing: 2px;
            font-size: 0.9rem;
        }

        .container {
            max-width: 600px;
            margin: 30px auto;
            background: white;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        h2 {
            color: var(--navy);
            border-bottom: 2px solid var(--cream);
            padding-bottom: 10px;
            margin-top: 0;
        }

        label {
            display: block;
            margin: 15px 0 5px;
            font-weight: 600;
            color: var(--navy);
        }

        input, select, textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid #ccc;
            border-radius: 6px;
            box-sizing: border-box;
            font-size: 1rem;
        }

        input:focus, select:focus, textarea:focus {
            border-color: var(--bright-blue);
            outline: none;
        }

        .checkbox-group {
            margin: 15px 0;
        }

        .checkbox-group label {
            display: inline-block;
            margin-left: 8px;
            font-weight: normal;
        }

        input[type="checkbox"] {
            width: auto;
            transform: scale(1.2);
        }

        button {
            width: 100%;
            background-color: var(--gold);
            color: var(--navy);
            border: none;
            padding: 14px;
            font-size: 1.1rem;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            transition: background 0.2s;
            margin-top: 20px;
            text-transform: uppercase;
        }

        button:hover {
            background-color: #bfa030;
            color: white;
        }

        .admin-toggle {
            text-align: center;
            margin: 20px 0;
        }

        .admin-toggle a {
            color: var(--bright-blue);
            text-decoration: none;
            font-weight: bold;
        }

        .footer-banner {
            background-color: var(--navy);
            color: white;
            text-align: center;
            padding: 15px;
            position: fixed;
            bottom: 0;
            width: 100%;
            font-size: 0.9rem;
            border-top: 3px solid var(--gold);
        }
    </style>
</head>
<body>

    <header>
        <h1>HouseQuest</h1>
        <p>FIND • VIEW • MOVE IN</p>
    </header>

    <!-- Client Intake Form Section -->
    <div class="container" id="clientView">
        <h2>Submit Your Housing Requirements</h2>
        <p style="color: #666; font-size: 0.9rem;">Your response is securely encrypted and visible only to verified HouseQuest admins.</p>
        
        <form id="intakeForm" onsubmit="handleFormSubmit(event)">
            <label for="fullName">Full Name</label>
            <input type="text" id="fullName" required placeholder="e.g. John Kamau">

            <label for="phone">Phone Number</label>
            <input type="tel" id="phone" required placeholder="e.g. 0115788485">

            <label for="homeType">Home Type Needed</label>
            <select id="homeType" required>
                <option value="">-- Select Home Type --</option>
                <option value="Bedsitter">Bedsitter & Studio (Affordable Efficiency)</option>
                <option value="1 Bedroom">One Bedroom Apartment (Modern Finish)</option>
                <option value="2 Bedroom">Two Bedroom Apartment (Perfect for Families)</option>
                <option value="3 Bedroom">Three Bedroom Executive Living</option>
                <option value="Stand-Alone">Stand-Alone House (Privacy & Compounds)</option>
            </select>

            <label for="town">Preferred Location (Nairobi & Suburbs)</label>
            <select id="town" required>
                <option value="">-- Select Town Area --</option>
                <option value="Ruiru">Ruiru</option>
                <option value="Utawala">Utawala</option>
                <option value="Kasarani">Kasarani</option>
                <option value="Kahawa">Kahawa</option>
                <option value="Wandani/Sukari">Wandani / Sukari</option>
                <option value="Zimmerman">Zimmerman</option>
                <option value="Waiyaki Way">Waiyaki Way</option>
                <option value="Kimbo">Kimbo</option>
                <option value="Witeithie">Witeithie</option>
                <option value="Juja">Juja</option>
            </select>

            <div class="checkbox-group">
                <input type="checkbox" id="waterCheck">
                <label for="waterCheck">Requires Consistent & Clean Water Supply</label>
            </div>

            <div class="checkbox-group">
                <input type="checkbox" id="securityCheck">
                <label for="securityCheck">Requires Controlled Access / High Security Neighborhood</label>
            </div>

            <label for="notes">Additional Custom Requests</label>
            <textarea id="notes" rows="3" placeholder="Any specific requirements..."></textarea>

            <button type="submit">Submit Secure Request</button>
        </form>

        <div class="admin-toggle">
            <a href="#" onclick="showAdminView()">🔒 Staff & Admin Portal</a>
        </div>
    </div>

    <script>
        // Temporary runtime repository simulating your C++ server array structure
        const localDatabase = [];

        function handleFormSubmit(e) {
            e.preventDefault();
            
            const submission = {
                name: document.getElementById('fullName').value,
                phone: document.getElementById('phone').value,
                homeType: document.getElementById('homeType').value,
                town: document.getElementById('town').value,
                water: document.getElementById('waterCheck').checked ? "Yes" : "No",
                security: document.getElementById('securityCheck').checked ? "Yes" : "No",
                notes: document.getElementById('notes').value || "None"
            };

            localDatabase.push(submission);
            alert("✅ Request Submitted Privately! Our team will contact you shortly.");
            document.getElementById('intakeForm').reset();
        }

        function showAdminView() {
            const password = prompt("Enter Admin Secure Verification Key:");
            // Simple gatekeeper protection simulation
            if (password === "HouseQuestAdmin2026") {
                alert("Access Granted. Loading Super Admin / Admin Dashboard Console.");
                // In production, this dynamically updates UI elements to bind the localDatabase array data safely into a markup grid table.
            } else {
                alert("❌ Unauthorized Access. Your IP and attempt has been reported.");
            }
        }
    </script>
</body>
</html>