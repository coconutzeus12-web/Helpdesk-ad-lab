# Ticket 01: Password Reset

**Date:** October 11, 2026
**User:** John Smith (jsmith)
**Category:** Account management

## Issue
User needed his password reset.

## Environment
- Windows Server 2022 domain controller (`lab.local`)
- Windows 11 client joined to the domain
- VirtualBox lab on an isolated internal network

## Steps Taken
1. Opened **Active Directory Users and Computers** on the domain controller and found the user in the Employees OU.
2. Right-clicked the account and chose **Reset Password**. Set a temporary password and enabled **User must change password at next logon**.
3. Signed in from the client with the temporary password.
4. The new password was rejected with a length/complexity/history error. I identified the likely cause (the password was already in the account's history) and chose a new password that met the length and complexity rules.

## Result
User signed in successfully with the new password.

## Lessons Learned
- A rejected new password usually comes down to **history**, **complexity**, or **length**. Check those first.
- Forcing a password change at next logon means only the user knows the final password.
