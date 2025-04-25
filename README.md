```html
   <!DOCTYPE html>
   <html lang="ar" dir="rtl">
   <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <meta name="description" content="FBOX - دردشة ذكية تعمل بالذكاء الاصطناعي للإجابة على أسئلتك بسهولة وسرعة">
     <meta name="keywords" content="FBOX, ذكاء اصطناعي, دردشة, واجهة ذكية">
     <meta name="author" content="FBOX Team">
     <title>FBOX - الدردشة الذكية</title>
     <link rel="icon" type="image/png" href="favicon.png">
     <script src="https://cdn.tailwindcss.com"></script>
   </head>
   <body class="bg-gradient-to-b from-blue-500 to-indigo-600 min-h-screen font-sans">
     <!-- Header -->
     <header class="bg-blue-700 text-white py-4 shadow">
       <div class="container mx-auto px-4 flex justify-between items-center">
         <h1 class="text-xl font-bold">FBOX</h1>
       </div>
     </header>

     <!-- Chat Section -->
     <section class="container mx-auto px-4 py-8">
       <div class="max-w-2xl mx-auto bg-white rounded-lg shadow-lg p-6">
         <h2 class="text-2xl font-bold text-gray-800 mb-4 text-center">تحدث مع FBOX</h2>
         <div id="chatArea" class="h-96 overflow-y-auto p-4 bg-gray-50 rounded-lg mb-4">
           <div class="flex justify-start mb-2">
             <div class="bg-gray-200 text-gray-800 p-3 rounded-lg max-w-xs">مرحبًا! أنا FBOX، جاهز للدردشة. ماذا تريد مناقشته؟</div>
           </div>
         </div>
         <div class="flex gap-2">
           <input id="userInput" type="text" placeholder="اكتب رسالتك هنا..." class="flex-1 p-3 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-600">
           <button onclick="sendMessage()" class="bg-blue-600 text-white px-6 py-3 rounded-lg font-semibold hover:bg-blue-700">إرسل</button>
         </div>
       </div>
     </section>

     <!-- Footer -->
     <footer class="bg-blue-700 text-white py-4 text-center">
       <p>© 2025 FBOX. جميع الحقوق محفوظة.</p>
     </footer>

     <script>
       function sendMessage() {
         const userInput = document.getElementById('userInput').value.trim().toLowerCase();
         const chatArea = document.getElementById('chatArea');
         const userMessage = document.createElement('div');
         userMessage.className = 'flex justify-end mb-2';
         userMessage.innerHTML = `<div class="bg-blue-100 text-gray-800 p-3 rounded-lg max-w-xs">${userInput}</div>`;
         
         if (userInput) {
           chatArea.appendChild(userMessage);
           chatArea.scrollTop = chatArea.scrollHeight; // Scroll to bottom
         } else {
           const botMessage = document.createElement('div');
           botMessage.className = 'flex justify-start mb-2';
           botMessage.innerHTML = `<div class="bg-gray-200 text-gray-800 p-3 rounded-lg max-w-xs">الرجاء كتابة شيء لأرد عليك!</div>`;
           chatArea.appendChild(botMessage);
           chatArea.scrollTop = chatArea.scrollHeight;
           return;
         }

         // Generate bot response
         let response = 'FBOX يفكر... 🤔';
         if (userInput.includes('مرحب') || userInput.includes('سلام')) {
           response = 'مرحبًا! سعيد بتواجدك هنا. ما جديدك؟';
         } else if (userInput.includes('كيف') || userInput.includes('؟')) {
           response = 'سؤال رائع! يمكنني مساعدتك إذا أعطيتني المزيد من التفاصيل. ماذا تقصد؟';
         } else if (userInput.includes('شكر') || userInput.includes('مشكور')) {
           response = 'العفو! FBOX هنا دائمًا للمساعدة. 😊';
         } else {
           const suggestions = [
             'حسنًا، هذا مثير للاهتمام! ماذا عن سؤال آخر؟',
             'أحب أفكارك! جرب شيئًا جديدًا.',
             'FBOX جاهز! ما الذي تريد استكشافه؟'
           ];
           response = `${suggestions[Math.floor(Math.random() * suggestions.length)]}`;
         }

         // Append bot response
         const botMessage = document.createElement('div');
         botMessage.className = 'flex justify-start mb-2';
         botMessage.innerHTML = `<div class="bg-gray-200 text-gray-800 p-3 rounded-lg max-w-xs">${response}</div>`;
         setTimeout(() => {
           chatArea.appendChild(botMessage);
           chatArea.scrollTop = chatArea.scrollHeight;
         }, 500); // Slight delay for natural feel

         // Clear input
         document.getElementById('userInput').value = '';
       }

       // Allow sending message with Enter key
       document.getElementById('userInput').addEventListener('keypress', function(e) {
         if (e.key === 'Enter') {
           sendMessage();
         }
       });
     </script>
   </body>
   </html>
   ```
