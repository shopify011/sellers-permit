<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Shopify seller Permit Verification</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/feather-icons"></script>
    <script src="https://cdn.jsdelivr.net/npm/feather-icons/dist/feather.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
        }
        .shopify-gradient {
            background: linear-gradient(135deg, #95BF47 0%, #5E8E3E 100%);
        }
        .input-focus:focus {
            box-shadow: 0 0 0 3px rgba(149, 191, 71, 0.3);
        }
    </style>
</head>
<body class="bg-gray-50 min-h-screen flex items-center justify-center p-4">
    <div class="w-full max-w-md">
        <div class="bg-white rounded-xl shadow-lg overflow-hidden">
            <div class="shopify-gradient p-6 text-white">
                <div class="flex items-center justify-center space-x-3 mb-4">
                    <svg width="24" height="24" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M26.6667 9.33333L16 4L5.33333 9.33333L16 14.6667L26.6667 9.33333Z" fill="white"/>
                        <path d="M5.33333 16.4533V22.6667L15.0667 27.6267C15.36 27.7733 15.68 27.84 16 27.84C16.32 27.84 16.64 27.7733 16.9333 27.6267L26.6667 22.6667V16.4533L16 21.7867L5.33333 16.4533Z" fill="white"/>
                    </svg>
                    <h1 class="text-2xl font-bold">Permit Verification</h1>
                </div>
                <p class="text-center text-sm opacity-90">Check if a Shopify store has a valid seller permit</p>
            </div>

            <div class="p-6 space-y-6">
                <div>
                    <label for="storeUrl" class="block text-sm font-medium text-gray-700 mb-1">Shopify Store URL</label>
                    <div class="relative">
                        <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                            <i data-feather="link" class="text-gray-400"></i>
                        </div>
                        <input type="url" id="storeUrl" placeholder="example.myshopify.com" 
                            class="pl-10 block w-full rounded-md border-gray-300 shadow-sm focus:border-green-500 input-focus py-2 px-3 border">
                    </div>
                </div>

                <button onclick="verifyStore()" 
                    class="shopify-gradient w-full flex items-center justify-center space-x-2 py-3 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white hover:opacity-90 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500 transition">
                    <i data-feather="search" class="w-4 h-4"></i>
                    <span>Verify Store</span>
                </button>

                <div id="resultContainer" class="hidden">
                    <div class="rounded-lg bg-red-50 p-4">
                        <div class="flex">
                            <div class="flex-shrink-0">
                                <i data-feather="alert-triangle" class="h-5 w-5 text-red-400"></i>
                            </div>
                            <div class="ml-3">
                                <h3 class="text-sm font-medium text-red-800">Verification Result</h3>
                                <div id="resultContent" class="mt-2 text-sm text-red-700">
                                    <p>This store does not have a valid seller permit on file.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="bg-gray-50 px-6 py-4 border-t border-gray-200">
                <p class="text-xs text-gray-500 text-center">
                    This tool is not affiliated with or endorsed by Shopify Inc. Verification results are for informational purposes only.
                </p>
            </div>
        </div>
    </div>

    <script>
        feather.replace();
        
        function verifyStore() {
            const storeUrl = document.getElementById('storeUrl').value.trim();
            const resultContainer = document.getElementById('resultContainer');
            
            if (!storeUrl) {
                alert('Please enter a Shopify store URL');
                return;
            }

            // Simple validation for demo purposes
            if (!storeUrl.includes('.myshopify.com') && !storeUrl.includes('//')) {
                alert('Please enter a valid Shopify store URL (e.g., example.myshopify.com)');
                return;
            }

            // Show loading state
            resultContainer.classList.add('hidden');
            
            // Simulate API call with timeout
            setTimeout(() => {
                resultContainer.classList.remove('hidden');
                
                // Scroll to result
                resultContainer.scrollIntoView({ behavior: 'smooth' });
            }, 800);
        }
    </script>
</body>
</html>
