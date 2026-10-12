# Ticket 02: Account Lockout

**Date:** October 11, 2026
**User:** John Smith (jsmith)
**Category:** Account management

## Issue
User could not sign in. The account was locked out after repeated failed password attempts.

## Environment
- Windows Server 2022 domain controller (`lab.local`)
- Windows 11 client joined to the domain
- VirtualBox lab on an isolated internal network

## Setup
Configured the **Default Domain Policy** with an **account lockout threshold of 3 invalid attempts** (Group Policy Management > Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy). Applied it with `gpupdate /force`.

## Steps Taken
1. Reproduced the problem by entering three wrong passwords at the client sign-in screen. Windows reported the account as locked out.
2. On the domain controller, opened **Active Directory Users and Computers** and opened the user's properties.
3. On the **Account** tab, checked **Unlock account** and clicked Apply.
4. Had the user sign in again from the client.

## Result
Account unlocked and the user signed in successfully.

## Lessons Learned
- Lockouts are enforced by domain policy and fixed on the domain controller, not on the user's PC.
- In a real environment, verify the user's identity before unlocking an account.
