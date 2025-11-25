# DataCenterDashboard
GCU ITT-640 USER DESIGN INTERFACE ASSIGNMENT
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Data Center Dashboard Prototype</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: Arial, sans-serif;
    }

    body {
      display: flex;
      min-height: 100vh;
      background-color: #f3f4f6;
      color: #111827;
    }

    /* Sidebar navigation */
    .sidebar {
      width: 260px;
      background-color: #111827;
      color: #f9fafb;
      padding: 20px;
      display: flex;
      flex-direction: column;
    }

    .logo {
      font-size: 1.2rem;
      font-weight: bold;
      margin-bottom: 24px;
    }

    .logo span {
      display: block;
      font-size: 0.8rem;
      font-weight: normal;
      color: #9ca3af;
    }

    .nav-section-title {
      font-size: 0.75rem;
      text-transform: uppercase;
      color: #9ca3af;
      margin: 18px 0 6px;
    }

    .nav-link {
      display: block;
      padding: 10px 12px;
      border-radius: 6px;
      color: #e5e7eb;
      text-decoration: none;
      font-size: 0.9rem;
      margin-bottom: 4px;
    }

    .nav-link:hover {
      background-color: #1f2933;
    }

    .nav-link.active {
      background-color: #2563eb;
      color: #ffffff;
    }

    .sidebar-footer {
      margin-top: auto;
      font-size: 0.75rem;
      color: #6b7280;
    }

    /* Main content layout */
    .main {
      flex: 1;
      display: flex;
      flex-direction: column;
    }

    header {
      height: 60px;
      background-color: #ffffff;
      border-bottom: 1px solid #e5e7eb;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 0 24px;
    }

    header .page-title {
      font-weight: 600;
      font-size: 1.1rem;
    }

    header .user-info {
      font-size: 0.85rem;
      color: #4b5563;
    }

    .content {
      flex: 1;
      padding: 24px;
      overflow-y: auto;
    }

    .section {
      display: none;
    }

    .section.visible {
      display: block;
    }

    /* Cards and layout helpers */
    .grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 16px;
    }

    .card {
      background-color: #ffffff;
      border-radius: 10px;
      padding: 16px;
      border: 1px solid #e5e7eb;
    }

    .card h2 {
      font-size: 0.95rem;
      margin-bottom: 8px;
    }

    .card p {
      font-size: 0.8rem;
      color: #4b5563;
      line-height: 1.4;
    }

    .tag {
      display: inline-block;
      padding: 2px 8px;
      border-radius: 999px;
      font-size: 0.7rem;
      margin-right: 6px;
      margin-bottom: 6px;
      background-color: #e5e7eb;
    }

    .tag-critical {
      background-color: #fee2e2;
      color: #b91c1c;
    }

    .tag-warning {
      background-color: #fef3c7;
      color: #92400e;
    }

    .tag-ok {
      background-color: #dcfce7;
      color: #166534;
    }

    .section-title {
      font-size: 1rem;
      font-weight: 600;
      margin-bottom: 12px;
    }

    .section-subtitle {
      font-size: 0.85rem;
      color: #4b5563;
      margin-bottom: 18px;
    }

    /* Tables */
    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.8rem;
      margin-top: 12px;
    }

    th, td {
      padding: 8px;
      border-bottom: 1px solid #e5e7eb;
      text-align: left;
    }

    th {
      background-color: #f9fafb;
      font-weight: 600;
    }

    /* Forms (login / create account) */
    .form-container {
      max-width: 420px;
      background-color: #ffffff;
      padding: 24px;
      border-radius: 10px;
      border: 1px solid #e5e7eb;
    }

    .form-group {
      margin-bottom: 14px;
    }

    label {
      display: block;
      font-size: 0.8rem;
      margin-bottom: 4px;
      color: #374151;
    }

    input, select {
      width: 100%;
      padding: 8px 10px;
      border-radius: 6px;
      border: 1px solid #d1d5db;
      font-size: 0.85rem;
    }

    button {
      border: none;
      border-radius: 6px;
      padding: 10px 14px;
      font-size: 0.85rem;
      cursor: pointer;
    }

    .btn-primary {
      background-color: #2563eb;
      color: #ffffff;
    }

    .btn-secondary {
      background-color: #e5e7eb;
      color: #111827;
      margin-left: 6px;
    }

    .form-footer {
      margin-top: 12px;
      font-size: 0.8rem;
    }

    .form-footer a {
      color: #2563eb;
      text-decoration: none;
    }

    .form-footer a:hover {
      text-decoration: underline;
    }

    @media (max-width: 900px) {
      .grid {
        grid-template-columns: 1fr;
      }
      .sidebar {
        display: none; /* For prototype simplicity on small screens */
      }
      header {
        padding: 0 12px;
      }
      .content {
        padding: 12px;
      }
    }
  </style>
