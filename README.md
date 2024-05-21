# conan-exiles-eggs
Custom Pteradactyl Eggs for Conan Exiles

Started with Original egg at https://github.com/pelican-eggs/eggs.

Added a new variable called **Mod ID(s) List**.
This is a string that should be a comma separated list of Steam mod ID numbers in load order.

The install script was changed to include writing a new filed called exilesmod.sh into the /home/container directory in the server container.

This script runs prior to launching wine. It uses steamcmd.exe to download mods listed in the Mod ID(s) List variable. After that, the downlaoded files are copied into /home/container/ConanSandbox/Mods and a modlist.txt file is generated. From a storage perspective, this is inefficient since the container has 2 copies of each mod workshop folder, but I'm unsure how to accomplish the same wihtout re-downloading every mod at each server restart if the original downloads aren't kept in the download directory.
