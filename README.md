# OWL-Automation-Support
This app is to support complex scenarios in owl automation

# Plugin Installation:
* In the target environment, log in as the deployment user.
* Navigate to the Admin Console.
* On the left side of the console, click Plug-ins.
* Click ADD NEW PLUG-INS.
![ADD NEW PLUGIN](https://github.com/mukundanramesh/OWL-Automation-Support/blob/main/Images/Add%20New%20Plugins.png)
* Search for the plug-in by name - Content Tools.
![SEARCH PLUGIN](https://github.com/mukundanramesh/OWL-Automation-Support/blob/main/Images/Search%20Plugin.png)
* Click on the plug-in name.
* Click DEPLOY.
![DEPLOY PLUGIN](https://github.com/mukundanramesh/OWL-Automation-Support/blob/main/Images/Deploy%20Plugin.png)


# App Import and Changes in the Interface(s)
* Download the App OWL Automation Support from here - Owl Automation Support.zip
* Import the App to the site.
* After successful import open the interface - OAS_OWL_dev_tool_sync_all_records_ui
* Delete and re-enter the function name getconstantvaluebyname in lines 8 and 54.
![INTERFACE CHANGES](https://github.com/mukundanramesh/OWL-Automation-Support/blob/main/Images/Changes%20in%20Interface.png)

# How to use OWL Support Tool
* Once the app is imported the Site **OWL Support Tool** will be available in the widget menu.
![SITE HOME PAGE](https://github.com/mukundanramesh/OWL-Automation-Support/blob/main/Images/OWL%20Support%20Tool%20-%20Home%20Page.png)
* Create Stored Porcedures for either Delete , Truncate or Insert.
![STORED-PROCEDURE](https://github.com/mukundanramesh/OWL-Automation-Support/blob/main/Images/Stored%20Procedure%20Creation.png)
    * Example 1:
        '''
            DELIMITER $$
            CREATE DEFINER=`dbadmin`@`%` PROCEDURE `OWL_Delete_ACR_Tables`()
            BEGIN
            SET foreign_key_checks = 0;
            delete from CMGT_ACR_ASSIGNMENT_RULE where CREATED_ON between NOW() - INTERVAL 7 DAY and NOW();
            delete from CMGT_ACR_RULE_CONDITION where CREATED_ON between NOW() - INTERVAL 7 DAY and NOW();
            delete from CMGT_ACR_RULE_CONDITION_SET where CREATED_ON between NOW() - INTERVAL 7 DAY and NOW();
            delete from CMGT_ACR_USERS_TO_EXCLUDE where CREATED_ON between NOW() - INTERVAL 7 DAY and NOW();
            delete from CMGT_ACR_CASE_ASSIGNMENT_HISTORY where CREATED_ON between NOW() - INTERVAL 7 DAY and NOW();
            SET foreign_key_checks = 1;
            END$$
            DELIMITER ;
        '''

    * Example 2:
        '''
            DELIMITER $$
            CREATE DEFINER=`dbadmin`@`%` PROCEDURE `OWL_Truncate_ACR_Tables`()
            BEGIN
            SET foreign_key_checks = 0;
            truncate table CMGT_ACR_ASSIGNMENT_RULE;
            truncate table CMGT_ACR_RULE_CONDITION;
            truncate table CMGT_ACR_RULE_CONDITION_SET;
            truncate table CMGT_ACR_USERS_TO_EXCLUDE;
            truncate table CMGT_ACR_CASE_ASSIGNMENT_HISTORY;
            SET foreign_key_checks = 1;
            END$$
        '''

* Create constants for the created stored procedures.
![CONSTANT-STORED-PROCEDURE](https://github.com/mukundanramesh/OWL-Automation-Support/blob/main/Images/Constant-Stored%20Procedure.png)
* Create constants for the Record Types.
![CONSTANT-RECORD-TYPES](https://github.com/mukundanramesh/OWL-Automation-Support/blob/main/Images/Constant-Record%20Types.png)
* Use the created Constants in the **OWL Support Tool** site to delete records in the table and Sync the Record Types.
![USING CONSTANTS](https://github.com/mukundanramesh/OWL-Automation-Support/blob/main/Images/Delete%20and%20Sync%20Records.png)
* Upon Successful deletion **Deletion Successful!!** message will be displayed
![USING CONSTANTS](https://github.com/mukundanramesh/OWL-Automation-Support/blob/main/Images/Deletion%20Successful.png)
