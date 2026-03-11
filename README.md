# Active-Directory
Active Directory home lab built on Windows Server 2022, simulating an enterprise environment with custom OU design, PowerShell user and group management, and Group Policy security hardening.

# Organizational Unit Structure
The name of my domain for this project is marvelrivals.org. The parent Organizational Unit(OU) is HEROES. Within the HEROES OU is the Roles OU, followed by Duelists, Strategists, and Tanks OUs, representing each role in the game of Marvel Rivals. These OUs contain the users/characters affiliated with Marvel Rivals. The HEROES OU and all child OUs were created using PowerShell's New-ADOrganizationalUnit command, demonstrating the ability to build out AD structure efficiently through the command line.

# User Account Management
All user accounts were created and managed using Powershell. 
