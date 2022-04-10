# Install-win-11-cmd
Install win 11 cmd external disk

Open CMD admin

diskpart

list disk

sel disk 1 (selected disk installer)

clean (cleaning disk)

convert gpt

create part efi size=500

format quick fs=fat32 label="System"

assign letter="S"

create part primary

format quick fs=ntfs label="Workspace"

assign letter="W"

EXIT (out diskpart)

cd /d F:\sources (located sources disk)

dism / apply-image /imagefile:install.esd /index:1 / applydir:W:\

bcdboot W:\Windows /s S: /f ALL
