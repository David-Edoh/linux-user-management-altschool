

# linux-user-management-altschool

 1. **Create a Linux user:** To create a new user I used the `sudo adduser <username>` command. This is illustrated in the image below.
    
    ![create a new user](https://github.com/David-Edoh/linux-user-management-altschool/assets/45123163/a8108237-51dc-4825-aeb3-7195ac85e2c3)


 2. **Set an expiry date of 2weeks for the user:** To set an expiry date I used the `sudo usermod -e $(date -d "+2 weeks" "+%Y-%m-%d") <username>` command as illustrated in the image below. To verify the account's expiry date, I used the `sudo chage -l <username>`
    
    ![modify user expiry to 2 weeks](https://github.com/David-Edoh/linux-user-management-altschool/assets/45123163/870a3926-645b-4fd1-a340-61e6c2c9a2a7)

    **Note:** We can also set the expiry date when creating the new user using the -e flag as shown below:
    
    ![create a new user with expiry date](https://github.com/David-Edoh/linux-user-management-altschool/assets/45123163/6038af40-5392-41e8-ac46-2c88318a029d)


 3. **Prompt the user to change their password on login:** To force a user to change the user account password, I used the following command to expire the password of the user. `sudo passwd --expire <username>` This is illustrated below: To verify the password must be changed, I used the `sudo chage -l <username>` to check.
    
    ![Prompt user to change password](https://github.com/David-Edoh/linux-user-management-altschool/assets/45123163/f1c6cddb-7a12-4fe9-a85d-e409d994df17)


 4. **attach the user to a group called altschool:** First I created a group called **altschool** using the command `sudo groupadd altschool` . Next I added the user (David) to the new altschool group using the command `sudo usermod -aG altschool David` To confirm I checked the /etc/group file.
    
    ![Add user to Altschool group](https://github.com/David-Edoh/linux-user-management-altschool/assets/45123163/6027a07c-6b07-4bfb-a5bb-e33ffe85a63a)


 5. **Allow altschool group to be able to run only cat command on /etc/:** I achieved this using the `sudoers` configuration by running `sudo visudo`.
     
     ![running visudo](https://github.com/David-Edoh/linux-user-management-altschool/assets/45123163/cec17473-88c3-40b0-bde2-dc8fe29ff0ce)
    
     **I edited the configuration by adding the following line of code: `%altschool ALL=(ALL) /bin/cat /etc/*` as shown below.**
     
     ![Allow Group to Run Only 'cat' Command on etc folder](https://github.com/David-Edoh/linux-user-management-altschool/assets/45123163/4f7dab5b-0f55-499c-af78-8fa6153d079d)


 6. **Create another user. make sure that this user doesn't have a home directory.** To create a user without a home directory we can use the -M flag or the --no-create-home flag. This is illustrated in the image below:
     
     ![create user without Home dir](https://github.com/David-Edoh/linux-user-management-altschool/assets/45123163/1a95dcc1-bf68-4a57-9022-8867123fa923)

    To verify the user was not created with a home directory, I logged in as the new user and tried to access the home directory using `cd ~`:
    
    ![Proof no directory](https://github.com/David-Edoh/linux-user-management-altschool/assets/45123163/1fb1218e-dea2-4794-b094-bd60146a1c5a)

