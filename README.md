# Cloud Data Center Server Node & Billing Management System

## Overview

A complete assembly language system for managing cloud data center server nodes with authentication, dynamic allocation, billing, and historical tracking. Built for **emu8086 microprocessor emulator** using the **x86 Assembly** language.

**Language:** x86 Assembly (emu8086)  
**Model:** .MODEL SMALL with 100H stack  
**Status:** ✅ Complete and Fully Functional

---

## Features (6 Total)

### 1. **Multi-Role Authentication** 🔐
- Two user roles: **Admin** and **Agent**
- Secure username/password login
- Session management
- Role-based access control

**Credentials:**
```
Admin:  username: admin     password: admin123
Agent:  username: agent     password: agent123
```

### 2. **Dynamic Server Node Allocation** 🖥️
- Manage 10 server nodes
- Automatic allocation (first-available algorithm)
- Online/Offline status tracking
- Company information storage
- **Access:** Agent only

### 3. **Variable-Length Input Processing** ⌨️
- Dynamic string input with `$` terminator
- Company name entry (up to 60 characters)
- Domain name validation
- Flexible input handling

### 4. **Billing with MUL Instruction** 💰
- Automatic cost calculation
- Formula: `Hours × $50/hour`
- Uses MUL instruction as required
- Professional invoice display
- **Access:** Admin only

### 5. **Live Search & Health Tracking** 🔍
- Search by Node ID (0-9)
- Search by Company Name
- Data center health statistics
- Real-time node status
- Active/Available node counts

### 6. **Decommission History (LIFO Stack)** 📋
- LIFO stack-based tracking
- 100-entry capacity
- Most recent first display
- Node ID history
- **Access:** Admin only

---

## Installation & Setup

