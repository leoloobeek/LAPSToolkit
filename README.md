# LAPSToolkit
Functions written in PowerShell that leverage PowerView to audit and attack Active Directory environments that have deployed Microsoft's Local Administrator Password Solution (LAPS). It includes finding groups specifically delegated by sysadmins, finding users with "All Extended Rights" that can view passwords, and viewing all computers with LAPS enabled.

Please submit issues or comments for any problems or performance improvements. This project was created with code from an older version of PowerView.

For more information on how LAPS works see https://adsecurity.org/?p=1790.

#### Get-LAPSComputers:
Displays all computers with LAPS enabled, password expriation, and password if user has access
#### Find-LAPSDelegatedGroups:
Searches through all OUs to see which AD groups can read the ms-Mcs-AdmPwd attribute
#### Find-AdmPwdExtendedRights
Parses through ExtendedRights for each AD computer with LAPS enabled and looks for which group has read access and if any user has "All Extended Rights". Sysadmins may not be aware the users with All Extended Rights can view passwords and may be less protected than the users in the delegated groups. An example is the user which adds a computer to the domain automatically receives the "All Extended Rights" permission. Since this function will parse ACLs for each AD computer, this can take very long with a larger domain.

Special thanks to Sean Metcalf (@pyrotek3), Will Schroeder (@harmj0y), Karl Fosaaen (@kfosaaen), Matt Graeber (@mattifestation) for research and code with LAPS, AD permissions, and offensive PowerShell.
