<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplikasi Inputan + WhatsApp</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }
        .container {
            max-width: 1600px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            overflow: hidden;
        }
        .header {
            background: linear-gradient(135deg, #25D366, #128C7E);
            color: white;
            padding: 30px;
            text-align: center;
        }
        .header h1 {
            margin-bottom: 10px;
            font-size: 2.2em;
        }
        .header p {
            opacity: 0.9;
        }
        .form-section {
            padding: 30px;
        }
        .form-group {
            margin-bottom: 20px;
        }
        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
        }
        .form-row-3 {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            gap: 15px;
        }
        .form-row-4 {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr 1fr;
            gap: 15px;
        }
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #333;
        }
        input, select {
            width: 100%;
            padding: 12px;
            border: 2px solid #e1e5e9;
            border-radius: 8px;
            font-size: 14px;
            transition: border-color 0.3s;
        }
        input:focus, select:focus {
            outline: none;
            border-color: #25D366;
        }
        .input-uppercase {
            text-transform: uppercase;
        }
        .input-numeric {
            text-transform: none;
            text-align: right;
        }
        .btn-group {
            display: flex;
            gap: 10px;
            margin-top: 25px;
        }
        button {
            padding: 15px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }
        .btn-primary {
            background: #25D366;
            color: white;
            flex: 1;
        }
        .btn-primary:hover {
            background: #128C7E;
            transform: translateY(-2px);
        }
        .btn-secondary {
            background: #f8f9fa;
            color: #333;
            border: 2px solid #e1e5e9;
            flex: 1;
        }
        .btn-secondary:hover {
            background: #e9ecef;
        }
        .btn-whatsapp {
            background: #25D366;
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }
        .btn-whatsapp:hover {
            background: #128C7E;
            transform: translateY(-2px);
        }
        .data-section {
            padding: 0 30px 30px;
        }
        .data-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            font-size: 14px;
        }
        .data-table th,
        .data-table td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid #e1e5e9;
        }
        .data-table th {
            background: #f8f9fa;
            font-weight: 600;
            color: #333;
            font-size: 12px;
        }
        .data-table tr:hover {
            background: #f8f9fa;
        }
        .whatsapp-section {
            background: #f0f8f0;
            padding: 20px;
            margin: 20px 0;
            border-radius: 10px;
            border-left: 4px solid #25D366;
        }
        .preview-section {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            margin-top: 20px;
        }
        .preview-box {
            background: white;
            padding: 15px;
            border-radius: 8px;
            border: 1px solid #e1e5e9;
            min-height: 100px;
            margin-top: 10px;
            white-space: pre-wrap;
            font-family: monospace;
            line-height: 1.5;
            font-size: 14px;
        }
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            border-radius: 8px;
            color: white;
            font-weight: 600;
            z-index: 1000;
            transition: all 0.3s;
            transform: translateX(400px);
        }
        .notification.show {
            transform: translateX(0);
        }
        .notification.success {
            background: #28a745;
        }
        .notification.error {
            background: #dc3545;
        }
        .action-btn {
            padding: 6px 10px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 11px;
            margin: 2px;
        }
        .btn-delete {
            background: #dc3545;
            color: white;
        }
        .btn-send-single {
            background: #17a2b8;
            color: white;
        }
        .btn-edit {
            background: #ffc107;
            color: black;
        }
        .document-id {
            font-weight: bold;
            color: #25D366;
        }
        .current-doc-info {
            background: #e7f3ff;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            border-left: 4px solid #007bff;
        }
        .input-items {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 8px;
            margin-top: 20px;
        }
        .item-row {
            display: grid;
            grid-template-columns: 2fr 2fr 2fr 2fr 2fr 2fr 2fr 1fr;
            gap: 10px;
            align-items: end;
            margin-bottom: 15px;
            padding-bottom: 15px;
            border-bottom: 1px solid #e1e5e9;
        }
        .item-actions {
            display: flex;
            gap: 5px;
        }
        .btn-add-item {
            background: #007bff;
            color: white;
            padding: 10px 15px;
        }
        .btn-remove-item {
            background: #dc3545;
            color: white;
            padding: 8px 12px;
        }
        .total-section {
            background: #e7f3ff;
            padding: 15px;
            border-radius: 8px;
            margin-top: 15px;
            font-weight: bold;
        }
        .login-section {
            background: white;
            padding: 40px;
            border-radius: 15px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            max-width: 400px;
            margin: 100px auto;
            text-align: center;
        }
        .login-form {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }
        .login-input {
            padding: 15px;
            border: 2px solid #e1e5e9;
            border-radius: 8px;
            font-size: 16px;
        }
        .login-input:focus {
            outline: none;
            border-color: #25D366;
        }
        .login-btn {
            background: #25D366;
            color: white;
            padding: 15px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
        }
        .login-btn:hover {
            background: #128C7E;
        }
        .user-info {
            background: #e7f3ff;
            padding: 10px 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .logout-btn {
            background: #dc3545;
            color: white;
            padding: 8px 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .search-section {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
        }
        .search-form {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr 1fr;
            gap: 10px;
            align-items: end;
        }
        .hidden {
            display: none;
        }
        .edit-mode {
            background: #fff3cd;
            border-left: 4px solid #ffc107;
        }
        .customer-summary {
            background: #e7f3ff;
            padding: 10px;
            border-radius: 8px;
            margin-top: 10px;
            font-size: 12px;
        }
        .auto-calculated {
            background-color: #f0f8f0;
            border: 1px solid #25D366;
        }
        .validation-error {
            border-color: #dc3545 !important;
            background-color: #fff5f5;
        }
        .validation-message {
            color: #dc3545;
            font-size: 12px;
            margin-top: 5px;
        }
        .input-hint {
            font-size: 12px;
            color: #6c757d;
            margin-top: 5px;
        }
        @media (max-width: 768px) {
            .form-row, .form-row-3, .form-row-4 {
                grid-template-columns: 1fr;
            }
            .btn-group {
                flex-direction: column;
            }
            .data-table {
                font-size: 12px;
            }
            .item-row {
                grid-template-columns: 1fr;
            }
            .search-form {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Login Section -->
    <div id="loginSection" class="login-section">
        <h2>🔐 Login Aplikasi</h2>
        <p>Masukkan username dan password untuk melanjutkan</p>
        <form id="loginForm" class="login-form">
            <input type="text" id="username" class="login-input" placeholder="Username" required>
            <input type="password" id="password" class="login-input" placeholder="Password" required>
            <button type="submit" class="login-btn">Login</button>
        </form>
        <div id="loginError" style="color: #dc3545; margin-top: 15px; display: none;">
            ❌ Username atau password salah!
        </div>
        
        <!-- Info Login untuk Testing -->
        <div style="margin-top: 20px; padding: 15px; background: #f8f9fa; border-radius: 8px; font-size: 12px;">
            <strong>Info Login (untuk testing):</strong><br>
            • User: JIMMY - Pass: JIMMY11<br>
            • User: LUKAS - Pass: LUKAS22<br>
            • User: NANDO - Pass: NANDO33
        </div>
    </div>

    <!-- Main Application -->
    <div id="appSection" class="container hidden">
        <div class="header">
            <h1>📱 Aplikasi Inputan + WhatsApp</h1>
            <p>Input data dengan Cust per Item</p>
        </div>

        <div class="form-section">
            <!-- User Info -->
            <div class="user-info">
                <div>
                    <strong>👤 User:</strong> <span id="currentUser">-</span>
                    <span id="userRole" style="margin-left: 10px; padding: 2px 8px; color: white; border-radius: 10px; font-size: 12px;"></span>
                </div>
                <button class="logout-btn" onclick="logout()">🚪 Logout</button>
            </div>

            <!-- Info Dokumen Saat Ini -->
            <div class="current-doc-info" id="currentDocInfo">
                <strong>📋 Dokumen Saat Ini:</strong> <span id="currentDocId">-</span>
                | <strong>Total Inputan:</strong> <span id="currentItemCount">0</span>
                | <strong>Total Brt:</strong> <span id="currentTotalBrt">0</span>
                | <strong>Total Jumlah:</strong> <span id="currentTotalJumlah">0</span>
                <span id="editModeIndicator" class="hidden" style="margin-left: 10px; padding: 2px 8px; background: #ffc107; color: black; border-radius: 10px; font-size: 12px;">✏️ EDIT MODE</span>
            </div>

            <form id="dataForm">
                <div class="form-row">
                    <div class="form-group">
                        <label for="tanggal">📅 Tanggal</label>
                        <input type="date" id="tanggal" required onchange="resetDocumentCounter()">
                    </div>
                    <div class="form-group">
                        <label for="status">🟢 Status</label>
                        <select id="status" required>
                            <option value="Byr">Byr</option>
                            <option value="Tdk">Tdk</option>
                        </select>
                    </div>
                </div>

                <div class="form-row-3">
                    <div class="form-group">
                        <label for="sup">👨‍💼 Sup (3 Char)</label>
                        <input type="text" id="sup" required placeholder="ABC" maxlength="3" class="input-uppercase" oninput="validateSup()">
                        <div class="input-hint">Harus tepat 3 karakter</div>
                        <div class="validation-message" id="supValidation"></div>
                    </div>
                    <div class="form-group">
                        <label for="pic">👤 PIC</label>
                        <select id="pic" required>
                            <option value="Jimmy">Jimmy</option>
                            <option value="Lukas">Lukas</option>
                        </select>
                    </div>
                </div>

                <!-- Multiple Input Items dengan Cust per Item -->
                <div class="input-items">
                    <h3>📥 Input Items (Cust diinput per Item)</h3>
                    
                    <div id="itemsContainer">
                        <!-- Item rows will be added here -->
                    </div>

                    <button type="button" class="btn-add-item" onclick="addItemRow()">
                        ➕ Tambah Item
                    </button>

                    <div class="total-section">
                        <div class="form-row-3">
                            <div>
                                <strong>Total Items:</strong> <span id="totalItems">0</span>
                            </div>
                            <div>
                                <strong>Total Brt:</strong> <span id="totalBrt">0</span>
                            </div>
                            <div>
                                <strong>Total Jumlah:</strong> <span id="totalJumlah">0</span>
                            </div>
                        </div>
                    </div>

                    <!-- Customer Summary -->
                    <div class="customer-summary" id="customerSummary">
                        <strong>📊 Ringkasan per Customer:</strong>
                        <div id="customerSummaryContent">Belum ada data customer</div>
                    </div>
                </div>

                <div class="btn-group">
                    <button type="submit" class="btn-primary" id="submitButton">💾 Simpan Dokumen</button>
                    <button type="button" onclick="clearForm()" class="btn-secondary">🗑️ Clear Form</button>
                    <button type="button" onclick="startNewDocument()" class="btn-secondary" style="background: #17a2b8; color: white;">
                        📄 Dokumen Baru
                    </button>
                    <button type="button" onclick="cancelEdit()" class="btn-secondary hidden" style="background: #dc3545; color: white;" id="cancelEditButton">
                        ❌ Batal Edit
                    </button>
                </div>
            </form>

            <div class="whatsapp-section">
                <h3>📤 Kirim via WhatsApp</h3>
                <div class="form-row">
                    <div class="form-group">
                        <label for="phone">📞 Nomor WhatsApp (dengan kode negara)</label>
                        <input type="tel" id="phone" placeholder="62xxxxxxxxxx" required value="62">
                    </div>
                    <div class="form-group">
                        <label for="customMessage">💬 Pesan Custom</label>
                        <input type="text" id="customMessage" placeholder="Pesan pembuka..." value="📋 DOKUMEN INPUTAN">
                    </div>
                </div>
                
                <div class="btn-group">
                    <button type="button" onclick="sendLastData()" class="btn-whatsapp">
                        📨 Kirim Dokumen Terakhir
                    </button>
                    <button type="button" onclick="sendAllData()" class="btn-whatsapp">
                        📬 Kirim Semua Dokumen
                    </button>
                    <button type="button" onclick="previewMessage()" class="btn-secondary">
                        👁️ Preview Pesan
                    </button>
                </div>
            </div>

            <div class="preview-section">
                <h3>👁️ Preview Dokumen</h3>
                <div class="preview-box" id="previewBox">
                    Dokumen akan muncul di sini setelah Anda mengklik "Preview Pesan"...
                </div>
            </div>
        </div>

        <div class="data-section">
            <h3>💾 Data Tersimpan (Total: <span id="dataCount">0</span>)</h3>
            
            <!-- Search Section HANYA di Data Tersimpan -->
            <div class="search-section">
                <h3>🔍 Pencarian Data Tersimpan</h3>
                <form id="searchForm" class="search-form">
                    <div>
                        <label for="searchDocumentId">Cari ID Dokumen:</label>
                        <input type="text" id="searchDocumentId" placeholder="DOC25120001" class="input-uppercase">
                    </div>
                    <div>
                        <label for="searchSup">Sup:</label>
                        <input type="text" id="searchSup" placeholder="ABC" class="input-uppercase" maxlength="3">
                    </div>
                    <div>
                        <label for="searchCust">Cust:</label>
                        <input type="text" id="searchCust" placeholder="Nama Customer">
                    </div>
                    <div>
                        <button type="button" onclick="searchDocuments()" class="btn-primary">🔍 Cari</button>
                        <button type="button" onclick="clearSearch()" class="btn-secondary">🔄 Reset</button>
                    </div>
                </form>
            </div>

            <div style="overflow-x: auto;">
                <table class="data-table" id="dataTable">
                    <thead>
                        <tr>
                            <th>No</th>
                            <th>ID Dokumen</th>
                            <th>Tanggal</th>
                            <th>Sup</th>
                            <th>Total Items</th>
                            <th>Total Brt</th>
                            <th>Total Jumlah</th>
                            <th>Status</th>
                            <th>PIC</th>
                            <th>User</th>
                            <th>Aksi</th>
                        </tr>
                    </thead>
                    <tbody id="tableBody">
                        <!-- Data akan muncul di sini -->
                    </tbody>
                </table>
            </div>
            
            <div class="btn-group" style="margin-top: 20px;">
                <button onclick="exportData()" class="btn-primary">📊 Export ke CSV</button>
                <button onclick="clearAllData()" class="btn-secondary" style="background: #dc3545; color: white;">
                    🗑️ Hapus Semua Data
                </button>
            </div>
        </div>
    </div>

    <script>
        // Data user yang terdaftar - SEMUA UPPERCASE
        const registeredUsers = {
            'JIMMY': 'JIMMY11',
            'LUKAS': 'LUKAS22', 
            'NANDO': 'NANDO33'
        };

        // User dengan hak akses khusus - HANYA NANDO
        const specialUsers = {
            delete: ['NANDO'],
            edit: ['NANDO']
        };

        // Inisialisasi data dari localStorage
        let dataList = JSON.parse(localStorage.getItem('whatsappData')) || [];
        let documentCounter = {};
        let currentDocument = {
            id: '',
            items: [],
            tanggal: '',
            sup: '',
            pic: 'Jimmy',
            user: '',
            isEditMode: false,
            editIndex: -1
        };

        let currentUser = '';
        let currentSearchResults = [];
        let isSearching = false;
        
        // Initialize document counter
        function initializeDocumentCounter() {
            const today = new Date().toISOString().split('T')[0];
            documentCounter = JSON.parse(localStorage.getItem('documentCounter')) || {};
            
            // Inisialisasi untuk bulan ini jika belum ada
            const currentDate = new Date();
            const year = currentDate.getFullYear().toString().slice(-2);
            const month = (currentDate.getMonth() + 1).toString().padStart(2, '0');
            const monthKey = `${year}${month}`;
            
            if (!documentCounter[monthKey]) {
                documentCounter[monthKey] = 1;
                localStorage.setItem('documentCounter', JSON.stringify(documentCounter));
            }
        }
        
        // Set tanggal default ke hari ini
        document.getElementById('tanggal').valueAsDate = new Date();
        initializeDocumentCounter();
        
        // Reset document counter ketika tanggal diganti
        function resetDocumentCounter() {
            const selectedDate = document.getElementById('tanggal').value;
            const dateObj = new Date(selectedDate);
            const year = dateObj.getFullYear().toString().slice(-2);
            const month = (dateObj.getMonth() + 1).toString().padStart(2, '0');
            const monthKey = `${year}${month}`;
            
            if (!documentCounter[monthKey]) {
                documentCounter[monthKey] = 1;
                localStorage.setItem('documentCounter', JSON.stringify(documentCounter));
            }
            initializeDocument(); // Reset ke dokumen baru
        }
        
        // Login functionality
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const username = document.getElementById('username').value.toUpperCase();
            const password = document.getElementById('password').value;
            
            if (authenticateUser(username, password)) {
                currentUser = username;
                document.getElementById('currentUser').textContent = username;
                updateUserRoleDisplay();
                document.getElementById('loginSection').classList.add('hidden');
                document.getElementById('appSection').classList.remove('hidden');
                document.getElementById('loginError').style.display = 'none';
                initializeDocument();
                showNotification(`✅ Login berhasil! Selamat datang ${username}`, 'success');
            } else {
                document.getElementById('loginError').style.display = 'block';
                document.getElementById('loginError').textContent = '❌ Username atau password salah!';
            }
        });
        
        // Authentication function
        function authenticateUser(username, password) {
            return registeredUsers[username] === password;
        }

        // Update user role display
        function updateUserRoleDisplay() {
            const roleElement = document.getElementById('userRole');
            if (specialUsers.delete.includes(currentUser)) {
                roleElement.textContent = 'Admin';
                roleElement.style.background = '#dc3545';
            } else {
                roleElement.textContent = 'User';
                roleElement.style.background = '#28a745';
            }
        }
        
        // Check if user can delete
        function canDelete() {
            return specialUsers.delete.includes(currentUser);
        }

        // Check if user can edit
        function canEdit() {
            return specialUsers.edit.includes(currentUser);
        }
        
        // Logout function
        function logout() {
            currentUser = '';
            document.getElementById('loginSection').classList.remove('hidden');
            document.getElementById('appSection').classList.add('hidden');
            document.getElementById('loginForm').reset();
            document.getElementById('loginError').style.display = 'none';
        }
        
        // Update counter data
        function updateDataCount() {
            document.getElementById('dataCount').textContent = isSearching ? currentSearchResults.length : dataList.length;
        }
        
        // Generate Document ID dengan format baru: DOCYYMMXXXX
        function generateDocumentId() {
            const tanggal = document.getElementById('tanggal').value;
            const dateObj = new Date(tanggal);
            const year = dateObj.getFullYear().toString().slice(-2);
            const month = (dateObj.getMonth() + 1).toString().padStart(2, '0');
            
            // Buat key berdasarkan tahun dan bulan untuk counter
            const monthKey = `${year}${month}`;
            
            // Get and increment counter for this month
            if (!documentCounter[monthKey]) {
                documentCounter[monthKey] = 1;
            }
            const counter = documentCounter[monthKey]++;
            localStorage.setItem('documentCounter', JSON.stringify(documentCounter));
            
            // Format: DOC + YY + MM + XXXX (4 digit counter)
            return `DOC${year}${month}${counter.toString().padStart(4, '0')}`;
        }
        
        // Initialize new document
        function initializeDocument() {
            currentDocument.id = generateDocumentId();
            currentDocument.items = [];
            currentDocument.tanggal = document.getElementById('tanggal').value;
            currentDocument.sup = '';
            currentDocument.pic = 'Jimmy';
            currentDocument.user = currentUser;
            currentDocument.isEditMode = false;
            currentDocument.editIndex = -1;
            
            updateCurrentDocInfo();
            renderItems();
            addItemRow();
            updateFormMode();
            updateCustomerSummary();
        }
        
        // Start new document
        function startNewDocument() {
            if (currentDocument.items.length > 0 && !confirm('Yakin ingin membuat dokumen baru? Data yang belum disimpan akan hilang.')) {
                return;
            }
            initializeDocument();
            clearForm();
            showNotification('📄 Dokumen baru siap digunakan!', 'success');
        }

        // Update form mode (normal vs edit)
        function updateFormMode() {
            const submitButton = document.getElementById('submitButton');
            const cancelButton = document.getElementById('cancelEditButton');
            const docInfo = document.getElementById('currentDocInfo');
            const editIndicator = document.getElementById('editModeIndicator');

            if (currentDocument.isEditMode) {
                submitButton.textContent = '💾 Update Dokumen';
                cancelButton.classList.remove('hidden');
                docInfo.classList.add('edit-mode');
                editIndicator.classList.remove('hidden');
            } else {
                submitButton.textContent = '💾 Simpan Dokumen';
                cancelButton.classList.add('hidden');
                docInfo.classList.remove('edit-mode');
                editIndicator.classList.add('hidden');
            }
        }

        // Cancel edit mode
        function cancelEdit() {
            if (confirm('Yakin ingin membatalkan edit?')) {
                initializeDocument();
                clearForm();
                showNotification('❌ Edit dibatalkan', 'success');
            }
        }
        
        // Update current document info
        function updateCurrentDocInfo() {
            document.getElementById('currentDocId').textContent = currentDocument.id;
            document.getElementById('currentItemCount').textContent = currentDocument.items.length;
            
            const totalBrt = currentDocument.items.reduce((sum, item) => sum + (parseFloat(item.brt.replace(/,/g, '')) || 0), 0);
            const totalJumlah = currentDocument.items.reduce((sum, item) => sum + (parseFloat(item.jumlah.replace(/,/g, '')) || 0), 0);
            
            document.getElementById('currentTotalBrt').textContent = formatNumber(totalBrt);
            document.getElementById('currentTotalJumlah').textContent = formatNumber(totalJumlah);
        }
        
        // Format number dengan thousand separator
        function formatNumber(num) {
            if (!num && num !== 0) return '0';
            return new Intl.NumberFormat('id-ID').format(parseFloat(num) || 0);
        }
        
        // Parse number dari formatted string
        function parseNumber(str) {
            if (!str) return 0;
            return parseFloat(str.replace(/,/g, '')) || 0;
        }
        
        // Format input dengan thousand separator
        function formatInput(input) {
            const value = input.value.replace(/,/g, '');
            const number = parseFloat(value);
            if (!isNaN(number)) {
                input.value = formatNumber(number);
            }
            updateTotals();
            updateCustomerSummary();
        }

        // Calculate Jumlah automatically - FIXED VERSION
        function calculateJumlah(itemRow) {
            const brtInput = itemRow.querySelector('.item-brt');
            const krsInput = itemRow.querySelector('.item-krs');
            const jumlahInput = itemRow.querySelector('.item-jumlah');
            
            const brt = parseNumber(brtInput.value) || 0;
            const krs = parseNumber(krsInput.value) || 0;
            const jumlah = brt * krs;
            
            jumlahInput.value = formatNumber(jumlah);
            updateTotals();
            updateCustomerSummary();
        }

        // Update customer input
        function updateCustomerInput(input) {
            updateCustomerSummary();
        }
        
        // Add item row
        function addItemRow(itemData = null) {
            const itemId = 'item_' + Date.now() + '_' + Math.random().toString(36).substr(2, 9);
            const itemRow = document.createElement('div');
            itemRow.className = 'item-row';
            
            const custValue = itemData ? itemData.cust : '';
            const brtValue = itemData ? itemData.brt : '';
            const krsValue = itemData ? itemData.krs : '';
            const kursValue = itemData ? itemData.kurs : '';
            const jumlahValue = itemData ? itemData.jumlah : '';
            const caraBayarValue = itemData ? itemData.cara_bayar : 'TT';
            const jenisValue = itemData ? itemData.jenis : 'LD';
            
            itemRow.innerHTML = `
                <div>
                    <label>🏢 Cust *</label>
                    <input type="text" class="item-cust" placeholder="Nama Customer" required
                           value="${custValue}" oninput="updateCustomerInput(this)">
                </div>
                <div>
                    <label>⚖️ Brt *</label>
                    <input type="text" class="input-numeric item-brt" placeholder="0" required
                           value="${brtValue}" onblur="formatInput(this)" oninput="calculateJumlah(this.parentElement.parentElement)">
                </div>
                <div>
                    <label>📋 Krs</label>
                    <input type="text" class="input-numeric item-krs" placeholder="0" 
                           value="${krsValue}" onblur="formatInput(this)" oninput="calculateJumlah(this.parentElement.parentElement)">
                </div>
                <div>
                    <label>💰 Kurs</label>
                    <input type="text" class="input-numeric item-kurs" placeholder="0" 
                           value="${kursValue}" onblur="formatInput(this)">
                </div>
                <div>
                    <label>💰 Jumlah (Brt × Krs)</label>
                    <input type="text" class="input-numeric item-jumlah auto-calculated" placeholder="0" readonly
                           value="${jumlahValue}">
                </div>
                <div>
                    <label>💳 Cara Bayar</label>
                    <select class="item-cara-bayar">
                        <option value="TT" ${caraBayarValue === 'TT' ? 'selected' : ''}>TT</option>
                        <option value="Cash" ${caraBayarValue === 'Cash' ? 'selected' : ''}>Cash</option>
                        <option value="Transfer" ${caraBayarValue === 'Transfer' ? 'selected' : ''}>Transfer</option>
                    </select>
                </div>
                <div>
                    <label>📦 Jenis</label>
                    <select class="item-jenis">
                        <option value="LD" ${jenisValue === 'LD' ? 'selected' : ''}>LD</option>
                        <option value="CTY" ${jenisValue === 'CTY' ? 'selected' : ''}>CTY</option>
                        <option value="LM" ${jenisValue === 'LM' ? 'selected' : ''}>LM</option>
                    </select>
                </div>
                <div class="item-actions">
                    <button type="button" class="btn-remove-item" onclick="removeItemRow('${itemId}')">🗑️</button>
                </div>
            `;
            itemRow.id = itemId;
            document.getElementById('itemsContainer').appendChild(itemRow);
            
            // Trigger calculation for new row
            if (brtValue || krsValue) {
                calculateJumlah(itemRow);
            }
            
            updateTotals();
            updateCustomerSummary();
        }
        
        // Remove item row
        function removeItemRow(id) {
            const element = document.getElementById(id);
            if (element) {
                element.remove();
                updateTotals();
                updateCustomerSummary();
            }
        }
        
        // Render items
        function renderItems(items = []) {
            const container = document.getElementById('itemsContainer');
            container.innerHTML = '';
            
            if (items.length > 0) {
                items.forEach(item => {
                    addItemRow(item);
                });
            } else {
                addItemRow();
            }
            updateTotals();
            updateCustomerSummary();
        }
        
        // Update totals (Brt dan Jumlah)
        function updateTotals() {
            const brtInputs = document.querySelectorAll('.item-brt');
            const jumlahInputs = document.querySelectorAll('.item-jumlah');
            
            let totalBrt = 0;
            let totalJumlah = 0;
            let totalItems = 0;
            
            brtInputs.forEach(input => {
                if (input.value.trim()) {
                    totalBrt += parseNumber(input.value);
                    totalItems++;
                }
            });
            
            jumlahInputs.forEach(input => {
                if (input.value.trim()) {
                    totalJumlah += parseNumber(input.value);
                }
            });
            
            document.getElementById('totalItems').textContent = totalItems;
            document.getElementById('totalBrt').textContent = formatNumber(totalBrt);
            document.getElementById('totalJumlah').textContent = formatNumber(totalJumlah);
            
            updateCurrentDocInfo();
        }

        // Update customer summary
        function updateCustomerSummary() {
            const custInputs = document.querySelectorAll('.item-cust');
            const brtInputs = document.querySelectorAll('.item-brt');
            const jumlahInputs = document.querySelectorAll('.item-jumlah');
            
            const customerData = {};
            
            // Group by customer
            custInputs.forEach((custInput, index) => {
                const customer = custInput.value.trim();
                const brt = brtInputs[index] ? parseNumber(brtInputs[index].value) : 0;
                const jumlah = jumlahInputs[index] ? parseNumber(jumlahInputs[index].value) : 0;
                
                if (customer && (brt > 0 || jumlah > 0)) {
                    if (!customerData[customer]) {
                        customerData[customer] = { brt: 0, jumlah: 0 };
                    }
                    customerData[customer].brt += brt;
                    customerData[customer].jumlah += jumlah;
                }
            });
            
            // Update summary display
            const summaryContent = document.getElementById('customerSummaryContent');
            if (Object.keys(customerData).length === 0) {
                summaryContent.innerHTML = 'Belum ada data customer';
            } else {
                let summaryHTML = '';
                Object.keys(customerData).forEach(customer => {
                    summaryHTML += `<div>• ${customer}: ${formatNumber(customerData[customer].brt)} Brt | ${formatNumber(customerData[customer].jumlah)} Jumlah</div>`;
                });
                summaryContent.innerHTML = summaryHTML;
            }
        }
        
        // Event listener untuk form submit - FIXED VERSION
        document.getElementById('dataForm').addEventListener('submit', function(e) {
            e.preventDefault();
            if (currentDocument.isEditMode) {
                updateData();
            } else {
                saveData();
            }
        });
        
        // Validasi Sup
        function validateSup() {
            const supInput = document.getElementById('sup');
            const validationMsg = document.getElementById('supValidation');
            const supValue = supInput.value.trim().toUpperCase();
            
            if (supValue.length !== 3) {
                supInput.classList.add('validation-error');
                validationMsg.textContent = 'Sup harus tepat 3 karakter!';
                return false;
            } else {
                supInput.classList.remove('validation-error');
                validationMsg.textContent = '';
                return true;
            }
        }
        
        // Validasi input
        function validateInputs() {
            const sup = document.getElementById('sup').value.trim().toUpperCase();
            
            // Validasi Sup (3 karakter)
            if (!validateSup()) {
                showNotification('❌ Sup harus tepat 3 karakter!', 'error');
                return false;
            }
            
            // Validasi minimal 1 item dengan Brt dan Cust
            const brtInputs = document.querySelectorAll('.item-brt');
            const custInputs = document.querySelectorAll('.item-cust');
            let hasValidItem = false;
            
            brtInputs.forEach((input, index) => {
                const brt = input.value.trim();
                const cust = custInputs[index].value.trim();
                if (brt && cust) {
                    hasValidItem = true;
                }
            });
            
            if (!hasValidItem) {
                showNotification('❌ Minimal harus ada 1 item dengan nilai Brt dan Customer!', 'error');
                return false;
            }
            
            return true;
        }
        
        // Fungsi simpan data baru - FIXED VERSION
        function saveData() {
            if (!validateInputs()) {
                return;
            }
            
            const tanggal = document.getElementById('tanggal').value;
            const sup = document.getElementById('sup').value.trim().toUpperCase();
            const status = document.getElementById('status').value;
            const pic = document.getElementById('pic').value;
            
            // Collect items
            const items = [];
            const itemRows = document.querySelectorAll('.item-row');
            
            itemRows.forEach(row => {
                const cust = row.querySelector('.item-cust').value.trim();
                const brt = row.querySelector('.item-brt').value;
                const krs = row.querySelector('.item-krs').value;
                const kurs = row.querySelector('.item-kurs').value;
                const jumlah = row.querySelector('.item-jumlah').value;
                const cara_bayar = row.querySelector('.item-cara-bayar').value;
                const jenis = row.querySelector('.item-jenis').value;
                
                if (cust && brt.trim()) {
                    items.push({
                        cust: cust,
                        brt: brt,
                        krs: krs || '0',
                        kurs: kurs || '0',
                        jumlah: jumlah || '0',
                        cara_bayar: cara_bayar,
                        jenis: jenis
                    });
                }
            });
            
            const totalBrt = parseNumber(document.getElementById('totalBrt').textContent);
            const totalJumlah = parseNumber(document.getElementById('totalJumlah').textContent);
            
            const data = {
                documentId: currentDocument.id,
                tanggal: formatDate(tanggal),
                sup,
                status,
                pic,
                user: currentUser,
                items: items,
                totalBrt: totalBrt,
                totalJumlah: totalJumlah,
                itemCount: items.length,
                timestamp: new Date().getTime()
            };
            
            console.log('Data yang akan disimpan:', data); // Debug log
            
            dataList.push(data);
            localStorage.setItem('whatsappData', JSON.stringify(dataList));
            updateTable();
            showNotification(`✅ Dokumen ${currentDocument.id} berhasil disimpan! (${items.length} items)`, 'success');
            
            // Auto preview dokumen terakhir
            setTimeout(() => previewLastDocument(), 500);
            
            // Start new document after save
            setTimeout(() => {
                initializeDocument();
                clearForm();
            }, 1000);
        }

        // Fungsi update data yang sudah ada - FIXED VERSION
        function updateData() {
            if (!validateInputs()) {
                return;
            }

            if (!canEdit()) {
                showNotification('❌ Anda tidak memiliki akses untuk mengedit dokumen!', 'error');
                return;
            }
            
            const tanggal = document.getElementById('tanggal').value;
            const sup = document.getElementById('sup').value.trim().toUpperCase();
            const status = document.getElementById('status').value;
            const pic = document.getElementById('pic').value;
            
            // Collect items
            const items = [];
            const itemRows = document.querySelectorAll('.item-row');
            
            itemRows.forEach(row => {
                const cust = row.querySelector('.item-cust').value.trim();
                const brt = row.querySelector('.item-brt').value;
                const krs = row.querySelector('.item-krs').value;
                const kurs = row.querySelector('.item-kurs').value;
                const jumlah = row.querySelector('.item-jumlah').value;
                const cara_bayar = row.querySelector('.item-cara-bayar').value;
                const jenis = row.querySelector('.item-jenis').value;
                
                if (cust && brt.trim()) {
                    items.push({
                        cust: cust,
                        brt: brt,
                        krs: krs || '0',
                        kurs: kurs || '0',
                        jumlah: jumlah || '0',
                        cara_bayar: cara_bayar,
                        jenis: jenis
                    });
                }
            });
            
            const totalBrt = parseNumber(document.getElementById('totalBrt').textContent);
            const totalJumlah = parseNumber(document.getElementById('totalJumlah').textContent);
            
            const updatedData = {
                documentId: currentDocument.id,
                tanggal: formatDate(tanggal),
                sup,
                status,
                pic,
                user: dataList[currentDocument.editIndex].user, // Tetap user original
                items: items,
                totalBrt: totalBrt,
                totalJumlah: totalJumlah,
                itemCount: items.length,
                timestamp: dataList[currentDocument.editIndex].timestamp // Tetap timestamp original
            };
            
            console.log('Data yang akan diupdate:', updatedData); // Debug log
            
            dataList[currentDocument.editIndex] = updatedData;
            localStorage.setItem('whatsappData', JSON.stringify(dataList));
            updateTable();
            showNotification(`✅ Dokumen ${currentDocument.id} berhasil diupdate! (${items.length} items)`, 'success');
            
            // Kembali ke mode normal
            initializeDocument();
            clearForm();
        }
        
        // Format tanggal ke format Indonesia
        function formatDate(dateString) {
            const date = new Date(dateString);
            return date.toLocaleDateString('id-ID', {
                day: '2-digit',
                month: '2-digit',
                year: 'numeric'
            });
        }
        
        // Clear form input
        function clearForm() {
            document.getElementById('sup').value = '';
            document.getElementById('status').value = 'Byr';
            document.getElementById('pic').value = 'Jimmy';
            document.getElementById('tanggal').valueAsDate = new Date();
            
            // Clear validation
            document.getElementById('sup').classList.remove('validation-error');
            document.getElementById('supValidation').textContent = '';
            
            renderItems();
        }

        // Search documents - HANYA di Data Tersimpan
        function searchDocuments() {
            const searchDocId = document.getElementById('searchDocumentId').value.trim().toUpperCase();
            const searchSup = document.getElementById('searchSup').value.trim().toUpperCase();
            const searchCust = document.getElementById('searchCust').value.trim().toLowerCase();
            
            currentSearchResults = dataList.filter(doc => {
                const matchDocId = !searchDocId || doc.documentId.includes(searchDocId);
                const matchSup = !searchSup || doc.sup.includes(searchSup);
                const matchCust = !searchCust || doc.items.some(item => 
                    item.cust.toLowerCase().includes(searchCust)
                );
                
                return matchDocId && matchSup && matchCust;
            });
            
            isSearching = true;
            updateTable();
            showNotification(`🔍 Ditemukan ${currentSearchResults.length} dokumen`, 'success');
        }

        // Clear search
        function clearSearch() {
            document.getElementById('searchDocumentId').value = '';
            document.getElementById('searchSup').value = '';
            document.getElementById('searchCust').value = '';
            isSearching = false;
            updateTable();
            showNotification('🔄 Pencarian direset', 'success');
        }
        
        // Update tabel data dengan nomor urut reset
        function updateTable() {
            const tableBody = document.getElementById('tableBody');
            tableBody.innerHTML = '';
            
            const displayData = isSearching ? currentSearchResults : dataList;
            
            // Sort data berdasarkan timestamp (terbaru di atas)
            const sortedData = [...displayData].sort((a, b) => b.timestamp - a.timestamp);
            
            sortedData.forEach((data, index) => {
                const row = document.createElement('tr');
                
                // Tombol aksi berdasarkan hak akses
                let actionButtons = `
                    <button class="action-btn btn-send-single" onclick="sendSingleData(${isSearching ? currentSearchResults.indexOf(data) : dataList.indexOf(data)})" title="Kirim dokumen ini via WhatsApp">
                        📨
                    </button>`;
                
                // Hanya NANDO yang bisa hapus dan edit
                if (canDelete()) {
                    actionButtons += `
                        <button class="action-btn btn-delete" onclick="deleteData(${isSearching ? currentSearchResults.indexOf(data) : dataList.indexOf(data)})" title="Hapus dokumen ini">
                            🗑️
                        </button>`;
                }
                
                if (canEdit()) {
                    actionButtons += `
                        <button class="action-btn btn-edit" onclick="editData(${isSearching ? currentSearchResults.indexOf(data) : dataList.indexOf(data)})" title="Edit dokumen ini">
                            ✏️
                        </button>`;
                }
                
                // Nomor urut selalu dari 1
                row.innerHTML = `
                    <td>${index + 1}</td>
                    <td class="document-id">${data.documentId}</td>
                    <td>${data.tanggal}</td>
                    <td><strong>${data.sup}</strong></td>
                    <td>${data.itemCount} items</td>
                    <td>${formatNumber(data.totalBrt)}</td>
                    <td>${formatNumber(data.totalJumlah)}</td>
                    <td>${data.status}</td>
                    <td>${data.pic}</td>
                    <td>${data.user}</td>
                    <td>${actionButtons}</td>
                `;
                tableBody.appendChild(row);
            });
            
            updateDataCount();
        }

        // Edit data - FIXED VERSION
        function editData(index) {
            if (!canEdit()) {
                showNotification('❌ Anda tidak memiliki akses untuk mengedit dokumen!', 'error');
                return;
            }

            const data = isSearching ? currentSearchResults[index] : dataList[index];
            
            // Set current document untuk edit mode
            currentDocument.id = data.documentId;
            currentDocument.isEditMode = true;
            currentDocument.editIndex = isSearching ? dataList.indexOf(data) : index;
            
            // Isi form dengan data yang akan diedit
            document.getElementById('tanggal').value = data.tanggal.split('/').reverse().join('-');
            document.getElementById('sup').value = data.sup;
            document.getElementById('status').value = data.status;
            document.getElementById('pic').value = data.pic;
            
            // Render items
            renderItems(data.items);
            
            updateFormMode();
            showNotification(`✏️ Edit mode untuk dokumen ${data.documentId}`, 'success');
        }
        
        // Format dokumen untuk single data
        function formatDocument(data) {
            let message = `📋 DOKUMEN: ${data.documentId}
━━━━━━━━━━━━━━━━━━━━━━
📅 TANGGAL    : ${data.tanggal}
👨‍💼 SUP       : ${data.sup}
👤 PIC        : ${data.pic}
🟢 STATUS     : ${data.status}
👤 USER       : ${data.user}

📊 ITEMS (${data.itemCount}):\n`;

            // Group items by customer
            const itemsByCustomer = {};
            data.items.forEach(item => {
                if (!itemsByCustomer[item.cust]) {
                    itemsByCustomer[item.cust] = [];
                }
                itemsByCustomer[item.cust].push(item);
            });

            // Format items by customer
            Object.keys(itemsByCustomer).forEach(customer => {
                message += `\n▬▬▬ ${customer} ▬▬▬\n`;
                itemsByCustomer[customer].forEach((item, index) => {
                    message += `   ${index + 1}. ⚖️ Brt: ${item.brt}`;
                    if (item.krs && item.krs !== '0') {
                        message += ` | 📋 Krs: ${item.krs}`;
                    }
                    if (item.kurs && item.kurs !== '0') {
                        message += ` | 💰 Kurs: ${item.kurs}`;
                    }
                    message += ` | 💰 Jumlah: ${item.jumlah}`;
                    message += ` | 💳 ${item.cara_bayar}`;
                    message += ` | 📦 ${item.jenis}`;
                    message += '\n';
                });
            });

            message += `\n💰 TOTAL:\n`;
            message += `   ⚖️ TOTAL BRT: ${formatNumber(data.totalBrt)}\n`;
            message += `   💰 TOTAL JUMLAH: ${formatNumber(data.totalJumlah)}\n`;
            message += `────────────────────\n`;
            message += `_Generated by DocApp_`;

            return message;
        }
        
        // Format dokumen untuk semua data
        function formatAllDocuments() {
            if (dataList.length === 0) return 'Belum ada dokumen yang tersimpan.';
            
            let message = '📊 LAPORAN DOKUMEN INPUTAN\n\n';
            message += `Total Dokumen: ${dataList.length}\n`;
            message += `Tanggal Cetak: ${new Date().toLocaleDateString('id-ID')}\n\n`;
            
            // Sort by timestamp descending untuk tampilkan terbaru pertama
            const sortedData = [...dataList].sort((a, b) => b.timestamp - a.timestamp);
            
            sortedData.forEach((data, index) => {
                message += `▬▬▬ DOKUMEN ${data.documentId} ▬▬▬\n`;
                message += `📅 Tanggal : ${data.tanggal}\n`;
                message += `👨‍💼 Sup     : ${data.sup}\n`;
                message += `👤 PIC      : ${data.pic}\n`;
                message += `🟢 Status   : ${data.status}\n`;
                message += `👤 User     : ${data.user}\n`;
                message += `📦 Items    : ${data.itemCount}\n`;
                message += `⚖️ Total Brt: ${formatNumber(data.totalBrt)}\n`;
                message += `💰 Total Jml: ${formatNumber(data.totalJumlah)}\n\n`;
            });
            
            message += '────────────────────\n';
            message += '_Generated by DocApp_';
            return message;
        }
        
        // Preview dokumen terakhir
        function previewLastDocument() {
            if (dataList.length === 0) return;
            
            const lastData = dataList[dataList.length - 1];
            const customMessage = document.getElementById('customMessage').value;
            const message = `${customMessage}\n\n${formatDocument(lastData)}`;
            
            document.getElementById('previewBox').textContent = message;
        }
        
        // Kirim data terakhir
        function sendLastData() {
            if (dataList.length === 0) {
                showNotification('❌ Belum ada dokumen yang disimpan!', 'error');
                return;
            }
            
            const phone = document.getElementById('phone').value.trim();
            if (!phone) {
                showNotification('❌ Nomor WhatsApp harus diisi!', 'error');
                return;
            }
            
            const customMessage = document.getElementById('customMessage').value;
            const lastData = dataList[dataList.length - 1];
            const message = `${customMessage}\n\n${formatDocument(lastData)}`;
            
            sendWhatsApp(phone, message);
        }
        
        // Kirim semua data
        function sendAllData() {
            if (dataList.length === 0) {
                showNotification('❌ Belum ada dokumen yang disimpan!', 'error');
                return;
            }
            
            const phone = document.getElementById('phone').value.trim();
            if (!phone) {
                showNotification('❌ Nomor WhatsApp harus diisi!', 'error');
                return;
            }
            
            const customMessage = document.getElementById('customMessage').value;
            const allDataMessage = formatAllDocuments();
            const message = `${customMessage}\n\n${allDataMessage}`;
            
            sendWhatsApp(phone, message);
        }
        
        // Kirim single data by index
        function sendSingleData(index) {
            const phone = document.getElementById('phone').value.trim();
            if (!phone) {
                showNotification('❌ Nomor WhatsApp harus diisi!', 'error');
                return;
            }
            
            const customMessage = document.getElementById('customMessage').value;
            const data = isSearching ? currentSearchResults[index] : dataList[index];
            const message = `${customMessage}\n\n${formatDocument(data)}`;
            
            sendWhatsApp(phone, message);
        }
        
        // Fungsi utama kirim WhatsApp
        function sendWhatsApp(phone, message) {
            const formattedPhone = phone.replace(/\D/g, '');
            
            if (formattedPhone.length < 10) {
                showNotification('❌ Format nomor WhatsApp tidak valid!', 'error');
                return;
            }
            
            const encodedMessage = encodeURIComponent(message);
            const waUrl = `https://wa.me/${formattedPhone}?text=${encodedMessage}`;
            
            window.open(waUrl, '_blank');
            showNotification('📱 Membuka WhatsApp...', 'success');
        }
        
        // Preview pesan
        function previewMessage() {
            if (dataList.length === 0) {
                showNotification('❌ Belum ada dokumen yang disimpan!', 'error');
                return;
            }
            
            const customMessage = document.getElementById('customMessage').value;
            let message;
            
            if (dataList.length === 1) {
                message = `${customMessage}\n\n${formatDocument(dataList[0])}`;
            } else {
                message = `${customMessage}\n\n${formatAllDocuments()}`;
            }
            
            document.getElementById('previewBox').textContent = message;
            showNotification('👁️ Preview dokumen diperbarui!', 'success');
        }
        
        // Hapus data
        function deleteData(index) {
            if (!canDelete()) {
                showNotification('❌ Anda tidak memiliki akses untuk menghapus dokumen!', 'error');
                return;
            }

            const data = isSearching ? currentSearchResults[index] : dataList[index];
            
            if (confirm(`Yakin ingin menghapus dokumen ${data.documentId}?`)) {
                const actualIndex = isSearching ? dataList.indexOf(data) : index;
                dataList.splice(actualIndex, 1);
                localStorage.setItem('whatsappData', JSON.stringify(dataList));
                updateTable();
                showNotification('✅ Dokumen berhasil dihapus!', 'success');
            }
        }
        
        // Hapus semua data
        function clearAllData() {
            if (!canDelete()) {
                showNotification('❌ Anda tidak memiliki akses untuk menghapus semua data!', 'error');
                return;
            }

            if (dataList.length === 0) {
                showNotification('❌ Tidak ada dokumen untuk dihapus!', 'error');
                return;
            }
            
            if (confirm(`Yakin ingin menghapus SEMUA dokumen (${dataList.length} dokumen)?`)) {
                dataList = [];
                localStorage.removeItem('whatsappData');
                localStorage.removeItem('documentCounter');
                documentCounter = {};
                updateTable();
                showNotification('✅ Semua dokumen berhasil dihapus!', 'success');
            }
        }
        
        // Export data ke CSV dengan detail per item
        function exportData() {
            if (dataList.length === 0) {
                showNotification('❌ Tidak ada data untuk diexport!', 'error');
                return;
            }
            
            let csv = 'No,ID Dokumen,Tanggal,Sup,Status,PIC,User,Customer,Brt,Krs,Kurs,Jumlah,Cara Bayar,Jenis\n';
            
            dataList.forEach((data, docIndex) => {
                data.items.forEach((item, itemIndex) => {
                    csv += `"${docIndex + 1}","${data.documentId}","${data.tanggal}","${data.sup}","${data.status}","${data.pic}","${data.user}","${item.cust}","${item.brt}","${item.krs}","${item.kurs}","${item.jumlah}","${item.cara_bayar}","${item.jenis}"\n`;
                });
            });
            
            const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
            const url = URL.createObjectURL(blob);
            const link = document.createElement('a');
            link.href = url;
            link.setAttribute('download', `detail_inputan_${new Date().toISOString().slice(0,10)}.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            
            showNotification('📊 Data detail berhasil diexport!', 'success');
        }
        
        // Show notification
        function showNotification(message, type) {
            const notification = document.createElement('div');
            notification.className = `notification ${type}`;
            notification.textContent = message;
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.classList.add('show');
            }, 100);
            
            setTimeout(() => {
                notification.classList.remove('show');
                setTimeout(() => {
                    document.body.removeChild(notification);
                }, 300);
            }, 3000);
        }
        
        // Initialize aplikasi
        document.addEventListener('DOMContentLoaded', function() {
            updateTable();
        });
    </script>
</body>
</html>
