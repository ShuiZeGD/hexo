---
title: 第一篇python博客测试
date: 2025-01-11 21:07
categories: 
    - python
    - test
tags: 
    - python
    - 懵懵懂懂
---

```python
    #! python3
    # pw.py - An insecure password locker program.

    PASSWORDS = {'email': 'FF7minlBDDuvMJuxESSKHFhTxFtjVB6',
                'blog': 'VmALvQyKAxiVH5G8v01if1MLZF3sdt',
                'luggage': '12345'}

    import sys, pyperclip

    if len(sys.argv) < 2:
        print('Usage: python pw.py [account] - copy account password')
        sys.exit()

    account = sys.argv[1] # fist command line arg is the account name

    if account in PASSWORDS:
        pyperclip.copy(PASSWORDS[account])
        print('Password for ' + account + ' copied to clipboard')
    else:
        print('There is no account named ' + account)
```