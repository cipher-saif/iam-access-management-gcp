```
██╗ █████╗ ███╗   ███╗
██║██╔══██╗████╗ ████║
██║███████║██╔████╔██║
██║██╔══██║██║╚██╔╝██║
██║██║  ██║██║ ╚═╝ ██║
╚═╝╚═╝  ╚═╝╚═╝     ╚═╝
```

<div align="center">

# Implementing Identity and Access Management (IAM) Using Google Cloud

*Role-based access control, least-privilege enforcement, and security validation on GCP*

</div>

---

&nbsp;

```
═══════════════════════════════════════════════════════
𝐎𝐕𝐄𝐑𝐕𝐈𝐄𝐖
═══════════════════════════════════════════════════════
```

This project demonstrates the implementation of Identity and Access Management (IAM) on Google Cloud Platform using a multi-user sandbox environment. Three principals were configured with distinct roles — Owner, Editor, and Viewer — to simulate real-world access control scenarios and validate the enforcement of role-based permissions across a shared cloud project.

The work directly mirrors enterprise security practices: assigning the minimum permissions required per identity, testing access boundaries, and confirming that unauthorized actions are blocked at the policy level.

&nbsp;

---

```
═══════════════════════════════════════════════════════
𝐎𝐁𝐉𝐄𝐂𝐓𝐈𝐕𝐄𝐒
═══════════════════════════════════════════════════════
```

- Implement Role-Based Access Control (RBAC) using Google Cloud IAM
- Assign and manage user roles across a shared GCP project
- Enforce the principle of least privilege across all three principals
- Validate access restrictions by testing each role's permission boundaries
- Confirm that IAM policies prevent unauthorized modifications and resource access
- Simulate SOC and cloud administration workflows for access control management

&nbsp;

---

```
═══════════════════════════════════════════════════════
𝐓𝐎𝐎𝐋𝐒  &  𝐓𝐄𝐂𝐇𝐍𝐎𝐋𝐎𝐆𝐈𝐄𝐒
═══════════════════════════════════════════════════════
```

