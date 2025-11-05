<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>High-Impact Observation Tracker</title>
    <!-- Load Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f7f9fb;
        }
        .scroll-container {
            max-height: 80vh;
            overflow-y: auto;
        }
        /* Style for the new modal */
        .modal {
            display: none; 
            position: fixed; 
            z-index: 100; 
            left: 0;
            top: 0;
            width: 100%; 
            height: 100%; 
            overflow: auto; 
            background-color: rgba(0,0,0,0.4); 
            backdrop-filter: blur(5px);
        }
        .modal-content {
            background-color: #fefefe;
            margin: 10% auto; 
            padding: 24px;
            border-radius: 12px;
            width: 90%; 
            max-width: 700px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
            position: relative;
        }
    </style>
</head>
<body class="p-4 md:p-8">

    <!-- Main Header -->
    <header class="mb-8 border-b pb-4">
        <h1 class="text-3xl font-bold text-gray-800">ISS Informal Observation Dashboard</h1>
        <p class="text-gray-500">Log informal observations focused on high-impact instructional practices</p>
    </header>

    <!-- Global Message Box for Errors/Success -->
    <div id="message-box" class="hidden fixed top-4 right-4 p-4 rounded-lg text-white font-medium shadow-lg z-50 transition-opacity duration-300"></div>

    <!-- Main Grid Layout -->
    <main class="grid grid-cols-1 lg:grid-cols-3 gap-8">
        
        <!-- COLUMN 1: Observation Form -->
        <div class="lg:col-span-1 p-6 bg-white rounded-xl shadow-lg h-full">
            <h2 class="text-xl font-semibold text-indigo-700 mb-6 border-b pb-2">Log New Observation</h2>
            <form id="observation-form">
                
                <!-- Metadata -->
                <div class="mb-4">
                    <label for="teacherName" class="block text-sm font-medium text-gray-700">Teacher Name</label>
                    <input type="text" id="teacherName" required class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 p-2 border">
                </div>
                <div class="mb-4">
                    <label for="date" class="block text-sm font-medium text-gray-700">Date</label>
                    <input type="date" id="date" required class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 p-2 border">
                </div>
                <div class="mb-4">
                    <label for="time" class="block text-sm font-medium text-gray-700">Time (Approx)</label>
                    <input type="time" id="time" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 p-2 border">
                </div>
                <div class="mb-4">
                    <label for="observerName" class="block text-sm font-medium text-gray-700">Observer Name</label>
                    <input type="text" id="observerName" required class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 p-2 border">
                </div>

                <!-- NEW DROPDOWNS -->
                <div class="mb-4">
                    <label for="classType" class="block text-sm font-medium text-gray-700">Class Type</label>
                    <select id="classType" required class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 p-2 border bg-white">
                        <option value="" disabled selected>Select Class Type</option>
                        <option value="Reading">Reading</option>
                        <option value="Math">Math</option>
                        <option value="AIM">AIM</option>
                        <option value="ESOL">ESOL</option>
                        <option value="Study Skills">Study Skills</option>
                        <option value="Tier 3 Intervention">Tier 3 Intervention</option>
                    </select>
                </div>
                <div class="mb-6">
                    <label for="gradeBand" class="block text-sm font-medium text-gray-700">Grade Band</label>
                    <select id="gradeBand" required class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-indigo-500 focus:ring-indigo-500 p-2 border bg-white">
                        <option value="" disabled selected>Select Grade Band</option>
                        <option value="PGB">PGB</option>
                        <option value="EGB">EGB</option>
                        <option value="MGB">MGB</option>
                        <option value="SGB">SGB</option>
                    </select>
                </div>

                <!-- Instructional Look-Fors (FOCUSED CATEGORIES) -->
                <h3 class="text-lg font-medium text-gray-800 mb-4 border-t pt-4">Instructional Look-Fors (High-Leverage)</h3>
                
                <!-- Observed TEACHER Behaviors (6) -->
                <div class="mb-6 border-b pb-4">
                    <h4 class="text-base font-semibold text-gray-700 mb-3 text-indigo-700">Observed Teacher Behaviors</h4>
                    <div class="space-y-3 text-sm">
                        <div class="flex items-center">
                            <input id="metric_T_onCamera" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_T_onCamera" class="ml-3 font-medium text-gray-700">Teacher On-Camera (Required)</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_T_scaffolding" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_T_scaffolding" class="ml-3 text-gray-600">Scaffolding (Supports tailored to the task)</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_T_smallGroup" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_T_smallGroup" class="ml-3 text-gray-600">Small-Group Instruction/Breakouts</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_T_modeling" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_T_modeling" class="ml-3 text-gray-600">Modeling (Think alouds, worked examples)</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_T_dataChats" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_T_dataChats" class="ml-3 text-gray-600">Data Chats (Using evidence to drive learning)</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_T_cfu" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_T_cfu" class="ml-3 text-gray-600">Checks for Understanding (Quick, formative)</label>
                        </div>
                    </div>
                </div>

                <!-- Observed STUDENT Behaviors (4) -->
                <div class="mb-6 border-b pb-4">
                    <h4 class="text-base font-semibold text-gray-700 mb-3 text-indigo-700">Observed Student Behaviors</h4>
                    <div class="space-y-3 text-sm">
                         <div class="flex items-center">
                            <input id="metric_S_onCamera" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_S_onCamera" class="ml-3 text-gray-600">Students on Camera</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_S_activeResponse" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_S_activeResponse" class="ml-3 text-gray-600">Students Actively Responding (Chat, Mic, Polling)</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_S_whiteboardWork" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_S_whiteboardWork" class="ml-3 text-gray-600">Students Constructing Knowledge (Whiteboard/Desmos)</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_S_iReady" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_S_iReady" class="ml-3 text-gray-600">Students Working Independently/Small Group</label>
                        </div>
                    </div>
                </div>
                
                <!-- Check-Offs (6) -->
                <div class="mb-6">
                    <h4 class="text-base font-semibold text-gray-700 mb-3 text-indigo-700">Check-Offs</h4>
                    <div class="space-y-3 text-sm">
                         <div class="flex items-center">
                            <input id="metric_C_clearTargets" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_C_clearTargets" class="ml-3 text-gray-600">Clear Learning Targets</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_C_safeEnvironment" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_C_safeEnvironment" class="ml-3 text-gray-600">Safe & Conducive Learning Environment</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_C_variedTools" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_C_variedTools" class="ml-3 text-gray-600">Differentiated Instruction</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_C_lessonStructure" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_C_lessonStructure" class="ml-3 text-gray-600">Clear Lesson Structure</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_C_effectiveTime" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_C_effectiveTime" class="ml-3 text-gray-600">Effective Use of Instructional Time</label>
                        </div>
                        <div class="flex items-center">
                            <input id="metric_C_positiveFeedback" type="checkbox" class="h-4 w-4 text-indigo-600 border-gray-300 rounded focus:ring-indigo-500">
                            <label for="metric_C_positiveFeedback" class="ml-3 text-gray-600">Timely and Responsive Feedback Provided</label>
                        </div>
                    </div>
                </div>

                <!-- Qualitative Feedback -->
                <div class="mt-6 mb-4">
                    <label for="glows" class="block text-sm font-medium text-green-700">Glows</label>
                    <textarea id="glows" rows="3" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-green-500 focus:ring-green-500 p-2 border"></textarea>
                </div>
                <div class="mb-4">
                    <label for="grows" class="block text-sm font-medium text-red-700">Grows</label>
                    <textarea id="grows" rows="3" class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-red-500 focus:ring-red-500 p-2 border"></textarea>
                </div>
                
                <!-- Gemini API Button -->
                <button type="button" id="generate-report-button" class="w-full py-2 px-4 mb-6 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-pink-600 hover:bg-pink-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-pink-500 transition duration-150 flex items-center justify-center">
                    <span id="report-text">✨ Generate Coaching Report</span>
                    <span id="report-loading" class="hidden flex items-center">
                        <svg class="animate-spin -ml-1 mr-3 h-5 w-5 text-white" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                            <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                            <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                        </svg>
                        Generating...
                    </span>
                </button>

                <button type="submit" id="submit-button" class="w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 transition duration-150">
                    <span id="submit-text">Submit Observation</span>
                    <span id="submit-loading" class="hidden">...Saving Data</span>
                </button>
            </form>
        </div>

        <!-- COLUMN 2 & 3: Real-Time Dashboard and Observation Log -->
        <div class="lg:col-span-2 space-y-8">
            
            <!-- Real-Time Metrics Dashboard -->
            <div class="p-6 bg-white rounded-xl shadow-lg">
                <h2 class="text-xl font-semibold text-indigo-700 mb-6 border-b pb-2">Real-Time Instructional Trends</h2>
                
                <div id="loading-dashboard" class="text-center p-8 text-gray-500">Loading live data...</div>
                
                <div id="dashboard-content" class="hidden">
                    <p class="text-2xl font-bold text-gray-800 mb-4">Total Observations Logged: <span id="total-observations" class="text-indigo-600">0</span></p>

                    <div id="metrics-charts" class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <!-- Charts will be injected here -->
                    </div>
                </div>
            </div>

            <!-- Observation Log Table -->
            <div class="p-6 bg-white rounded-xl shadow-lg">
                <h2 class="text-xl font-semibold text-indigo-700 mb-4 border-b pb-2">Recent Observations Log</h2>
                <div class="scroll-container border rounded-lg">
                    <table class="min-w-full divide-y divide-gray-200">
                        <thead class="bg-gray-50 sticky top-0 z-10">
                            <tr>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Teacher</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Observer</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Type</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Band</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Date</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Active Response</th>
                                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Glows/Grows</th>
                            </tr>
                        </thead>
                        <tbody id="observations-table-body" class="bg-white divide-y divide-gray-200">
                            <!-- Rows will be injected here -->
                        </tbody>
                    </table>
                </div>
            </div>

        </div>
    </main>
    
    <!-- Gemini Report Modal -->
    <div id="report-modal" class="modal">
        <div class="modal-content">
            <div class="flex justify-between items-center border-b pb-3 mb-4">
                <h3 class="text-xl font-bold text-pink-600">Generated Coaching Report</h3>
                <button onclick="document.getElementById('report-modal').style.display='none'" class="text-gray-500 hover:text-gray-700 text-2xl font-semibold">&times;</button>
            </div>
            
            <div id="generated-report-content" class="space-y-4">
                <p id="report-loading-message" class="text-center text-gray-500">
                    <svg class="animate-spin inline-block mr-2 h-5 w-5 text-pink-500" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                        <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
                        <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                    </svg>
                    Analyzing observation data and generating report...
                </p>
                <!-- Report will be injected here -->
            </div>

            <div class="mt-6 pt-4 border-t flex justify-end space-x-3">
                <button onclick="copyReportToClipboard()" class="py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-white bg-green-500 hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500 transition duration-150">
                    Copy to Clipboard
                </button>
                <button onclick="document.getElementById('report-modal').style.display='none'" class="py-2 px-4 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 transition duration-150">
                    Close
                </button>
            </div>
        </div>
    </div>

    <!-- Firebase SDK Scripts -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, addDoc, onSnapshot, collection, query, orderBy, serverTimestamp, setLogLevel } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Global Firebase variables will be defined by the Canvas environment
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : null;

        let db, auth, userId;
        const COL_PATH = `artifacts/${appId}/public/data/observations`;
        const GEMINI_MODEL = 'gemini-2.5-flash-preview-09-2025';
        const API_KEY = ""; // Placeholder for Canvas environment

        // Utility to display messages
        function showMessage(text, isError = false) {
            const box = document.getElementById('message-box');
            box.textContent = text;
            box.classList.remove('hidden', 'bg-red-500', 'bg-green-500');
            box.classList.add(isError ? 'bg-red-500' : 'bg-green-500');
            setTimeout(() => box.classList.add('hidden'), 3000);
        }

        // --- 1. FIREBASE INITIALIZATION AND AUTHENTICATION ---
        try {
            // setLogLevel('Debug'); // Enable for debugging Firestore
            const app = initializeApp(firebaseConfig);
            db = getFirestore(app);
            auth = getAuth(app);

            onAuthStateChanged(auth, async (user) => {
                if (user) {
                    userId = user.uid;
                    console.log("Firebase Auth Ready. User ID:", userId);
                    setupRealTimeListener();
                } else {
                    console.log("No user signed in. Attempting sign-in.");
                    if (initialAuthToken) {
                        await signInWithCustomToken(auth, initialAuthToken);
                    } else {
                        await signInAnonymously(auth);
                    }
                }
            });
        } catch (e) {
            console.error("Firebase initialization error:", e);
            showMessage("Database initialization failed.", true);
        }
        
        // --- 2. DATA SUBMISSION ---
        document.getElementById('observation-form').addEventListener('submit', async (e) => {
            e.preventDefault();
            const submitButton = document.getElementById('submit-button');
            const submitText = document.getElementById('submit-text');
            const submitLoading = document.getElementById('submit-loading');

            submitText.classList.add('hidden');
            submitLoading.classList.remove('hidden');
            submitButton.disabled = true;

            try {
                if (!db || !userId) {
                    throw new Error("Database or user not ready. Please wait a moment.");
                }

                const observationData = {
                    teacherName: document.getElementById('teacherName').value,
                    observerName: document.getElementById('observerName').value,
                    classType: document.getElementById('classType').value,
                    gradeBand: document.getElementById('gradeBand').value,
                    date: document.getElementById('date').value,
                    time: document.getElementById('time').value,
                    
                    // Instructional Look-Fors (Boolean values) - 16 focused metrics
                    // TEACHER BEHAVIORS (6)
                    metric_T_onCamera: document.getElementById('metric_T_onCamera').checked,
                    metric_T_scaffolding: document.getElementById('metric_T_scaffolding').checked,
                    metric_T_smallGroup: document.getElementById('metric_T_smallGroup').checked,
                    metric_T_modeling: document.getElementById('metric_T_modeling').checked,
                    metric_T_dataChats: document.getElementById('metric_T_dataChats').checked,
                    metric_T_cfu: document.getElementById('metric_T_cfu').checked,

                    // STUDENT BEHAVIORS (4)
                    metric_S_onCamera: document.getElementById('metric_S_onCamera').checked,
                    metric_S_activeResponse: document.getElementById('metric_S_activeResponse').checked,
                    metric_S_whiteboardWork: document.getElementById('metric_S_whiteboardWork').checked,
                    metric_S_iReady: document.getElementById('metric_S_iReady').checked,

                    // CHECK-OFFS (6)
                    metric_C_clearTargets: document.getElementById('metric_C_clearTargets').checked,
                    metric_C_safeEnvironment: document.getElementById('metric_C_safeEnvironment').checked,
                    metric_C_variedTools: document.getElementById('metric_C_variedTools').checked,
                    metric_C_lessonStructure: document.getElementById('metric_C_lessonStructure').checked,
                    metric_C_effectiveTime: document.getElementById('metric_C_effectiveTime').checked,
                    metric_C_positiveFeedback: document.getElementById('metric_C_positiveFeedback').checked,


                    // Qualitative
                    glows: document.getElementById('glows').value,
                    grows: document.getElementById('grows').value,

                    // Metadata for Firestore
                    timestamp: serverTimestamp(),
                    userId: userId,
                };

                await addDoc(collection(db, COL_PATH), observationData);
                
                document.getElementById('observation-form').reset();
                showMessage("Observation saved successfully!");

            } catch (error) {
                console.error("Error saving document: ", error);
                showMessage("Failed to save observation: " + error.message, true);
            } finally {
                submitText.classList.remove('hidden');
                submitLoading.classList.add('hidden');
                submitButton.disabled = false;
            }
        });

        // --- 3. LLM GENERATION LOGIC ---

        const METRIC_NAMES = {
            metric_T_onCamera: 'Teacher On-Camera (Required)',
            metric_T_scaffolding: 'Scaffolding',
            metric_T_smallGroup: 'Small-Group Instruction/Breakouts',
            metric_T_modeling: 'Modeling (Think alouds, worked examples)',
            metric_T_dataChats: 'Data Chats (Using evidence to drive learning)',
            metric_T_cfu: 'Checks for Understanding (Quick, formative)',
            metric_S_onCamera: 'Students on Camera',
            metric_S_activeResponse: 'Students Actively Responding (Chat, Mic, Polling)',
            metric_S_whiteboardWork: 'Students Constructing Knowledge (Whiteboard/Desmos)',
            metric_S_iReady: 'Students Working Independently/Small Group',
            metric_C_clearTargets: 'Clear Learning Targets',
            metric_C_safeEnvironment: 'Safe & Conducive Learning Environment',
            metric_C_variedTools: 'Differentiated Instruction',
            metric_C_lessonStructure: 'Clear Lesson Structure',
            metric_C_effectiveTime: 'Effective Use of Instructional Time',
            metric_C_positiveFeedback: 'Timely and Responsive Feedback Provided',
        };
        
        // Function to call the Gemini API with exponential backoff
        async function callGeminiAPIWithRetry(payload, maxRetries = 5, delay = 1000) {
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/${GEMINI_MODEL}:generateContent?key=${API_KEY}`;

            for (let i = 0; i < maxRetries; i++) {
                try {
                    const response = await fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    if (response.status === 429 && i < maxRetries - 1) {
                        // Rate limit exceeded, retry after delay
                        await new Promise(resolve => setTimeout(resolve, delay * (2 ** i)));
                        continue;
                    }

                    if (!response.ok) {
                        throw new Error(`HTTP error! status: ${response.status}`);
                    }

                    const result = await response.json();
                    
                    if (result.candidates && result.candidates.length > 0 && 
                        result.candidates[0].content && result.candidates[0].content.parts && 
                        result.candidates[0].content.parts.length > 0) {
                        const jsonText = result.candidates[0].content.parts[0].text;
                        return JSON.parse(jsonText);
                    }
                    throw new Error("Invalid response structure from API.");

                } catch (error) {
                    if (i === maxRetries - 1) {
                        throw new Error("API call failed after multiple retries: " + error.message);
                    }
                    // Log to console without showing an error box for silent retries
                    console.warn(`Attempt ${i + 1} failed. Retrying in ${delay * (2 ** i) / 1000}s.`, error);
                }
            }
        }

        document.getElementById('generate-report-button').addEventListener('click', generateCoachingReport);

        async function generateCoachingReport() {
            const glows = document.getElementById('glows').value;
            const grows = document.getElementById('grows').value;
            
            if (!glows && !grows) {
                showMessage("Please enter 'Glows' or 'Grows' to generate a report.", true);
                return;
            }

            const button = document.getElementById('generate-report-button');
            const textSpan = document.getElementById('report-text');
            const loadingSpan = document.getElementById('report-loading');
            const modal = document.getElementById('report-modal');
            const reportContent = document.getElementById('generated-report-content');
            const loadingMessage = document.getElementById('report-loading-message');

            // Collect all checked and unchecked metrics
            const metricResults = [];
            Object.keys(METRIC_NAMES).forEach(id => {
                const checked = document.getElementById(id).checked;
                metricResults.push(`${METRIC_NAMES[id]}: ${checked ? 'Observed (Glow)' : 'Not Observed (Potential Grow)'}`);
            });
            
            const rawData = `
                --- Raw Observation Data ---
                Glows (Specific Positive Comments): ${glows || 'None provided.'}
                Grows (Specific Areas for Improvement): ${grows || 'None provided.'}
                
                Instructional Checklists:
                ${metricResults.join('\n')}
            `;

            // UI feedback
            textSpan.classList.add('hidden');
            loadingSpan.classList.remove('hidden');
            button.disabled = true;
            loadingMessage.classList.remove('hidden');
            reportContent.innerHTML = ''; // Clear previous content
            modal.style.display = 'block';

            const systemPrompt = "You are a highly experienced Instructional Coach focused on high-leverage practices. Your goal is to analyze the provided raw observation data (Glows, Grows, and instructional metrics) and synthesize it into a structured, professional, and encouraging coaching report. Use clear, positive, and growth-oriented language. The 'affirmationSummary' must be encouraging, and the 'actionPlan' must be 3-5 specific, actionable steps, drawing from the 'Grows' and 'Not Observed' metrics.";
            
            const userQuery = `Generate the coaching report based on the following observation data: ${rawData}`;

            const payload = {
                contents: [{ parts: [{ text: userQuery }] }],
                systemInstruction: { parts: [{ text: systemPrompt }] },
                generationConfig: {
                    responseMimeType: "application/json",
                    responseSchema: {
                        type: "OBJECT",
                        properties: {
                            "affirmationSummary": { 
                                "type": "STRING", 
                                "description": "A 1-2 sentence encouraging summary of the positive observations (Glows)." 
                            },
                            "actionPlan": {
                                "type": "ARRAY",
                                "description": "3-5 specific, high-leverage, and actionable growth steps for the teacher.",
                                "items": { "type": "STRING" }
                            },
                            "keyTakeaway": { 
                                "type": "STRING", 
                                "description": "A single, overarching key takeaway or focus area for the teacher's next lesson." 
                            }
                        },
                        "propertyOrdering": ["affirmationSummary", "actionPlan", "keyTakeaway"]
                    }
                }
            };
            
            try {
                const report = await callGeminiAPIWithRetry(payload);
                renderReport(report);
            } catch (error) {
                console.error("Gemini Report Generation Error:", error);
                reportContent.innerHTML = `<p class="text-red-500">Error generating report. Please check the console for details. Data was likely too sparse or the network failed.</p>`;
                showMessage("Report generation failed.", true);
            } finally {
                textSpan.classList.remove('hidden');
                loadingSpan.classList.add('hidden');
                button.disabled = false;
                loadingMessage.classList.add('hidden');
            }
        }

        function renderReport(report) {
            const reportContent = document.getElementById('generated-report-content');
            
            // Generate Markdown-style report for display
            const reportHTML = `
                <div id="coaching-report-text">
                    <!-- Affirmation Summary -->
                    <h4 class="text-lg font-bold text-green-700 mb-2">Summary (Glows)</h4>
                    <p class="mb-6 border-l-4 border-green-400 pl-3 italic">${report.affirmationSummary}</p>
                    
                    <!-- Action Plan -->
                    <h4 class="text-lg font-bold text-red-700 mb-2">High-Leverage Next Steps (Grows)</h4>
                    <ul class="list-disc list-inside space-y-2 mb-6">
                        ${report.actionPlan.map(step => `<li class="ml-4 text-gray-700">${step}</li>`).join('')}
                    </ul>

                    <!-- Key Takeaway -->
                    <h4 class="text-lg font-bold text-indigo-700 mb-2">Key Takeaway</h4>
                    <p class="p-3 bg-indigo-50 border border-indigo-200 rounded-lg font-medium">${report.keyTakeaway}</p>
                </div>
            `;
            reportContent.innerHTML = reportHTML;
        }

        window.copyReportToClipboard = function() {
            const reportTextDiv = document.getElementById('coaching-report-text');
            if (!reportTextDiv) {
                showMessage("No report to copy.", true);
                return;
            }

            // Convert HTML structure back to a clean text format for email/document
            let textToCopy = `Instructional Coaching Report\n\n`;
            
            const summary = reportTextDiv.querySelector('h4:nth-of-type(1) + p').textContent.trim();
            textToCopy += `Summary (Glows):\n${summary}\n\n`;

            const actionPlanItems = Array.from(reportTextDiv.querySelectorAll('ul li')).map(li => `- ${li.textContent.trim()}`);
            textToCopy += `High-Leverage Next Steps (Grows):\n${actionPlanItems.join('\n')}\n\n`;

            const takeaway = reportTextDiv.querySelector('h4:nth-of-type(3) + p').textContent.trim();
            textToCopy += `Key Takeaway:\n${takeaway}`;
            
            // Use standard method for clipboard copy
            if (navigator.clipboard && navigator.clipboard.writeText) {
                navigator.clipboard.writeText(textToCopy).then(() => {
                    showMessage("Report copied to clipboard!");
                }).catch(err => {
                    console.error('Could not copy text: ', err);
                    showMessage("Copy failed. Try selecting the text manually.", true);
                });
            } else {
                 // Fallback for older browsers (though not reliable in all iFrames)
                const textArea = document.createElement("textarea");
                textArea.value = textToCopy;
                document.body.appendChild(textArea);
                textArea.focus();
                textArea.select();
                try {
                    document.execCommand('copy');
                    showMessage("Report copied to clipboard (via fallback)!");
                } catch (err) {
                    showMessage("Copy failed. Try selecting the text manually.", true);
                }
                document.body.removeChild(textArea);
            }
        }


        // --- 4. REAL-TIME DATA LISTENER AND RENDERING ---

        const METRICS = [
            // TEACHER BEHAVIORS (6)
            { id: 'metric_T_onCamera', name: 'T: On-Camera (Req)' },
            { id: 'metric_T_scaffolding', name: 'T: Scaffolding' },
            { id: 'metric_T_smallGroup', name: 'T: Small-Group' },
            { id: 'metric_T_modeling', name: 'T: Modeling' },
            { id: 'metric_T_dataChats', name: 'T: Data Chats' },
            { id: 'metric_T_cfu', name: 'T: Checks for Understanding' },

            // STUDENT BEHAVIORS (4)
            { id: 'metric_S_onCamera', name: 'S: On Camera' },
            { id: 'metric_S_activeResponse', name: 'S: Active Responding' },
            { id: 'metric_S_whiteboardWork', name: 'S: Constructing Knowledge' },
            { id: 'metric_S_iReady', name: 'S: Working in iReady' },

            // CHECK-OFFS (6)
            { id: 'metric_C_clearTargets', name: 'C: Clear Learning Targets' },
            { id: 'metric_C_safeEnvironment', name: 'C: Safe Environment' },
            { id: 'metric_C_variedTools', name: 'C: Differentiated Instruction' },
            { id: 'metric_C_lessonStructure', name: 'C: Lesson Structure' },
            { id: 'metric_C_effectiveTime', name: 'C: Effective Time Use' },
            { id: 'metric_C_positiveFeedback', name: 'C: Timely/Responsive Feedback' },
        ];

        function setupRealTimeListener() {
            const q = query(collection(db, COL_PATH), orderBy("timestamp", "desc"));

            onSnapshot(q, (snapshot) => {
                const observations = [];
                const metricsCount = {};
                let totalObservations = 0;

                METRICS.forEach(m => metricsCount[m.id] = 0);

                snapshot.forEach((doc) => {
                    const data = doc.data();
                    observations.push(data);
                    totalObservations++;

                    METRICS.forEach(m => {
                        // Ensure that we only count metrics if they are explicitly true
                        if (data[m.id] === true) {
                            metricsCount[m.id]++;
                        }
                    });
                });

                document.getElementById('loading-dashboard').classList.add('hidden');
                document.getElementById('dashboard-content').classList.remove('hidden');

                renderDashboard(totalObservations, metricsCount);
                renderTable(observations);

            }, (error) => {
                console.error("Error listening to Firestore: ", error);
                showMessage("Failed to load real-time data.", true);
            });
        }

        function renderDashboard(totalObservations, metricsCount) {
            document.getElementById('total-observations').textContent = totalObservations;
            const chartsContainer = document.getElementById('metrics-charts');
            chartsContainer.innerHTML = ''; // Clear previous charts

            if (totalObservations === 0) {
                chartsContainer.innerHTML = '<p class="col-span-2 text-center text-gray-500">No observations logged yet. Submit a form to see the data!</p>';
                return;
            }

            METRICS.forEach(metric => {
                const count = metricsCount[metric.id];
                const percentage = Math.round((count / totalObservations) * 100);

                const chartHTML = `
                    <div class="bg-gray-50 p-4 rounded-lg shadow-sm">
                        <p class="text-sm font-semibold text-gray-700 mb-1">${metric.name}</p>
                        <div class="flex justify-between items-baseline mb-1">
                            <span class="text-2xl font-extrabold text-indigo-600">${percentage}%</span>
                            <span class="text-xs text-gray-500">${count} of ${totalObservations}</span>
                        </div>
                        <div class="w-full bg-gray-200 rounded-full h-2.5">
                            <div class="h-2.5 rounded-full" style="width: ${percentage}%; background-color: ${percentage > 75 ? '#10B981' : percentage > 50 ? '#F59E0B' : '#EF4444'};"></div>
                        </div>
                    </div>
                `;
                chartsContainer.insertAdjacentHTML('beforeend', chartHTML);
            });
        }

        function renderTable(observations) {
            const tableBody = document.getElementById('observations-table-body');
            tableBody.innerHTML = ''; // Clear previous rows

            observations.forEach(obs => {
                // Ensure obs.date is treated as a string for Date constructor
                const date = obs.date ? new Date(obs.date).toLocaleDateString('en-US', { month: 'short', day: 'numeric' }) : 'N/A';
                const time = obs.time ? ` @ ${obs.time}` : '';
                // Use the Student Active Response metric for the dedicated column (high-leverage)
                const activeResponseIcon = obs.metric_S_activeResponse 
                    ? '<span class="text-green-500 text-xl" title="Yes">&#10003;</span>' 
                    : '<span class="text-red-500 text-xl" title="No">&#10006;</span>';

                const rowHTML = `
                    <tr class="hover:bg-indigo-50 transition duration-100">
                        <td class="px-6 py-3 whitespace-nowrap text-sm font-medium text-gray-900">${obs.teacherName}</td>
                        <td class="px-6 py-3 whitespace-nowrap text-sm text-gray-500">${obs.observerName}</td>
                        <td class="px-6 py-3 whitespace-nowrap text-sm text-gray-500">${obs.classType || 'N/A'}</td>
                        <td class="px-6 py-3 whitespace-nowrap text-sm text-gray-500">${obs.gradeBand || 'N/A'}</td>
                        <td class="px-6 py-3 whitespace-nowrap text-sm text-gray-500">${date}${time}</td>
                        <td class="px-6 py-3 whitespace-nowrap text-center">${activeResponseIcon}</td>
                        <td class="px-6 py-3 text-sm text-gray-500 max-w-xs truncate">
                            <span class="font-semibold text-green-700">Glow:</span> ${obs.glows || 'N/A'}<br>
                            <span class="font-semibold text-red-700">Grow:</span> ${obs.grows || 'N/A'}
                        </td>
                    </tr>
                `;
                tableBody.insertAdjacentHTML('beforeend', rowHTML);
            });
        }

    </script>
</body>
</html>