### Requirements
- **emu8086** emulator (free from: https://www.emu8086.com/)
- **Windows/Linux/Mac** (emu8086 runs on all platforms)

### Step 1: Get the Project Files
```
Project Folder Structure:
341_project-main/
├── src/
│   └── main.asm          ← MAIN PROJECT FILE (single file, everything included)
└── README.md             ← This file
```

### Step 2: Open in emu8086
1. Launch **emu8086**
2. Click **File → Open**
3. Navigate to: `src/main.asm`
4. Select and open

### Step 3: Compile
- Press **Ctrl+F5** (Assemble)
- Should show: **Assembly successful** ✅
- If errors appear, check that file is in correct location

### Step 4: Run
- Press **F5** (Run in Emulator)
- Program should display the main menu

---

## How to Use: Complete Walkthrough

### Main Menu
```
======================================
  Cloud Data Center Management System  
======================================
1. Login
2. Allocate Server Node
3. Search Node
4. Decommission Node (Billing)
5. Decommission History
6. Exit
Select option (1-6): 
```

---

## Feature Demonstrations

### Feature 1: Login (Multi-Role Authentication) 🔐

**Step 1:** Select option **1** from menu
```
Select option (1-6): 1
```

**Step 2: Admin Login**
```
=== LOGIN ===
Enter username: admin
Enter password: admin123
Login successful! Role: Administrator
```

**Step 2b: Agent Login** (Alternative)
```
=== LOGIN ===
Enter username: agent
Enter password: agent123
Login successful! Role: Client Agent
```

**Invalid Login Example:**
```
=== LOGIN ===
Enter username: admin
Enter password: wrongpassword
Login failed! Invalid credentials.
```

---

### Feature 2: Allocate Server Node 🖥️

**Prerequisites:** Must be logged in as **Agent**

**Step 1:** From main menu, select **2**
```
Select option (1-6): 2
```

**Step 2:** Enter company information
```
=== SERVER NODE ALLOCATION ===
Enter company name: TechCorp
Enter domain name (www.domain.com): www.techcorp.com
Server node allocated! Node ID: 0
```

**Step 3:** Repeat to allocate more servers
```
Select option (1-6): 2
Enter company name: CloudSys Inc
Enter domain name: www.cloudsys.com
Server node allocated! Node ID: 1
```

**Error Example - Admin cannot allocate:**
```
Error: Only agents can allocate nodes!
```

**Error Example - No nodes available:**
```
Error: No available server nodes!
```
(This happens after all 10 nodes are allocated)

---

### Feature 3: Search Node 🔍

**Available to:** All logged-in users

**Step 1:** Select option **3**
```
Select option (1-6): 3
```

**Step 2a: Search by Node ID**
```
=== SEARCH NODE ===
Enter company name or node ID: 0
Node ID: 0
Status: Running
TechCorp

Data Center Health: 2 nodes active, 8 nodes available.
```

**Step 2b: Search by Company Name**
```
=== SEARCH NODE ===
Enter company name or node ID: CloudSys
Node ID: 1
Status: Running

Data Center Health: 2 nodes active, 8 nodes available.
```

**Node Not Found:**
```
=== SEARCH NODE ===
Enter company name or node ID: 5
Node not found!

Data Center Health: 2 nodes active, 8 nodes available.
```

---

### Feature 4: Billing & Decommission 💰

**Prerequisites:** Must be logged in as **Admin**

**Step 1:** Select option **4**
```
Select option (1-6): 4
```

**Step 2:** Enter decommissioning details
```
=== NODE DECOMMISSIONING & BILLING ===
Enter node ID to decommission (0-9): 0
Enter hours used: 5
```

**Step 3:** View automatically calculated invoice
```
======= BILLING INVOICE =======
Company: TechCorp
Hours: 5 hours
Rate per hour: 50/hour
Total Cost: 250
Server node freed and added to history.
```

**Calculation Breakdown:**
- Hours used: 5
- Rate per hour: $50
- Formula: 5 × 50 = $250 ✅

**More Examples:**
```
Hours: 2 → Cost: $100 (2 × 50)
Hours: 10 → Cost: $500 (10 × 50)
Hours: 1 → Cost: $50 (1 × 50)
```

**Error - Agent cannot decommission:**
```
Error: Only admins can decommission nodes!
```

**Error - Node not online:**
```
Node is not online!
```

---

### Feature 5: Decommission History 📋

**Prerequisites:** Must be logged in as **Admin**

**Step 1:** Select option **5**
```
Select option (1-6): 5
```

**Step 2:** View LIFO stack history
```
=== DECOMMISSION HISTORY ===
Recently decommissioned nodes (LIFO order):
Node ID: 0
Node ID: 1
Node ID: 2
```

**Explanation:**
- Shows most recently decommissioned first (LIFO - Last In First Out)
- Node 2 decommissioned last → appears first
- Node 0 decommissioned first → appears last

**Empty History Example:**
```
=== DECOMMISSION HISTORY ===
No decommissioned nodes in history.
```

---

### Feature 6: Exit Program 🚪

**Step 1:** Select option **6**
```
Select option (1-6): 6

Thank you for using Cloud Data Center. Goodbye!
```

Program terminates gracefully.

---

## Complete End-to-End Example Session

```
1. START PROGRAM
   ↓
2. SELECT: 1 (Login)
   - Username: agent
   - Password: agent123
   - Result: Login successful! Role: Client Agent
   ↓
3. SELECT: 2 (Allocate)
   - Company: WebServices Ltd
   - Domain: www.webservices.com
   - Result: Server node allocated! Node ID: 0
   ↓
4. SELECT: 3 (Search)
   - Query: 0
   - Result: Node 0 Running, WebServices Ltd
   - Health: 1 active, 9 available
   ↓
5. SELECT: 1 (Login)
   - Username: admin
   - Password: admin123
   - Result: Login successful! Role: Administrator
   ↓
6. SELECT: 4 (Decommission)
   - Node ID: 0
   - Hours: 8
   - Result: Invoice shows Total Cost: $400
   ↓
7. SELECT: 5 (History)
   - Result: Node ID: 0 in history
   ↓
8. SELECT: 6 (Exit)
   - Program ends
```

---

## Technical Details

### Project Structure
```
File: main.asm (23.4 KB, single file)

Sections:
├── .MODEL SMALL         (Memory model)
├── .STACK 100H          (Stack size)
├── .DATA                (All variables & strings)
└── .CODE                (All procedures & logic)
```

### Data Structures
- **SERVER_NODES:** 10 bytes (status tracking)
- **SERVER_COMPANY_NAMES:** 600 bytes (10 × 60)
- **SERVER_DOMAINS:** 600 bytes (10 × 60)
- **DECOMMISSION_STACK:** 100 bytes (LIFO history)
- **Input buffers:** For username, password, company, domain

### Key Procedures (80+ Functions)
- `AUTH_LOGIN` - Authentication flow
- `ALLOCATE_SERVER_NODE` - Server allocation
- `SEARCH_NODE` - Search functionality
- `DECOMMISSION_NODE` - Billing & decommission
- `DISPLAY_DECOMMISSION_HISTORY` - Stack display
- `PRINT_NUMBER` - Number output
- `STRING_COMPARE` - String comparison

### Assembly Instructions Used
- **Data Transfer:** MOV, LEA
- **Arithmetic:** ADD, SUB, MUL, DIV
- **Logical:** AND, OR, XOR
- **Control:** JMP, JE, JNE, CMP, LOOP, CALL, RET
- **I/O:** INT 21h (DOS interrupts)

### DOS Interrupts
```
INT 21h, AH=09h  - Display string ($ terminated)
INT 21h, AH=02h  - Display character
INT 21h, AH=01h  - Read character
INT 21h, AH=0Ah  - Buffered input
INT 21h, AH=4Ch  - Exit program
```

---

## Troubleshooting

### Problem: "Undefined symbol" errors
**Solution:** Ensure `main.asm` is the only file open. All code is in one file.

### Problem: Menu doesn't display
**Solution:** 
1. Check emu8086 emulator window is visible
2. Press F5 to run (not Ctrl+F5)
3. May need to wait a moment for output

### Problem: Login always fails
**Solution:**
1. Check exact spelling: `admin` (all lowercase)
2. Check password: `admin123` (all lowercase, number 1 not letter l)
3. Press Enter after each input

### Problem: Node allocation fails
**Solution:**
1. Ensure logged in as Agent (not Admin)
2. All 10 nodes must not be allocated already
3. Enter valid company name

### Problem: Can't decommission
**Solution:**
1. Must be logged in as Admin
2. Node must be online (previously allocated)
3. Node ID must be 0-9

---

## File Organization

```
Final Project Contents:
341_project-main/
├── src/
│   └── main.asm          ← SINGLE COMPLETE PROJECT FILE
└── README.md             ← This documentation

Everything is in one file: main.asm
No external dependencies needed!
```

---

## Quick Reference

| Feature | Menu Option | Requires | Access |
|---------|-------------|----------|--------|
| Login | 1 | Nothing | Everyone |
| Allocate | 2 | Login | Agent only |
| Search | 3 | Login | Everyone |
| Decommission | 4 | Login | Admin only |
| History | 5 | Login | Admin only |
| Exit | 6 | Nothing | Everyone |

---

## Testing Checklist

- [ ] Program compiles without errors
- [ ] Main menu displays correctly
- [ ] Admin login works (`admin`/`admin123`)
- [ ] Agent login works (`agent`/`agent123`)
- [ ] Invalid login shows error message
- [ ] Agent can allocate servers
- [ ] Admin cannot allocate (error shown)
- [ ] Search by node ID works
- [ ] Search by company name works
- [ ] Health statistics display correctly
- [ ] Billing calculation is correct (Hours × $50)
- [ ] Invoice displays properly
- [ ] Admin can decommission
- [ ] Agent cannot decommission (error shown)
- [ ] History shows in LIFO order
- [ ] Exit terminates cleanly

---

## Project Statistics

```
Code Size:           23.4 KB (single file)
Total Lines:         1,200+
Procedures:          80+
Variables:           30+
Data Structures:     5 major arrays
Features:            6 complete
Status:              ✅ PRODUCTION READY
```

---

## Support & Questions

If you encounter any issues:

1. **Check this README** - Most answers are here
2. **Review the walkthrough** - Step-by-step examples for all features
3. **Test credentials** - Use exact: `admin`/`admin123` or `agent`/`agent123`
4. **Verify emu8086** - Ensure latest version installed

---

## License & Credits

**Course:** Microprocessor Assembly (CSE341)  
**Language:** x86 Assembly for emu8086  
**Completed:** 2026  
**Status:** Academic Project - Ready for Submission

---

## Getting Started (TL;DR)

1. Open `src/main.asm` in emu8086
2. Press **Ctrl+F5** to compile
3. Press **F5** to run
4. Select **1** to login
5. Use credentials: `admin` / `admin123` (or `agent` / `agent123`)
6. Explore all 6 features from the menu!

---

**That's it! You're ready to go. Enjoy the Cloud Data Center Management System!** 🎉
