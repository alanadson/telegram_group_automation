This script is a Telegram bot that allows users to add other Telegram users to a group. It utilizes the Pyrogram library to interact with the Telegram API, as well as the PIL, configparser, and openpyxl libraries for image manipulation, configuration file handling, and Excel file handling respectively.

The script begins by reading in a configuration file (config.ini) which contains the API ID, API Hash, and phone number for the Telegram account being used. The Pyrogram Client is then initialized with these values and started.

The script then enters a while loop that presents the user with a menu of options. The options include:

Add users to a group via a link
Add users to a group via an Excel file
Export groups from the user's Telegram account
Export users from a group
Extract user IDs
Warmup a Telegram profile
Update Telegram credentials
The user enters the number corresponding to the desired option, and the script will execute the corresponding function.

The "add_users_by_link" function prompts the user for a link to the source group (from which users will be taken) and a link to the destination group (to which users will be added). It then uses the Pyrogram Client to get the group ID for both groups, and uses the "get_chat_members" function to get a list of members of the source group. The members are shuffled randomly, and the user is prompted for the number of users they want to add and the time to wait between adding each user. The script then iterates through the members, adding the specified number of users to the destination group with the "add_chat_members" function, and also records the user IDs of the added users to a json file "sent_messages.json"

The "add_users_by_excel" function prompts the user for the link to the destination group and the name of an Excel file containing a list of Telegram username to be added to the group. The script then uses openpyxl to read the Excel file and extract the usernames from the specified column and row range. It then uses the Pyrogram Client to add the users to the destination group using the "add_chat_members" function.

The "add_groups_by_excel" function prompts the user for the name of an Excel file in which the user wants to export the groups. The script then uses openpyxl to create the Excel file and uses the Pyrogram Client to extract the groups from the user's Telegram account using the "get_dialogs" function.

The "export_users_from_group" function prompts the user for a link to a Telegram group and the name of an Excel file in which to export the group's members. The script then uses the Pyrogram Client to get the group ID from the link and extract the group members using the "get_chat_members" function. It then uses openpyxl to write the members' usernames to the specified Excel file.

The "extract_ids" function prompts the user for a link to a Telegram group and the name of a file in which to export the group's member IDs. The script then uses the Pyrogram Client to get the group ID from the link and extract the group members' IDs using the "get_chat_members" function. It then writes the IDs to the specified file.

The "warmup_profile" function prompts the user for the number of times they want to send a message to a random chat. The script then uses the Pyrogram Client to extract a list of the user's chats, shuffles them randomly, and iterates through the list, sending a message to a random chat the specified number of times. This function is useful for "warming up" a Telegram account that is new or has not been used in a while, as Telegram may temporarily limit the account's functionality if it detects abnormal usage.

Finally, the "update_credentials" function prompts the user for the new API ID, API Hash, and phone number for the Telegram account being used. It then updates the configuration file (config.ini) with the new values and restarts the Pyrogram Client with the new credentials. This allows the user to switch to a different Telegram account or update their credentials if they change.

The script ends when the user enters 'exit'.

Overall, this script provides a convenient way for users to manage Telegram groups and users, and makes use of various libraries to handle different tasks such as reading and writing to Excel files, interacting with the Telegram API, and image manipulation.