</head>
<body>
  <!-- Sidebar Navigation -->
  <aside class="sidebar">
    <div class="logo">
      DataCenter One
      <span>Operations Dashboard Prototype</span>
    </div>

    <div class="nav-section-title">Main</div>
    <a href="#overview" class="nav-link active">Landing / Overview</a>
    <a href="#systems" class="nav-link">Systems</a>
    <a href="#alerts" class="nav-link">Alerts</a>
    <a href="#settings" class="nav-link">Settings & Users</a>

    <div class="nav-section-title">Access</div>
    <a href="#login" class="nav-link">Login</a>
    <a href="#create-account" class="nav-link">Create Account</a>

    <div class="sidebar-footer">
      Placeholder prototype. All metrics and text are sample data and Lorem Ipsum.
    </div>
  </aside>

  <!-- Main Content Area -->
  <div class="main">
    <header>
      <div class="page-title">Data Center Dashboard – Prototype</div>
      <div class="user-info">Signed in as: <strong>placeholder.admin@demo</strong></div>
    </header>

    <main class="content">
      <!-- Landing / Overview Page -->
      <section id="overview" class="section visible">
        <div class="section-title">Landing / Overview</div>
        <div class="section-subtitle">
          High-level summary of data center health, capacity, and active alerts.
          This is the main landing page for operations staff.
        </div>

        <div class="grid">
          <div class="card">
            <h2>Global Health Status</h2>
            <p>
            </p>
            <div style="margin-top: 10px;">
              <span class="tag tag-ok">All Regions: Operational</span>
              <span class="tag tag-warning">Minor Warnings: 3</span>
              <span class="tag tag-critical">Critical: 1</span>
            </div>
          </div>

          <div class="card">
            <h2>Capacity Snapshot</h2>
            <p>
            </p>
            <table>
              <tr>
                <th>Resource</th>
                <th>Usage</th>
                <th>Trend</th>
              </tr>
              <tr>
                <td>Compute</td>
                <td>68%</td>
                <td>Stable</td>
              </tr>
              <tr>
                <td>Storage</td>
                <td>72%</td>
                <td>Increasing</td>
              </tr>
              <tr>
                <td>Network</td>
                <td>54%</td>
                <td>Stable</td>
              </tr>
            </table>
          </div>

          <div class="card">
            <h2>Recent Activity</h2>
            <p>
            </p>
            <ul style="margin-top: 8px; font-size: 0.8rem; padding-left: 18px;">
              <li>New maintenance window created for Region A.</li>
              <li>Security patch batch-2025Q1 deployed to 37 hosts.</li>
              <li>Backup job DC-East-01 completed successfully.</li>
            </ul>
          </div>
        </div>
      </section>

      <!-- Systems Page -->
      <section id="systems" class="section">
        <div class="section-title">Systems View</div>
        <div class="section-subtitle">
          Inventory and status of major data center systems, including clusters,
          storage arrays, and network segments.
        </div>

        <div class="card">
          <h2>Systems Inventory</h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum
            venenatis, nunc id dapibus tincidunt, nisl tortor placerat leo, eget
            suscipit diam magna id quam.
          </p>
          <table>
            <tr>
              <th>System</th>
              <th>Type</th>
              <th>Status</th>
              <th>Region</th>
            </tr>
            <tr>
              <td>Cluster-Prod-01</td>
              <td>Compute Cluster</td>
              <td><span class="tag tag-ok">Healthy</span></td>
              <td>US-East</td>
            </tr>
            <tr>
              <td>Storage-Array-07</td>
              <td>Storage</td>
              <td><span class="tag tag-warning">Degraded</span></td>
              <td>US-West</td>
            </tr>
            <tr>
              <td>Core-Network-Edge-03</td>
              <td>Network</td>
              <td><span class="tag tag-ok">Healthy</span></td>
              <td>EU-Central</td>
            </tr>
          </table>
        </div>

        <div class="card" style="margin-top: 16px;">
          <h2>System Detail Panel (Placeholder)</h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam
            rutrum mauris sit amet erat porttitor, sit amet euismod velit
            laoreet. Fusce at lorem ac nulla volutpat vehicula sit amet quis
            erat. Integer gravida risus libero, eget dictum dolor viverra in.
          </p>
        </div>
      </section>

      <!-- Alerts Page -->
      <section id="alerts" class="section">
        <div class="section-title">Alerts</div>
        <div class="section-subtitle">
          Centralized view of warnings and critical events for the data center.
        </div>

        <div class="card">
          <h2>Active Alerts</h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin
            sagittis dolor velit, a eleifend massa tincidunt nec.
          </p>
          <table>
            <tr>
              <th>Severity</th>
              <th>Alert</th>
              <th>Source</th>
              <th>Age</th>
            </tr>
            <tr>
              <td><span class="tag tag-critical">Critical</span></td>
              <td>Disk capacity above 90% on Storage-Array-07</td>
              <td>Monitoring Agent</td>
              <td>12 min</td>
            </tr>
            <tr>
              <td><span class="tag tag-warning">Warning</span></td>
              <td>High CPU usage on Cluster-Prod-01</td>
              <td>Metrics Collector</td>
              <td>34 min</td>
            </tr>
            <tr>
              <td><span class="tag tag-warning">Warning</span></td>
              <td>Backup job duration above baseline</td>
              <td>Backup Service</td>
              <td>2 hrs</td>
            </tr>
          </table>
        </div>

        <div class="card" style="margin-top: 16px;">
          <h2>Alert Filters & Views (Placeholder)</h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed congue
            lorem nisi, sed consequat magna fermentum ac. Nulla facilisi. Duis
            consequat velit ac enim varius, a porttitor arcu ultrices.
          </p>
        </div>
      </section>

      <!-- Settings & Users Page -->
      <section id="settings" class="section">
        <div class="section-title">Settings & User Management</div>
        <div class="section-subtitle">
          Configuration of notification preferences, roles, and access
          control for the dashboard.
        </div>

        <div class="card">
          <h2>User Roles</h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus
            dictum felis at lacinia aliquet. Nunc feugiat ante vel sapien
            fermentum, in dictum lectus tempus.
          </p>
          <table>
            <tr>
              <th>User</th>
              <th>Role</th>
              <th>Status</th>
            </tr>
            <tr>
              <td>placeholder.admin@demo</td>
              <td>Administrator</td>
              <td><span class="tag tag-ok">Active</span></td>
            </tr>
            <tr>
              <td>ops.engineer@demo</td>
              <td>Operator</td>
              <td><span class="tag tag-ok">Active</span></td>
            </tr>
            <tr>
              <td>audit.viewer@demo</td>
              <td>Read Only</td>
              <td><span class="tag tag-warning">Pending</span></td>
            </tr>
          </table>
        </div>

        <div class="card" style="margin-top: 16px;">
          <h2>Notification Preferences (Placeholder)</h2>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse
            blandit luctus sapien vitae molestie. Suspendisse potenti. Quisque
            et sem vel lorem suscipit malesuada.
          </p>
        </div>
      </section>

      <!-- Login Page -->
      <section id="login" class="section">
        <div class="section-title">Login</div>
        <div class="section-subtitle">
          Users enter their credentials to access the Data Center Dashboard.
        </div>

        <div class="form-container">
          <h2 style="margin-bottom: 16px; font-size: 1rem;">Sign In</h2>

          <div class="form-group">
            <label for="login-email">Email or Username</label>
            <input id="login-email" type="text" placeholder="admin@example.com" />
          </div>

          <div class="form-group">
            <label for="login-password">Password</label>
            <input id="login-password" type="password" placeholder="••••••••" />
          </div>

          <div class="form-group" style="display:flex; align-items:center; gap:6px;">
            <input id="remember-me" type="checkbox" style="width:auto;" />
            <label for="remember-me" style="margin:0;">Remember this device</label>
          </div>

          <button class="btn-primary" type="button">Login (Prototype Only)</button>
          <button class="btn-secondary" type="button">Cancel</button>

          <div class="form-footer">
            Forgot your password? This is a prototype, so reset flows are not fully implemented.
            <br />
            Don’t have an account? <a href="#create-account">Create an account</a>.
          </div>
        </div>
      </section>

      <!-- Create Account Page -->
      <section id="create-account" class="section">
        <div class="section-title">Create Account</div>
        <div class="section-subtitle">
          New users request access to the dashboard. In a full system, this would
          trigger an approval workflow.
        </div>

        <div class="form-container">
          <h2 style="margin-bottom: 16px; font-size: 1rem;">Request Access</h2>

          <div class="form-group">
            <label for="signup-name">Full Name</label>
            <input id="signup-name" type="text" placeholder="Jane Doe" />
          </div>

          <div class="form-group">
            <label for="signup-email">Work Email</label>
            <input id="signup-email" type="email" placeholder="jane.doe@datacenter.com" />
          </div>

          <div class="form-group">
            <label for="signup-role">Requested Role</label>
            <select id="signup-role">
              <option>Operator</option>
              <option>Administrator</option>
              <option>Read Only</option>
            </select>
          </div>

          <div class="form-group">
            <label for="signup-password">Create Password</label>
            <input id="signup-password" type="password" placeholder="••••••••" />
          </div>

          <div class="form-group">
            <label for="signup-notes">Additional Notes (Optional)</label>
            <input id="signup-notes" type="text" placeholder="Lorem ipsum dolor sit amet..." />
          </div>

          <button class="btn-primary" type="button">Submit Request (Prototype)</button>
          <button class="btn-secondary" type="button">Back to Login</button>

          <div class="form-footer">
            Placeholder text: Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
            In a real system, users would receive an email when their account is approved.
          </div>
        </div>
      </section>
    </main>
  </div>

  <!-- Tiny script to highlight active nav section (for prototype only) -->
  <script>
    const sections = document.querySelectorAll(".section");
    const navLinks = document.querySelectorAll(".nav-link");

    function showSectionFromHash() {
      const hash = window.location.hash || "#overview";
      sections.forEach(sec => {
        sec.classList.toggle("visible", "#" + sec.id === hash);
      });
      navLinks.forEach(link => {
        link.classList.toggle("active", link.getAttribute("href") === hash);
      });
    }

    window.addEventListener("hashchange", showSectionFromHash);
    window.addEventListener("load", showSectionFromHash);
  </script>
</body>
</html>
