# Fixing time synchronization in my Active Directory homelab

The clocks in my Windows Server lab were out of sync. While troubleshooting,
I found that my second domain controller was using the external NTP pool.
I wanted it to get its time through Active Directory.

I configured the domain controller holding the PDC Emulator role to sync
with us.pool.ntp.org. Since both domain controllers were in the same
organizational unit, I used a WMI filter to limit the external NTP policy
to the PDC Emulator. After the change, my second domain controller synced
with the first. I also used `w32tm /query /source` to check which domain
controller my Windows 11 workstation was using.

I have included a document in that briefly lists the steps taken to fix the Time Synchronization issue with screenshots included.
