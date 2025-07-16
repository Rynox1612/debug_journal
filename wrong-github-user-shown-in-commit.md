## 💥 Problem

I had two users on my system:  
- `user_1` with GitHub username: `username_1`  
- `user_2` with GitHub username: `username_2`

When I committed code inside a repo that belonged to **user_2**, the commit was showing as coming from **username_1's GitHub account**.  
This was happening even though I was using the `user_2` system account and intended to push as `username_2`.

---

## 🎯 Reason

This issue occurred because Git was still using the **global config**, which had `user_1`'s name and email set:

### To check
```bash
git config --global user.name
git config --global user.email 
```

---

## To Fix

** 📌 Case 1 ** : The device is your personal machine, but was previously used by someone else
In this case, it's safe to update the global Git config to reflect your identity:

```bash
- git config --global user.name "username_2"
- git config --global user.email "user_2_email@example.com"
```
This will apply your Git identity across all repos by default.


---

** 📌 Case 2 **: The device is shared between multiple users (e.g., user_1 and user_2 both use it)
In this case, it's better to apply a temporary fix inside the specific repository:
- Firstly go to yourproject directory in terminal

```bash

git config user.name "username_2"
git config user.email "user_2_email@example.com"
```

`To verify it worked:`

```bash

- git config user.name
- git config user.email
```
- Now you can make a demo commit to confirm:

```bash

- git commit  -m "test commit"
- git log --oneline --author="username_2"
```

---
---

✅ If you're looking for a permanent multi-user setup (like SSH key-based config for multiple GitHub accounts), refer to:

[👉 Multiple GitHub Accounts on One Device – Full Guide](comming soon);
