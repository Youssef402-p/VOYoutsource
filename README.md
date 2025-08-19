**[voy.html](https://github.com/user-attachments/files/21848292/voy.html)
<script type="text/javascript">
        var gk_isXlsx = false;
        var gk_xlsxFileLookup = {};
        var gk_fileData = {};
        function filledCell(cell) {
          return cell !== '' && cell != null;
        }
        function loadFileData(filename) {
        if (gk_isXlsx && gk_xlsxFileLookup[filename]) {
            try {
                var workbook = XLSX.read(gk_fileData[filename], { type: 'base64' });
                var firstSheetName = workbook.SheetNames[0];
                var worksheet = workbook.Sheets[firstSheetName];

                // Convert sheet to JSON to filter blank rows
                var jsonData = XLSX.utils.sheet_to_json(worksheet, { header: 1, blankrows: false, defval: '' });
                // Filter out blank rows (rows where all cells are empty, null, or undefined)
                var filteredData = jsonData.filter(row => row.some(filledCell));

                // Heuristic to find the header row by ignoring rows with fewer filled cells than the next row
                var headerRowIndex = filteredData.findIndex((row, index) =>
                  row.filter(filledCell).length >= filteredData[index + 1]?.filter(filledCell).length
                );
                // Fallback
                if (headerRowIndex === -1 || headerRowIndex > 25) {
                  headerRowIndex = 0;
                }

                // Convert filtered JSON back to CSV
                var csv = XLSX.utils.aoa_to_sheet(filteredData.slice(headerRowIndex)); // Create a new sheet from filtered array of arrays
                csv = XLSX.utils.sheet_to_csv(csv, { header: 1 });
                return csv;
            } catch (e) {
                console.error(e);
                return "";
            }
        }
        return gk_fileData[filename] || "";
        }
        </script><!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>VOY Out Sourcing - Close More Deals</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-900 text-white font-sans">
  <!-- Header -->
  <header class="bg-gray-800 shadow fixed w-full top-0 z-10">
    <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
      <h1 class="text-3xl font-bold text-purple-400">VOY</h1>
      <ul class="flex space-x-6">
        <li><a href="#home" class="text-gray-300 hover:text-red-400">Home</a></li>
        <li><a href="#about" class="text-gray-300 hover:text-red-400">About</a></li>
        <li><a href="#why-voy" class="text-gray-300 hover:text-red-400">Why VOY?</a></li>
        <li><a href="#contact" class="text-gray-300 hover:text-red-400">Contact</a></li>
      </ul>
    </nav>
  </header>

  <!-- Hero Section -->
  <section id="home" class="bg-gradient-to-r from-blue-700 to-purple-7**00 text-white py-32">
    <div class="container mx-auto px-6 text-center">
      <h2 class="text-5xl font-bold mb-4">Close More Deals with VOY</h2>
      <p class="text-xl mb-6">Professionally Trained and Managed Lead Specialists for Your Business</p>
      <a href="#contact" class="bg-red-500 text-white px-8 py-3 rounded-full font-semibold hover:bg-red-600">Get Started</a>
    </div>
  </section>

  <!-- About Section -->
  <section id="about" class="py-20 bg-gray-800">
    <div class="container mx-auto px-6">
      <h2 class="text-4xl font-bold text-center text-purple-400 mb-8">About VOY Out Sourcing</h2>
      <p class="text-gray-300 text-center max-w-3xl mx-auto text-lg">
        VOY provides you with professionally trained callers who will go through your goals to motivate customers and deliver professional support.
      </p>
    </div>
  </section>

  <!-- Why Choose VOY Section -->
  <section id="why-voy" class="py-20 bg-gray-900">
    <div class="container mx-auto px-6 text-center">
      <h2 class="text-4xl font-bold text-purple-400 mb-8">Why Choose VOY?</h2>
      <p class="text-gray-300 max-w-3xl mx-auto text-lg mb-6">
        Stop worrying, we’ve got your back! Our team of Professional Callers are trained to get your customers satisfied in no time!
      </p>
    </div>
  </section>

  <!-- Contact Section -->
  <section id="contact" class="bg-gray-800 py-20">
    <div class="container mx-auto px-6 text-center">
      <h2 class="text-4xl font-bold text-purple-400 mb-8">Get in Touch</h2>
      <p class="text-gray-300 mb-6 text-lg">Ready to close more deals? Contact us today!</p>
      <div class="flex flex-col items-center space-y-4">
        <a href="tel:+201550395056" class="text-blue-400 hover:text-blue-500 text-lg">Phone: +201550395056</a>
        <a href="http://www.voy.com" target="_blank" class="text-blue-400 hover:text-blue-500 text-lg">Website: www.voy.com</a>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer class="bg-gray-900 text-gray-300 py-6">
    <div class="container mx-auto px-6 text-center">
      <p>&copy; 2025 VOY Out Sourcing. All rights reserved.</p>
    </div>
  </footer>

  <script>
    // Smooth scrolling for navigation links
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function(e) {
        e.preventDefault();
        document.querySelector(this.getAttribute('href')).scrollIntoView({
          behavior: 'smooth'
        });
      });
    });
  </script>
</body>
</html>
