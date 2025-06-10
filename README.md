# Quniq-Domain-genrator
“Instantly find cool and available domain names for your next project.”

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Unique Domain Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            text-align: center;
        }
        .domain-display {
            font-size: 2.5em;
            margin: 30px 0;
            color: #2c3e50;
            font-weight: bold;
            min-height: 60px;
        }
        button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 12px 24px;
            font-size: 16px;
            cursor: pointer;
            border-radius: 4px;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #2980b9;
        }
        .options {
            margin: 20px 0;
            padding: 15px;
            background-color: #f8f9fa;
            border-radius: 4px;
        }
        .copied {
            color: green;
            font-weight: bold;
            display: none;
        }
    </style>
</head>
<body>
    <h1>Unique Domain Generator</h1>
    <p>Generate creative and unique domain name ideas instantly</p>
    
    <div class="domain-display" id="domainOutput">example.xyz</div>
    
    <button onclick="generateDomain()">Generate Domain</button>
    <button onclick="copyDomain()">Copy Domain</button>
    <div class="copied" id="copiedMessage">Copied to clipboard!</div>
    
    <div class="options">
        <h3>Generation Options</h3>
        <label>
            <input type="checkbox" id="usePrefix" checked> Use Prefix
        </label>
        <label>
            <input type="checkbox" id="useSuffix" checked> Use Suffix
        </label>
        <label>
            <input type="checkbox" id="useNumbers" checked> Include Numbers
        </label>
    </div>
    
    <script>
        // Word lists for domain generation
        const prefixes = ['super', 'mega', 'hyper', 'ultra', 'quantum', 'neo', 'alpha', 'omega', 'prime', 'zen', 'nova', 'vortex', 'cosmic', 'digital', 'virtual'];
        const words = ['tech', 'web', 'cloud', 'app', 'code', 'data', 'net', 'host', 'dev', 'ai', 'io', 'hub', 'lab', 'grid', 'flux', 'sphere', 'node', 'link', 'bit', 'byte'];
        const suffixes = ['ify', 'ly', 'er', 'ster', 'ify', 'io', 'ex', 'ix', 'ax', 'or', 'ar', 'ary', 'ify', 'ly'];
        const tlds = ['.com', '.io', '.ai', '.tech', '.dev', '.net', '.xyz', '.app', '.cloud', '.online', '.site', '.space'];
        
        function getRandomElement(array) {
            return array[Math.floor(Math.random() * array.length)];
        }
        
        function generateDomain() {
            const usePrefix = document.getElementById('usePrefix').checked;
            const useSuffix = document.getElementById('useSuffix').checked;
            const useNumbers = document.getElementById('useNumbers').checked;
            
            let domainParts = [];
            
            // Add prefix if enabled
            if (usePrefix) {
                domainParts.push(getRandomElement(prefixes));
            }
            
            // Add main word
            domainParts.push(getRandomElement(words));
            
            // Add suffix if enabled
            if (useSuffix) {
                domainParts.push(getRandomElement(suffixes));
            }
            
            // Add number if enabled (50% chance)
            if (useNumbers && Math.random() > 0.5) {
                domainParts.push(Math.floor(Math.random() * 100).toString());
            }
            
            // Combine parts and add TLD
            const domain = domainParts.join('') + getRandomElement(tlds);
            
            document.getElementById('domainOutput').textContent = domain;
            document.getElementById('copiedMessage').style.display = 'none';
        }
        
        function copyDomain() {
            const domain = document.getElementById('domainOutput').textContent;
            navigator.clipboard.writeText(domain).then(() => {
                const message = document.getElementById('copiedMessage');
                message.style.display = 'block';
                setTimeout(() => {
                    message.style.display = 'none';
                }, 2000);
            });
        }
        
        // Generate first domain on page load
        window.onload = generateDomain;
    </script>
</body>
</html>