![GCP](https://img.shields.io/badge/Google_Cloud_Platform-4285F4?style=flat&logo=googlecloud&logoColor=white)
![IAM](https://img.shields.io/badge/Cloud_IAM-34A853?style=flat&logo=googlecloud&logoColor=white)
![RBAC](https://img.shields.io/badge/RBAC-Role_Based_Access_Control-black?style=flat)
![Sandbox](https://img.shields.io/badge/Environment-GCP_Skills_Boost-grey?style=flat)

&nbsp;

---

```
═══════════════════════════════════════════════════════
𝐏𝐑𝐎𝐉𝐄𝐂𝐓  𝐒𝐓𝐑𝐔𝐂𝐓𝐔𝐑𝐄
═══════════════════════════════════════════════════════
```

```
iam-access-management-gcp/
│── README.md
│── Report/
│   └── Implementing_Identity_and_Access_Management__IAM__Policies.pdf
│── Screenshots/
│   ├── iam-dashboard.jfif
│   ├── iam-role-list.jfif
│   ├── no-access.jfif
│   ├── viewer-permission-denied.jfif
│   ├── setting-multiple-roles.jfif
│   └── principal-roles-view-edit-all.jfif
```

&nbsp;

---

```
═══════════════════════════════════════════════════════
𝐈𝐀𝐌  𝐂𝐎𝐍𝐂𝐄𝐏𝐓𝐒
═══════════════════════════════════════════════════════
```

| Concept | Description |
|---|---|
| Principal | An identity (user or service account) that can access cloud resources |
| Role | A collection of permissions grouped for a specific access level |
| Permission | A granular action allowed on a specific resource |
| RBAC | Role-Based Access Control — linking roles to principals |
| Least Privilege | Granting only the minimum permissions required to perform a task |

&nbsp;

---

```
═══════════════════════════════════════════════════════
𝐏𝐑𝐎𝐉𝐄𝐂𝐓  𝐀𝐑𝐂𝐇𝐈𝐓𝐄𝐂𝐓𝐔𝐑𝐄
═══════════════════════════════════════════════════════
```

Three principals were configured within a single GCP project, each assigned a distinct role:

```
My First Project
│
├── User 1 — thunderblizzard4@gmail.com     →  Owner   (Full administrative access)
├── User 2 — saifacc4.0@gmail.com           →  Viewer  (Read-only access)
└── User 3 — miraculouseclipse@gmail.com    →  Editor  (Modify resources, no IAM access)
```

Each user was tested independently to validate permission boundaries and confirm RBAC enforcement.

&nbsp;

---

```
═══════════════════════════════════════════════════════
𝐌𝐄𝐓𝐇𝐎𝐃𝐎𝐋𝐎𝐆𝐘
═══════════════════════════════════════════════════════
```

&nbsp;

### Step 1 — Accessing the Google Cloud Console

The GCP Console was accessed using sandbox credentials provided by Google Cloud Skills Boost. Three separate browser sessions were opened simultaneously — one per user — to enable real-time comparison of role-based behavior across principals.

&nbsp;

### Step 2 — Signing in as Project Owner (User 1)

User 1 logged in with Owner credentials and accessed the IAM & Admin Console. Owner-level permissions were confirmed, including full visibility of all principals, roles, and the ability to grant or revoke access across the project.

&nbsp;

### Step 3 — Exploring IAM Roles

The three built-in GCP roles used in this project were examined:

| Role | Permissions |
|---|---|
| Viewer | Read-only access to most GCP resources |
| Editor | Create, update, and delete resources — cannot manage IAM policies |
| Owner | Full administrative access including IAM policy management |

&nbsp;

### Step 4 — Signing in as Limited User (User 2 — Viewer)

User 2 was logged in with Viewer credentials. An attempt was made to modify IAM policies via the IAM & Admin Console. The action was blocked with a permission denial message, confirming that the Viewer role enforces read-only access at the project level.

**Required permission flagged:** `resourcemanager.projects.setIamPolicy`

&nbsp;

### Step 5 — Signing in as Limited User (User 3 — Editor)

User 3 was assigned the Editor role alongside a secondary Viewer role. Testing confirmed that the Editor was able to create and modify cloud resources but was blocked from making any IAM policy changes — validating the intermediate privilege boundary of the Editor role.

&nbsp;

### Step 6 — Testing Role-Based Access Control (RBAC)

A final validation pass was conducted across all three users:

- **User 1 (Owner):** Full access — can manage IAM, assign roles, and administer the project
- **User 2 (Viewer):** Read-only — cannot change resources or modify IAM policies
- **User 3 (Editor):** Modify access — can edit resources but cannot manage IAM

All RBAC boundaries were confirmed to be functioning correctly per GCP IAM policy definitions.

&nbsp;

---

```
═══════════════════════════════════════════════════════
𝐑𝐄𝐒𝐔𝐋𝐓𝐒  &  𝐒𝐂𝐑𝐄𝐄𝐍𝐒𝐇𝐎𝐓𝐒
═══════════════════════════════════════════════════════
```

&nbsp;

<div align="center">
<table border="1" cellpadding="16" cellspacing="0">
<tr>
<td align="center">
<img src="Screenshots/iam-dashboard.jfif" width="780"/>
<br/><br/>
<b>𝗙𝗶𝗴. 𝟭 &nbsp;·&nbsp; IAM Dashboard — Owner View</b><br/>
<sub>The IAM &amp; Admin Console under User 1 (Owner). The dashboard confirms <code>thunderblizzard4@gmail.com</code> as project Owner with Grant access and Remove access fully active.</sub>
</td>
</tr>
</table>
</div>

&nbsp;

<div align="center">
<table border="1" cellpadding="16" cellspacing="0">
<tr>
<td align="center">
<img src="Screenshots/iam-role-list.jfif" width="780"/>
<br/><br/>
<b>𝗙𝗶𝗴. 𝟮 &nbsp;·&nbsp; IAM Role List — All Principals</b><br/>
<sub>The principal list after all three users are configured under "View by principals". Three distinct identities are visible — Editor + Viewer, Viewer, and Owner — confirming successful role assignment across all principals.</sub>
</td>
</tr>
</table>
</div>

&nbsp;

<div align="center">
<table border="1" cellpadding="16" cellspacing="0">
<tr>
<td align="center">
<img src="Screenshots/no-access.jfif" width="780"/>
<br/><br/>
<b>𝗙𝗶𝗴. 𝟯 &nbsp;·&nbsp; No Access — Unauthorized Page</b><br/>
<sub>The "You don't have access" screen triggered when a restricted user navigates to a resource outside their permission scope. Confirms IAM enforces access at the page and resource level, not solely at the API layer.</sub>
</td>
</tr>
</table>
</div>

&nbsp;

<div align="center">
<table border="1" cellpadding="16" cellspacing="0">
<tr>
<td align="center">
<img src="Screenshots/viewer-permission-denied.jfif" width="780"/>
<br/><br/>
<b>𝗙𝗶𝗴. 𝟰 &nbsp;·&nbsp; Viewer — Permission Denied on IAM Action</b><br/>
<sub>Permission denial triggered when User 2 (Viewer) attempts to grant access in the IAM console. Required permission <code>resourcemanager.projects.setIamPolicy</code> is flagged, confirming least-privilege enforcement.</sub>
</td>
</tr>
</table>
</div>

&nbsp;

<div align="center">
<table border="1" cellpadding="16" cellspacing="0">
<tr>
<td align="center">
<img src="Screenshots/setting-multiple-roles.jfif" width="780"/>
<br/><br/>
<b>𝗙𝗶𝗴. 𝟱 &nbsp;·&nbsp; Setting Multiple Roles for a Single Principal</b><br/>
<sub>The "Edit access" panel for User 3 (<code>miraculouseclipse@gmail.com</code>), showing both Editor and Viewer roles assigned simultaneously. Each role entry supports an optional IAM condition for attribute-based access refinement.</sub>
</td>
</tr>
</table>
</div>

&nbsp;

<div align="center">
<table border="1" cellpadding="16" cellspacing="0">
<tr>
<td align="center">
<img src="Screenshots/principal-roles-view-edit-all.jfif" width="780"/>
<br/><br/>
<b>𝗙𝗶𝗴. 𝟲 &nbsp;·&nbsp; Principal Roles — View by Roles</b><br/>
<sub>The "View by roles" tab grouping all three role categories — Editor (1), Owner (1), Viewer (1) — with their respective principals listed beneath each. Confirms clean separation of duties across all assigned identities.</sub>
</td>
</tr>
</table>
</div>

&nbsp;

---

```
═══════════════════════════════════════════════════════
𝐒𝐄𝐂𝐔𝐑𝐈𝐓𝐘  𝐕𝐀𝐋𝐈𝐃𝐀𝐓𝐈𝐎𝐍
═══════════════════════════════════════════════════════
```

- Viewer users are blocked from modifying IAM policies — read-only access is strictly enforced
- Editor users can create and update resources but cannot grant or revoke IAM roles
- Only the Owner can manage IAM policies, assign roles, and perform administrative operations
- IAM enforces permissions at the project level, applying uniformly across all child resources
- Role misconfiguration introduces security risk — granting elevated access unnecessarily expands the attack surface
- Least-privilege assignment demonstrably reduces the blast radius of compromised credentials

&nbsp;

---

```
═══════════════════════════════════════════════════════
𝐃𝐎𝐂𝐔𝐌𝐄𝐍𝐓𝐀𝐓𝐈𝐎𝐍
═══════════════════════════════════════════════════════
```

[Download Full Report](Report/Implementing_Identity_and_Access_Management__IAM__Policies.pdf)

&nbsp;

---

```
═══════════════════════════════════════════════════════
𝐂𝐎𝐍𝐂𝐋𝐔𝐒𝐈𝐎𝐍
═══════════════════════════════════════════════════════
```

This project successfully implemented and validated Identity and Access Management across a multi-user Google Cloud environment. Role-based access control was enforced across three distinct principals — Owner, Editor, and Viewer — with each role boundary confirmed through live access testing.

The implementation demonstrated that GCP IAM reliably blocks unauthorized actions at the policy level, enforces the principle of least privilege, and provides granular visibility into who holds what permissions across a project. These outcomes directly reflect enterprise cloud security requirements, where strict access governance is foundational to reducing risk and maintaining compliance.

&nbsp;

---

<div align="center">

Developed as part of a personal cloud security portfolio project

</div>
