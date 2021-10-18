## Overview
1. [User Role Mappings](#1-user-role-mappings)
2. [Security AD-Groups](#2-security-ad-groups)
3. [Distribution Groups](#3-distribution-groups)
4. Wiki-Page: [How to maintain user groups and role assignments](/How to assign user roles in PRIMA)

<br>
<br>

## 1. User Role Mappings

**Matrix**:
[User_Roles_Mapping_2020-07-01.xlsx](uploads/b5c392f614397542cafc11bb9b5103c3/User_Roles_Mapping_2020-07-01.xlsx)

In general:

| **CWID** | **Role**  | **Application** |
| -------- | --------- | --------------- |
| 1st      | WRITER    | CoA/PC          | 
| 2nd      | ADMIN     | CoA/PC          | 
| 3rd      | APPROVER  | CoA/PC          | 
| 4th      | gARM-User (CoA) / Hierarchy-Maintainer (ProfitCenter)  | CoA/PC |


To check your current group-mappings, you can run following command on command line: `net user %USERNAME% /domain`

![get_group_membership](uploads/676bc78423f95c6666b45a651f88b316/get_group_membership.png)
<br>
[[go up to Overview]](#overview)
<br>
<br>

## 2. Security AD-Groups
| **AD-Group**                 | **AD-Role**              | **CWID** | **Members**        | **Description**         |  
| ---------------------------- | ------------------------ | -------- | ------------------ | ----------------------- |
| **GBOX-COA-DEPLOY**          | ROLE_GBOX-COA-DEPLOY     | 2nd      | SPOC + SUPPORT     | required to get access to 'BY0PWQ\wwwroot' folder on PROD-server. |
| **GBOX_DB_ADMIN**            | ROLE_GBOX_DB_ADMIN       | 2nd      | SPOC + SUPPORT     | required to get admin rights for GBOX databases MDRS |
| **GBOX_DB_WRITER**           | ROLE_GBOX_DB_WRITER      | 2nd      | SPOC + SUPPORT     | required to get writer rights for GBOX databases MDRS |
| **GBOX_DB_WRITER_DQ**        | no role available        | 1st      | ALL                | required to get writer rights for all GBOX databases MDRS_D, MDRS_Q, MDRS_20_X |
| **GBOX_COA_DB_READER**       | no role available        | 1st      | ALL                | required to get admin rights for GBOX databases MDRS_P |
| **GBOX_COA_DB_WRITER**       | ROLE_GBOX-COA-DB_WRITER  | 1st      | SPOC + SUPPORT     | required to get writer rights for GBOX databases MDRS_P |
| **GBOX_IMP_MANAGER**         | no role available        | 1st      | DRS-Team + SUPPORT | required for **GBox Cockpit** and **GBox Manager** deployment on: `\\BY8116\by-swp101019_by-gbox.bayer-ag.com`, `\\BY8116\by-swp101020_by-dbox.bayer-ag.com`, `\\BY8116\by-swp101021_by-qbox.bayer-ag.com`. As the group **GBOX_TFS_ADMIN** is also member of the **GBOX_IMP_MANAGER**, user will also get access to TFS-repository as well. |
| **MDAS-DI-CG**               | no role available        | 1st      | ALL                | required to maintain the GBox Wiki at http://go/gboxwiki |
| **GBOX_TFS_ADMIN**           | no role available        | 1st      | DRS-Team + SUPPORT | required to maintain TFS repository, which is used for GBOX Manager and GBOX Cockpit. To gain access to TFS repository for that user BBS needs to raise a requested via DRM4SDI (refer to: [Wiki-Page: System Access > TFS](https://by-gitlab.de.bayer.cnb/IMSMA/GBox/wikis/system%20access#tfs)). |
| **EDM_Gitlab_Developer_ext** | no role available        | 1st      | ALL                | required for accessing the 'new' [GitLab Repository](https://by-gitlab.de.bayer.cnb/edm/solutions/code/gbox). This can be done by a SPOC via a self service request in PRIMA. |

How to edit GBox-Wiki:
![edit_gbox_wiki](uploads/221dda7906665ea8c2207899dfa3516f/edit_gbox_wiki.png)

<br>
[[go up to Overview]](#overview)
<br>
<br>

## 3. Distribution Groups

**GBOX_COA_SUPPORT-EMAIL** is required to get status mails from TWS team, which inform us about failed/succeed distribution jobs for global group/validation and profit center distribution. This membership is required for [monitoring task](/Monitoring Tasks#perform-monitoring-4-hierarchy-distribution).
<br>
[[go up to Overview]](#overview)
<br>
<br>