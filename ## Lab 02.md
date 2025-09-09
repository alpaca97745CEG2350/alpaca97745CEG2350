## Lab 02

- Name: Gary Maltby
- Email maltby.3@wright.edu

## Part 1 Answers

Full / absolute path to your private key file: C:\Users\GARYM\Desktop\CEG 2350\keyfile

Command to SSH to AWS instance:
```
ssh -i .\ceg2350-aws-vm.pem unbuntu@52.0.82.125 unbuntu@52.0.82.125
```

## Part 2 Answers

1. `chmod u+r bubbles.txt`
    - Means: Adding read to the user permissions.
    - Assessment: Adding a read permission to the user (owner of the file) will not impact anything since they own the file and its a read permission.
2. `chmod u=rw,g-w,o-x banana.cabana`
    - Means: Changes permissions to the file banana.cabana. U=rw changes the user permissions to exclusively read and write. G-w Changes the group permissions by removing write but all other permissions remain the same. o-x Removes the execute permission from others but all other permissions are unchanged.
    - Assessment: Execute was removed from all groups. The user/owner is the only person with write permissions. The owner should be allowed to read and write, but not members belonging to group or other.
3. `chmod a=w snow.md`
    - Means: Changes permissions to the file snow.md. Removes read and execute permissions for Users, Groups, and Others and assigns the  write permission to Users, Groups, and Others.
    - Assessment: This isn't a good idea, because not even the owner will be able to view the file
4. `chmod 751 program`
    - Means: Owner can read write and execute, Group can read and execute, and others can only execute the file.
    - Assessment: This is not a good idea because others can execute the file, so anyone can run the program.
5. `chmod -R ug+w share`
    - Means: Recursively add the permission write to user and group to "share".
    - Assessment: This is ok if everyone in the group is authorized to write to the contents included in the share folder.

## Part 3 Answers

1. Command to create new user: sudo adduser gmaltby
2. Path to new user's home directory: /home/gmaltby
3. Evaluate if `ubuntu` can add files to new user's home directory: Yes it can
4. Command to switch to new user: su gmaltby
5. Command(s) to go to new user's home directory: cd ~
6. Evaluate if new user can add files to user's home directory: Yes. touch usernewfile.txt 
7. Command to return to `ubuntu` user: exit
8. Command to return to `ubuntu` home directory: cd ~

## Part 4 Answers

1. Command(s) to create group named `squad` and add members: sudo addgroup squad
2. Command(s) to add `ubuntu` & user to group `squad`: sudo usermod -aG squad ubuntu  sudo usermod -aG squad gmaltby
3. Command(s) to allow `squad` to view the `ubuntu` user's home directory contents: sudo chgrp -R squad /home/ubuntu
4. Command(s) to modify `share` to have group ownership of `squad`: 
5. Describe your tests and commands with the user account: Tested both users could view the permissions with ls -la /home/ubuntu/SHARE. Both users could view the permissions of the folder.

6. Describe the full set of permissions / settings that enable the user to make edits: The user/owner has RWX, the group/squad has RWX, and Others have R-X. Because gmaltby is a member of squad, that have permissions RWX, the user is able to create the file.

## Part 5 Answers

For each, write the command used or answer the question posed.

1. Command(s) to make file using `sudo`: sudo touch /home/ubuntu/madeitwithsudo.txt
2. Command(s) to make file with `root`: sudo -i 	touch /home/ubuntu/madewithroot.txt
3. Describe / compare ownership and permissions of files: -rw-r--r-- The user/owner has read/write. Group and others have read permissions.
4. Which account can do what actions? (Type Y or N in columns)

Contents inside of `share`
| Account   | Can View  | Can Edit  | Can Change Permissions    |
| ---       | ---       | ---       | ---                       |
| `root`    |    Y      |    Y      |       Y                   |
| `ubuntu`  |    Y      |    Y      |       Y                   |
| `BOB`     |    Y      |    Y      |       N                   |

`madewithsudo.txt`
| Account   | Can View  | Can Edit  | Can Change Permissions    |
| ---       | ---       | ---       | ---                       |
| `root`    |   Y       |    Y      |       Y                   |
| `ubuntu`  |   Y       |    N      |       N                   |
| `BOB`     |   Y       |    N      |      N                    |

5. Command(s) to modify permissions: sudo chown ubuntu:squad /home/ubuntu/madeitwithsudo.txt   sudo chmod 664 /home/ubuntu/madeitwithsudo.txt 
6. How to give user account `sudo`: ubuntu is a member of sudo and gmaltby is not. sudo usermod -aG sudo gmaltby 

## Citations

To add citations, provide the site and a summary of what it assisted you with.  If generative AI was used, include which generative AI system was used and what prompt(s) you fed it.
