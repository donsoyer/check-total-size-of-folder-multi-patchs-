# check-total-size-of-folder-multi-patchs-
Python script that will calculate the total size of folders listed in a text file.

import os
# Path to the directory where the script is located
script_dir = os.path.dirname(os.path.abspath(__file__))
# Path to the text file with the list of folders
folder_list_path = os.path.join(script_dir, "foldery.txt")
# Function to calculate the size of a folder
def get_folder_size(folder):
    total_size = 0
    for dirpath, dirnames, filenames in os.walk(folder):
        for f in filenames:
            fp = os.path.join(dirpath, f)
            if os.path.exists(fp):
                total_size += os.path.getsize(fp)
    return total_size
# Read folder paths from the text file
with open(folder_list_path, 'r', encoding='utf-8') as file:
    folders = file.readlines()
# Variable to store the total size
total_size = 0
# Iterate through each folder and calculate its size
for folder in folders:
    folder = folder.strip()
    if os.path.exists(folder):
        folder_size = get_folder_size(folder)
        total_size += folder_size
    else:
        print(f"Folder does not exist: {folder}")
# Convert size to GB and display the result
total_size_gb = round(total_size / (1024 ** 3), 2)
print(f"Total size of folders: {total_size_gb} GB")


Description: This script automatically sets the path to the foldery.txt file in the same directory where the script scr.py is located. Now you can place the foldery.txt file in the same directory as the script and run it without manually setting the path.
