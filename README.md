# Block Windows Password Logon
Block the ability to log onto Windows sessions with passwords (created for improving EIDAuthenticate).
This is done by disabling the Password Credential Provider built into Windows.

One additional registry tweak for Safe Mode support is to prohibit fallback (force all providers to load even in Safe Mode).
Otherwise you wouldn't be able to log onto your session at all if you happened to need the Windows Safe Mode (F8 startup key).

## Why block password logon?
Windows doesn't only have password available for logon. It's also possible to use third-party Credential Providers such as Rohos Logon Key, Rohos Face Logon, EIDAuthenticate & MultiOTP which add 2-factor authentication for Windows session logon.

In such cases you can potentially login to your Windows user accoutn using either of these:
- Fingerprint (builtin)
- Smartcard (builtin/EIDAuthenticate)
- Face (Rohos Face Logon)
- Time-based OTP (Rohos Logon Key)
- SMS OTP (MultiOTP/Rohos Logon Key)
- USB drive (VsUsbLogon)

Thus you'll understand that it's desirable to combine one or many of these at once without allowing plain passwords to be used anymore.
Otherwise the Force Smartcard Logon method via Group Policy only works for smartcard logon and nothing else.
