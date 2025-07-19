🐞 Debug Journal Entry: Managing Two GitHub Users on One System
---------------------------------------------------------------

### 📌 Problem Faced:

This month, my system was being used by **two different GitHub users** — me and one more contributor. But the problem was:

*   bashCopyEditgit config --global user.name "Rupesh Sahu"git config --global user.email "rssahu8454@gmail.com"
    
*   Due to this, **every commit** — even those pushed by the second user — was getting committed under **my identity**, which caused confusion on GitHub commit history.
    

### 🤔 Understanding the Root Cause:

Git tracks identity based on the config set:

*   If --global is used, it applies system-wide.
    
*   So multiple GitHub users on a **single machine** will cause overlaps and **wrong author information**.
    

> ❌ **System credentials alone can't manage two GitHub users cleanly unless you create full separate OS-level users** — which:
> 
> *   Consumes extra disk space
>     
> *   Affects system performance
>     
> *   Is not practical for most cases
>     

# ✅ Solution: Use SSH Key-Based Configuration

Instead of relying on GitHub username/password or token (HTTP method), I adopted the **SSH method**, which allows separation of identities securely and efficiently.

#### 🔑 How SSH Works:

*   SSH keys act like a **lock and key pair**.
    
*   Each user can have their own **unique key pair**.
    
*   These keys are **mapped to specific GitHub accounts**, so Git knows who’s who.
    
*   To setup SSH key refer:[SSH key setup](./SSH-key-setup.md).

### 💡 Outcome:

Now, commits from both users are:

*   **Accurately tracked**
    
*   **Properly separated**
    
*   **Securely authenticated**
    

### 🧠 Takeaway:

> Always avoid using global Git config when multiple users are working on the same system.Use SSH key-based authentication for clean identity separation.

