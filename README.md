<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="theme-color" content="#1a3a6b">
    <title>Admin · F AND TRIPLE D ACADEMY</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #f0f2f5;
            --card-bg: #ffffff;
            --text-main: #050505;
            --text-muted: #52565c;
            --accent-color: #1a3a6b;
            --accent-hover: #0f2547;
            --accent-soft: rgba(26, 58, 107, 0.1);
            --border-color: #ced0d4;
            --input-bg: #f0f2f5;
            --success: #2e7d32;
            --danger: #c62828;
            --radius: 14px;
        }

        [data-theme="dark"] {
            --bg-color: #18191a;
            --card-bg: #242526;
            --text-main: #e4e6eb;
            --text-muted: #c4c7cc;
            --accent-color: #7aa3e0;
            --accent-hover: #9bbce8;
            --accent-soft: rgba(122, 163, 224, 0.15);
            --border-color: #3e4042;
            --input-bg: #3a3b3c;
        }

        * {
            margin: 0; padding: 0; box-sizing: border-box;
            font-family: 'Poppins', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            min-height: 100vh;
            transition: background-color 0.3s, color 0.3s;
        }

        .container { max-width: 600px; margin: 0 auto; padding: 20px 14px 60px; }

        /* HEADER */
        .admin-header {
            display: flex; justify-content: space-between; align-items: center;
            margin-bottom: 20px;
        }
        .admin-header .brand { display: flex; align-items: center; gap: 10px; }
        .admin-header .brand-logo {
            width: 36px; height: 36px; border-radius: 50%;
            object-fit: cover; border: 2px solid var(--accent-color);
        }
        .admin-header .brand-text {
            font-size: 0.85rem; font-weight: 800;
            color: var(--accent-color); text-transform: uppercase; letter-spacing: 0.4px;
        }
        .admin-header .back-btn {
            background-color: var(--input-bg); border: 1px solid var(--border-color);
            color: var(--text-main); padding: 8px 14px; border-radius: 20px;
            font-family: inherit; font-size: 0.78rem; font-weight: 600;
            cursor: pointer; text-decoration: none; display: inline-block;
        }
        .admin-header .back-btn:hover { background-color: var(--border-color); }

        /* TABS */
        .tabs {
            display: flex; gap: 6px; overflow-x: auto;
            padding-bottom: 14px; margin-bottom: 6px; scrollbar-width: none;
        }
        .tabs::-webkit-scrollbar { display: none; }
        .tab {
            flex-shrink: 0; padding: 9px 16px; border-radius: 20px;
            border: 1px solid var(--border-color); background-color: var(--card-bg);
            color: var(--text-muted); font-size: 0.78rem; font-weight: 600;
            font-family: inherit; cursor: pointer; transition: all 0.2s;
        }
        .tab.active { background-color: var(--accent-color); color: white; border-color: var(--accent-color); }
        .tab-panel { display: none; }
        .tab-panel.active { display: block; animation: fadeIn 0.25s ease; }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(6px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* FORM */
        .form-card {
            background-color: var(--card-bg); border-radius: var(--radius);
            padding: 20px 18px; border: 1px solid var(--border-color);
            box-shadow: 0 1px 3px rgba(0,0,0,0.04); margin-bottom: 16px;
        }
        .form-card h2 {
            font-size: 1rem; font-weight: 700; color: var(--accent-color); margin-bottom: 4px;
        }
        .form-card .form-desc { font-size: 0.78rem; color: var(--text-muted); margin-bottom: 16px; }
        .form-group { margin-bottom: 14px; }
        .form-group label {
            display: block; font-size: 0.78rem; font-weight: 600;
            margin-bottom: 5px; color: var(--text-main);
        }
        .form-group label .required { color: var(--danger); margin-left: 2px; }
        .form-group input, .form-group textarea, .form-group select {
            width: 100%; padding: 11px 13px; border-radius: 10px;
            border: 1px solid var(--border-color); background-color: var(--input-bg);
            color: var(--text-main); font-family: inherit; font-size: 0.9rem;
            outline: none; transition: border-color 0.2s;
        }
        .form-group input:focus, .form-group textarea:focus, .form-group select:focus {
            border-color: var(--accent-color);
        }
        .form-group textarea { resize: vertical; min-height: 80px; line-height: 1.5; }

        .submit-btn {
            width: 100%; padding: 13px; border-radius: 10px; border: none;
            background-color: var(--accent-color); color: white;
            font-family: inherit; font-size: 0.92rem; font-weight: 600;
            cursor: pointer; transition: background-color 0.2s, transform 0.1s; margin-top: 6px;
        }
        .submit-btn:hover { background-color: var(--accent-hover); }
        .submit-btn:active { transform: scale(0.98); }
        .submit-btn:disabled { opacity: 0.6; cursor: not-allowed; }

        .status-msg {
            margin-top: 14px; padding: 10px 14px; border-radius: 10px;
            font-size: 0.85rem; display: none; text-align: center; font-weight: 500;
        }
        .status-msg.success {
            background-color: rgba(46, 125, 50, 0.1); color: var(--success);
            border: 1px solid var(--success); display: block;
        }
        .status-msg.error {
            background-color: rgba(198, 40, 40, 0.1); color: var(--danger);
            border: 1px solid var(--danger); display: block;
        }

        .info-note {
            background-color: var(--accent-soft); border-left: 3px solid var(--accent-color);
            padding: 10px 14px; border-radius: 8px; font-size: 0.78rem;
            color: var(--text-muted); margin-top: 16px; line-height: 1.5;
        }

        /* ENTRIES LIST */
        .entries-card {
            background-color: var(--card-bg); border-radius: var(--radius);
            padding: 18px; border: 1px solid var(--border-color);
            box-shadow: 0 1px 3px rgba(0,0,0,0.04);
        }
        .entries-header {
            display: flex; justify-content: space-between; align-items: center;
            margin-bottom: 12px;
        }
        .entries-header h3 {
            font-size: 0.9rem; font-weight: 700; color: var(--text-main);
        }
        .entries-header .count {
            font-size: 0.72rem; font-weight: 600; color: var(--text-muted);
            background-color: var(--input-bg); padding: 3px 10px; border-radius: 12px;
        }
        .entries-header .refresh-btn {
            background: none; border: none; color: var(--accent-color);
            font-family: inherit; font-size: 0.75rem; font-weight: 600;
            cursor: pointer; padding: 4px 8px; border-radius: 6px;
        }
        .entries-header .refresh-btn:hover { background-color: var(--accent-soft); }
        .entries-header .refresh-btn:disabled { opacity: 0.5; cursor: not-allowed; }

        .entries-list { display: flex; flex-direction: column; gap: 8px; }

        .entry-row {
            display: flex; align-items: center; gap: 10px;
            padding: 10px 12px; border-radius: 10px;
            background-color: var(--input-bg); border: 1px solid transparent;
            transition: border-color 0.2s;
        }
        .entry-row:hover { border-color: var(--border-color); }

        .entry-info { flex: 1; min-width: 0; }
        .entry-main {
            font-size: 0.85rem; font-weight: 500; color: var(--text-main);
            overflow: hidden; text-overflow: ellipsis; white-space: nowrap;
        }
        .entry-meta {
            font-size: 0.7rem; color: var(--text-muted); margin-top: 2px;
        }

        .entry-delete {
            flex-shrink: 0; background: none; border: none; cursor: pointer;
            font-size: 1rem; padding: 6px 8px; border-radius: 8px;
            color: var(--text-muted); transition: all 0.2s;
        }
        .entry-delete:hover {
            background-color: rgba(198, 40, 40, 0.1); color: var(--danger);
        }
        .entry-delete:disabled { opacity: 0.4; cursor: not-allowed; }

        .entries-empty {
            text-align: center; padding: 24px 12px;
            font-size: 0.8rem; color: var(--text-muted);
        }

        .entries-loading {
            text-align: center; padding: 20px;
            font-size: 0.8rem; color: var(--text-muted);
        }
        .entries-loading .spinner {
            display: inline-block; width: 16px; height: 16px;
            border: 2px solid var(--border-color); border-top-color: var(--accent-color);
            border-radius: 50%; animation: spin 0.7s linear infinite;
            vertical-align: middle; margin-right: 6px;
        }
        @keyframes spin { to { transform: rotate(360deg); } }

        /* CONFIRM MODAL */
        .modal-overlay {
            display: none; position: fixed; inset: 0;
            background: rgba(0, 0, 0, 0.6); z-index: 9999;
            align-items: center; justify-content: center; padding: 20px;
        }
        .modal-overlay.active { display: flex; }
        .modal {
            background-color: var(--card-bg); border-radius: var(--radius);
            padding: 24px 20px; max-width: 340px; width: 100%;
            border: 1px solid var(--border-color);
            animation: modalIn 0.2s ease;
        }
        @keyframes modalIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }
        .modal h3 {
            font-size: 1rem; font-weight: 700; margin-bottom: 8px; color: var(--text-main);
        }
        .modal p {
            font-size: 0.85rem; color: var(--text-muted);
            margin-bottom: 20px; line-height: 1.5;
        }
        .modal-actions { display: flex; gap: 10px; }
        .modal-actions button {
            flex: 1; padding: 11px; border-radius: 10px; border: none;
            font-family: inherit; font-size: 0.88rem; font-weight: 600;
            cursor: pointer; transition: all 0.2s;
        }
        .modal-cancel {
            background-color: var(--input-bg); color: var(--text-main);
            border: 1px solid var(--border-color) !important;
        }
        .modal-cancel:hover { background-color: var(--border-color); }
        .modal-confirm {
            background-color: var(--danger); color: white;
        }
        .modal-confirm:hover { background-color: #a01e1e; }
        .modal-confirm:disabled { opacity: 0.6; cursor: not-allowed; }
    </style>
</head>
<body>

<div class="container">
    <div class="admin-header">
        <div class="brand">
            <img src="https://dl.dropboxusercontent.com/scl/fi/rdej9enx2pnsktjjuviv4/1790280398985.jpg?rlkey=12t90yeb0o50yqfz5ndqomxz3&st=59kxo5d7&dl=1" 
                 alt="Logo" class="brand-logo"
                 onerror="this.style.display='none';">
            <span class="brand-text">Admin Panel</span>
        </div>
        <a href="./index.html" class="back-btn">← Website</a>
    </div>

    <div class="tabs">
        <button class="tab active" onclick="switchTab('updates', this)">Updates</button>
        <button class="tab" onclick="switchTab('words', this)">Words</button>
        <button class="tab" onclick="switchTab('calendar', this)">Calendar</button>
        <button class="tab" onclick="switchTab('hairstyles', this)">Hairstyles</button>
        <button class="tab" onclick="switchTab('roaster', this)">Roaster</button>
    </div>

    <!-- UPDATES -->
    <div id="updatesPanel" class="tab-panel active">
        <div class="form-card">
            <h2>Post a New Update</h2>
            <p class="form-desc">This appears on the Updates feed of the website.</p>
            <form onsubmit="submitForm(event, 'updates')">
                <div class="form-group">
                    <label>Post Text <span class="required">*</span></label>
                    <textarea name="PostText" placeholder="What's happening at school?" required></textarea>
                </div>
                <div class="form-group">
                    <label>Image URL 1</label>
                    <input type="url" name="ImageURL1" placeholder="https://... (optional)">
                </div>
                <div class="form-group">
                    <label>Image URL 2</label>
                    <input type="url" name="ImageURL2" placeholder="https://... (optional)">
                </div>
                <button type="submit" class="submit-btn">📤 Publish Update</button>
                <div class="status-msg"></div>
            </form>
            <div class="info-note">
                💡 Use <strong>Dropbox image links</strong> ending in <code>&amp;dl=1</code> for images to display correctly.
            </div>
        </div>
        <div class="entries-card">
            <div class="entries-header">
                <h3>Existing Posts <span class="count" id="updatesCount">0</span></h3>
                <button class="refresh-btn" onclick="loadAllData(true)">↻ Refresh</button>
            </div>
            <div class="entries-list" id="updatesEntries">
                <div class="entries-loading"><span class="spinner"></span>Loading...</div>
            </div>
        </div>
    </div>

    <!-- WORDS -->
    <div id="wordsPanel" class="tab-panel">
        <div class="form-card">
            <h2>Words of the Week</h2>
            <p class="form-desc">Add a word of the week for the Events tab.</p>
            <form onsubmit="submitForm(event, 'words')">
                <div class="form-group">
                    <label>Week Number <span class="required">*</span></label>
                    <input type="number" name="Week" placeholder="e.g. 1" required min="1" max="20">
                </div>
                <div class="form-group">
                    <label>Word <span class="required">*</span></label>
                    <input type="text" name="Word" placeholder="e.g. Goodness" required>
                </div>
                <button type="submit" class="submit-btn">📤 Save Word</button>
                <div class="status-msg"></div>
            </form>
        </div>
        <div class="entries-card">
            <div class="entries-header">
                <h3>Existing Words <span class="count" id="wordsCount">0</span></h3>
                <button class="refresh-btn" onclick="loadAllData(true)">↻ Refresh</button>
            </div>
            <div class="entries-list" id="wordsEntries">
                <div class="entries-loading"><span class="spinner"></span>Loading...</div>
            </div>
        </div>
    </div>

    <!-- CALENDAR -->
    <div id="calendarPanel" class="tab-panel">
        <div class="form-card">
            <h2>Academic Calendar</h2>
            <p class="form-desc">Add a week to the academic session calendar.</p>
            <form onsubmit="submitForm(event, 'calendar')">
                <div class="form-group">
                    <label>Week Number <span class="required">*</span></label>
                    <input type="number" name="Week" placeholder="e.g. 1" required min="1" max="20">
                </div>
                <div class="form-group">
                    <label>Date Range <span class="required">*</span></label>
                    <input type="text" name="Date" placeholder="e.g. 14th - 18th Sept 2026" required>
                </div>
                <div class="form-group">
                    <label>Activity <span class="required">*</span></label>
                    <input type="text" name="Activity" placeholder="e.g. Teaching / C.A Test / Revision" required>
                </div>
                <button type="submit" class="submit-btn">📤 Save Calendar Entry</button>
                <div class="status-msg"></div>
            </form>
        </div>
        <div class="entries-card">
            <div class="entries-header">
                <h3>Existing Calendar Entries <span class="count" id="calendarCount">0</span></h3>
                <button class="refresh-btn" onclick="loadAllData(true)">↻ Refresh</button>
            </div>
            <div class="entries-list" id="calendarEntries">
                <div class="entries-loading"><span class="spinner"></span>Loading...</div>
            </div>
        </div>
    </div>

    <!-- HAIRSTYLES -->
    <div id="hairstylesPanel" class="tab-panel">
        <div class="form-card">
            <h2>Hairstyles for the Week</h2>
            <p class="form-desc">Add a hairstyle for the Events tab.</p>
            <form onsubmit="submitForm(event, 'hairstyles')">
                <div class="form-group">
                    <label>Week Number <span class="required">*</span></label>
                    <input type="number" name="Week" placeholder="e.g. 1" required min="1" max="20">
                </div>
                <div class="form-group">
                    <label>Hairstyle <span class="required">*</span></label>
                    <input type="text" name="Hairstyle" placeholder="e.g. All Back / Shuku / Suku" required>
                </div>
                <button type="submit" class="submit-btn">📤 Save Hairstyle</button>
                <div class="status-msg"></div>
            </form>
        </div>
        <div class="entries-card">
            <div class="entries-header">
                <h3>Existing Hairstyles <span class="count" id="hairstylesCount">0</span></h3>
                <button class="refresh-btn" onclick="loadAllData(true)">↻ Refresh</button>
            </div>
            <div class="entries-list" id="hairstylesEntries">
                <div class="entries-loading"><span class="spinner"></span>Loading...</div>
            </div>
        </div>
    </div>

    <!-- ROASTER -->
    <div id="roasterPanel" class="tab-panel">
        <div class="form-card">
            <h2>Staff Duty Roaster</h2>
            <p class="form-desc">Assign a teacher to a duty week.</p>
            <form onsubmit="submitForm(event, 'roaster')">
                <div class="form-group">
                    <label>Week Number <span class="required">*</span></label>
                    <input type="number" name="Week" placeholder="e.g. 1" required min="1" max="20">
                </div>
                <div class="form-group">
                    <label>Teacher <span class="required">*</span></label>
                    <input type="text" name="Teacher" placeholder="e.g. JSS (1) Form Teacher" required>
                </div>
                <button type="submit" class="submit-btn">📤 Save Duty Entry</button>
                <div class="status-msg"></div>
            </form>
        </div>
        <div class="entries-card">
            <div class="entries-header">
                <h3>Existing Roaster Entries <span class="count" id="roasterCount">0</span></h3>
                <button class="refresh-btn" onclick="loadAllData(true)">↻ Refresh</button>
            </div>
            <div class="entries-list" id="roasterEntries">
                <div class="entries-loading"><span class="spinner"></span>Loading...</div>
            </div>
        </div>
    </div>
</div>

<!-- CONFIRM DELETE MODAL -->
<div class="modal-overlay" id="deleteModal">
    <div class="modal">
        <h3>Delete this entry?</h3>
        <p id="deleteModalText">This action cannot be undone. The entry will be removed from the website immediately.</p>
        <div class="modal-actions">
            <button class="modal-cancel" onclick="closeDeleteModal()">Cancel</button>
            <button class="modal-confirm" id="deleteConfirmBtn" onclick="confirmDelete()">Delete</button>
        </div>
    </div>
</div>

<script>
/* ============================================================
   CONFIG
   ============================================================ */
const CONFIG = {
    apiUrl: 'https://script.google.com/macros/s/AKfycbyfHevn3f_zqBqWsgn73szoyjvPYRiTxDD5y23XFd-jzAOU-WdEn8iGcTqhMcxwMeSZyg/exec'
};

let allData = { updates: [], calendar: [], words: [], hairstyles: [], roaster: [] };
let pendingDelete = null; // { type, row, preview }

/* ============================================================
   TABS
   ============================================================ */
function switchTab(tabId, element) {
    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
    element.classList.add('active');
    document.querySelectorAll('.tab-panel').forEach(p => p.classList.remove('active'));
    const panel = document.getElementById(tabId + 'Panel');
    if (panel) panel.classList.add('active');
}

/* ============================================================
   LOAD DATA
   ============================================================ */
async function loadAllData(showFeedback = false) {
    const containerIds = ['updates', 'words', 'calendar', 'hairstyles', 'roaster'];
    
    // Show loading state in all lists
    containerIds.forEach(type => {
        const el = document.getElementById(type + 'Entries');
        if (el) el.innerHTML = '<div class="entries-loading"><span class="spinner"></span>Loading...</div>';
    });

    try {
        const response = await fetch(CONFIG.apiUrl + '?t=' + Date.now(), { cache: 'no-cache' });
        if (!response.ok) throw new Error('HTTP ' + response.status);
        allData = await response.json();
        renderAllEntries();
        
        if (showFeedback) {
            // Brief visual confirmation of refresh
            document.querySelectorAll('.refresh-btn').forEach(btn => {
                const orig = btn.textContent;
                btn.textContent = '✅';
                setTimeout(() => { btn.textContent = orig; }, 1000);
            });
        }
    } catch (err) {
        console.error('Load error:', err);
        containerIds.forEach(type => {
            const el = document.getElementById(type + 'Entries');
            if (el) el.innerHTML = '<div class="entries-empty">⚠️ Could not load. Check connection.</div>';
        });
    }
}

/* ============================================================
   RENDER ENTRIES
   ============================================================ */
function renderAllEntries() {
    renderEntries('updates', allData.updates || [], item => ({
        main: item.PostText || '(no text)',
        meta: `Row ${item._row}${item.Date ? ' • ' + formatDate(item.Date) : ''}`
    }));

    renderEntries('words', allData.words || [], item => ({
        main: `Week ${item.Week}: ${item.Word || ''}`,
        meta: `Row ${item._row}`
    }));

    renderEntries('calendar', allData.calendar || [], item => ({
        main: `Week ${item.Week}: ${item.Activity || ''}`,
        meta: `Row ${item._row}${item.Date ? ' • ' + item.Date : ''}`
    }));

    renderEntries('hairstyles', allData.hairstyles || [], item => ({
        main: `Week ${item.Week}: ${item.Hairstyle || ''}`,
        meta: `Row ${item._row}`
    }));

    renderEntries('roaster', allData.roaster || [], item => ({
        main: `Week ${item.Week}: ${item.Teacher || ''}`,
        meta: `Row ${item._row}`
    }));
}

function renderEntries(type, items, mapper) {
    const listEl = document.getElementById(type + 'Entries');
    const countEl = document.getElementById(type + 'Count');
    if (!listEl) return;
    if (countEl) countEl.textContent = items.length;

    if (items.length === 0) {
        listEl.innerHTML = '<div class="entries-empty">No entries yet. Use the form above to add one.</div>';
        return;
    }

    // Show newest at the top
    const reversed = [...items].reverse();

    listEl.innerHTML = reversed.map(item => {
        const { main, meta } = mapper(item);
        return `
            <div class="entry-row">
                <div class="entry-info">
                    <div class="entry-main" title="${escapeHtml(main)}">${escapeHtml(main)}</div>
                    <div class="entry-meta">${escapeHtml(meta)}</div>
                </div>
                <button class="entry-delete" 
                        onclick="requestDelete('${type}', ${item._row}, '${escapeJs(main)}')"
                        title="Delete this entry">🗑️</button>
            </div>
        `;
    }).join('');
}

/* ============================================================
   DELETE
   ============================================================ */
function requestDelete(type, row, preview) {
    pendingDelete = { type, row, preview };
    document.getElementById('deleteModalText').innerHTML = 
        `This action cannot be undone. The entry will be removed from the website immediately.<br><br>
         <strong>Entry:</strong> ${escapeHtml(preview)}`;
    document.getElementById('deleteModal').classList.add('active');
}

function closeDeleteModal() {
    pendingDelete = null;
    document.getElementById('deleteModal').classList.remove('active');
}

async function confirmDelete() {
    if (!pendingDelete) return;
    const btn = document.getElementById('deleteConfirmBtn');
    btn.disabled = true;
    btn.textContent = 'Deleting...';

    try {
        const response = await fetch(CONFIG.apiUrl, {
            method: 'POST',
            headers: { 'Content-Type': 'text/plain;charset=utf-8' },
            body: JSON.stringify({
                action: 'delete',
                type: pendingDelete.type,
                row: pendingDelete.row
            })
        });
        const result = await response.json();
        if (result.status !== 'success') {
            throw new Error(result.message || 'Delete failed');
        }
        // Reload fresh data
        await loadAllData();
    } catch (err) {
        console.error('Delete error:', err);
        alert('❌ Failed to delete: ' + err.message);
    } finally {
        btn.disabled = false;
        btn.textContent = 'Delete';
        closeDeleteModal();
    }
}

/* ============================================================
   SUBMIT NEW ENTRY
   ============================================================ */
async function submitForm(event, type) {
    event.preventDefault();
    const form = event.target;
    const btn = form.querySelector('.submit-btn');
    const status = form.querySelector('.status-msg');
    const originalBtnText = btn.textContent;

    const data = {};
    new FormData(form).forEach((value, key) => { data[key] = value.trim(); });

    btn.disabled = true;
    btn.textContent = '⏳ Saving...';
    status.className = 'status-msg';
    status.textContent = '';
    status.style.display = 'none';

    try {
        const response = await fetch(CONFIG.apiUrl, {
            method: 'POST',
            headers: { 'Content-Type': 'text/plain;charset=utf-8' },
            body: JSON.stringify({ action: 'add', type: type, data: data })
        });
        const result = await response.json();
        if (result.status === 'success') {
            status.className = 'status-msg success';
            status.textContent = '✅ Saved! It appears on the website and in the list below.';
            form.reset();
            // Refresh list so the new entry shows up
            await loadAllData();
        } else {
            throw new Error(result.message || 'Server returned an error');
        }
    } catch (err) {
        console.error('Submit error:', err);
        status.className = 'status-msg error';
        status.textContent = '❌ Failed to save. ' + (err.message || 'Check your connection.');
    } finally {
        btn.disabled = false;
        btn.textContent = originalBtnText;
    }
}

/* ============================================================
   HELPERS
   ============================================================ */
function escapeHtml(str) {
    const div = document.createElement('div');
    div.textContent = String(str);
    return div.innerHTML;
}

function escapeJs(str) {
    return String(str)
        .replace(/\\/g, '\\\\')
        .replace(/'/g, "\\'")
        .replace(/"/g, '&quot;')
        .replace(/\n/g, ' ')
        .substring(0, 80);
}

function formatDate(dateStr) {
    try {
        const d = new Date(dateStr);
        if (isNaN(d.getTime())) return dateStr;
        return d.toLocaleDateString('en-GB', { day: 'numeric', month: 'short', year: 'numeric' });
    } catch { return dateStr; }
}

/* ============================================================
   INIT
   ============================================================ */
document.addEventListener('DOMContentLoaded', () => {
    loadAllData();
});

// Close modal when clicking outside it
document.getElementById('deleteModal').addEventListener('click', (e) => {
    if (e.target.id === 'deleteModal') closeDeleteModal();
});
</script>

</body>
</html>
