# Active-Directory
Active Directory home lab built on Windows Server 2022, simulating an enterprise environment with custom OU design, PowerShell user and group management, and Group Policy security hardening.

# Organizational Unit Structure
The name of my domain for this project is marvelrivals.org. The parent Organizational Unit(OU) is HEROES. Within the HEROES OU is the Roles OU, followed by Duelists, Strategists, and Tanks OUs, representing each role in the game of Marvel Rivals. These OUs contain the users/characters affiliated with Marvel Rivals. The HEROES OU and all child OUs were created using PowerShell's New-ADOrganizationalUnit command, demonstrating the ability to build out AD structure efficiently through the command line.

# User Account Management
All user accounts were created and managed using Powershell. 
* New-ADUser: Created and enabled multiple user accounts, placing each into their respective OU within the HEROES hierarchy using parameters such as -SamAccountName, -UserPrincipalName, -Path, and -AccountPassword
* Set-ADUser: Modifies existing accounts including updating email attributes, adding office phone numbers, and toggling account enabled/disabled status — simulating real-world onboarding and offboarding tasks
* Set-ADAccountPassword — Reset user passwords with the -ChangePasswordAtLogon flag enforced, following security best practices.

# Group Management
Three security groups were created for the Marvel Rivals domain.

### X-Men
Anna Marie(Rogue), Betsy Braddock(Psylocke), Emma Frost, Jean Grey(Phoenix), Logan Howlett(Wolverine),
Remy LeBeau(Gambit)

### Avengers
Peter Parker(Spider-Man), Steve Rogers(Captain America), Thor Odinson(Thor), Tony Stark(Iron Man)

### Fantastic Four
Benn Grimm(The Thing), Susan Storm(Invisible Woman), Reed Richards(Mr. Fantastic), Johnny Storm(Human Torch)

# Group Policy Objects

### Password Policy
The Password Policy GPO enforces a 12-character minimum password length, 90-day maximum password age, complexity requirements, and a 5-password history to prevent reuse.

### Account Lockout Policy
The Account Lockout GPO locks accounts after 5 invalid login attempts for 30 minutes, with the failed attempt counter resetting after 15 minutes to protect against brute force attacks.

### Windows Defender Policy
The Windows Defender GPO ensures the antimalware service is always running with real-time protection, behavior monitoring, and scanning of all downloaded files enabled. A daily quick scan is scheduled at 2:00 AM with catch-up full scans enabled to ensure machines that were offline do not miss scheduled scans.

### Windows Update Policy
The Windows Update GPO configures machines to automatically download and install updates every Tuesday at 6:00 AM, aligning with Microsoft's Patch Tuesday schedule to minimize security vulnerabilities.

### Firewall Policy
The Firewall GPO enables the Windows Defender Firewall across all profiles, blocking all inbound connections while allowing outbound traffic to maintain a secure network boundary.

### Screen Lock Policy
The Screen Lock GPO automatically locks workstations after 15 minutes of inactivity, enforces a 5-attempt machine lockout threshold, and displays a custom "Welcome to Rivals HQ" logon banner.

### Removable Storage Policy
The Removable Storage GPO denies all access to removable storage devices, blocks read access to CD/DVD drives, and prevents write access to USB drives to enforce data loss prevention controls.
