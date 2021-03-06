
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-list-events-for-a-configuration-v2-project-id-configurations-configuration-id-events:

List events for a configuration
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v2/{project_id}/configurations/{configuration_id}/events

Lists the events for the specified configuration.

This operation lists all the events for the specified configuration. You should consider these events to be transient because they might disappear after a minute or so. Therefore, this operation is most useful for monitoring a configuration's current events. 

Sample events that might be returned from this endpoint can be found in the descriptions for the following endpoints:



*  GET /v2/backups/{id}/events (See "List events for a backup".)
*  GET /v2/restores/{id}/events (See "List events for a restore".)




This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |OK                       |                         |
+--------------------------+-------------------------+-------------------------+
|400                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|401                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|403                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|405                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|409                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|500                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{project_id}              |String                   |Project ID of the user.  |
|                          |                         |Also referred to as the  |
|                          |                         |tenant ID or account ID. |
+--------------------------+-------------------------+-------------------------+
|{configuration_id}        |String *(Required)*      |Configuration ID. For    |
|                          |                         |example, ``7c8ee069-568f-|
|                          |                         |4d5a-932f-fb2af86b5fd5``.|
+--------------------------+-------------------------+-------------------------+



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|marker                    |String *(Optional)*      |ID of the event, for     |
|                          |                         |example, ``5152883998``. |
|                          |                         |Only events newer than   |
|                          |                         |the event specified by   |
|                          |                         |``marker`` are returned. |
|                          |                         |Use of ``marker`` is     |
|                          |                         |most useful when you are |
|                          |                         |continuously monitoring  |
|                          |                         |this endpoint for new    |
|                          |                         |events, so that old      |
|                          |                         |events are not repeated  |
|                          |                         |back to you in           |
|                          |                         |subsequent calls.        |
+--------------------------+-------------------------+-------------------------+
|limit                     |Integer *(Optional)*     |Number of events to      |
|                          |                         |list. The default value  |
|                          |                         |is 100.                  |
+--------------------------+-------------------------+-------------------------+
|sort_dir                  |String *(Optional)*      |Direction to sort the    |
|                          |                         |results. Valid values    |
|                          |                         |are ``asc`` and          |
|                          |                         |``desc``. The default    |
|                          |                         |value is ``desc``.       |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




**Example List events for a configuration: JSON request**


.. code::

   GET https://dfw.backup.api.rackspacecloud.com/v2/110011/configurations/7c8ee069-568f-4d5a-932f-fb2af86b5fd5/events?marker=5152883998&limit=100&sort_dir=desc HTTP/1.1
   Host: dfw.backup.api.rackspacecloud.com
   X-Auth-Token: 0f6e9f63600142f0a970911583522217
   Content-type: application/json





Response
""""""""""""""""





This table shows the body parameters for the response:

+-----------------------------+------------------------+-----------------------+
|Name                         |Type                    |Description            |
+=============================+========================+=======================+
|\ **events**                 |String                  |Information about      |
|                             |                        |events for the backup. |
+-----------------------------+------------------------+-----------------------+
|events.\ **id**              |String                  |ID of the event.       |
+-----------------------------+------------------------+-----------------------+
|events.\ **time**            |String                  |Time of the event.     |
+-----------------------------+------------------------+-----------------------+
|\ **event**s.\ **event**     |String                  |Type of the event.     |
+-----------------------------+------------------------+-----------------------+
|events.\ **agent**           |String                  |Information about the  |
|                             |                        |agent for each         |
|                             |                        |``event``.             |
+-----------------------------+------------------------+-----------------------+
|events.agent.\ **id**        |String                  |ID of the agent.       |
+-----------------------------+------------------------+-----------------------+
|events.agent.\ **vault**     |String                  |Information about the  |
|                             |                        |vault for the backup.  |
+-----------------------------+------------------------+-----------------------+
|events.agent.vault.\ **id**  |String                  |ID of the vault.       |
+-----------------------------+------------------------+-----------------------+
|events.agent.vault.\         |String                  |Indicates if the vault |
|**encrypted**                |                        |is encrypted.          |
+-----------------------------+------------------------+-----------------------+
|events.\ **configuration**   |String                  |Information about the  |
|                             |                        |configuration for each |
|                             |                        |``event``.             |
+-----------------------------+------------------------+-----------------------+
|events.configuration.\ **id**|String                  |ID of the              |
|                             |                        |configuration.         |
+-----------------------------+------------------------+-----------------------+
|events.\ **backup**          |String                  |Information about the  |
|                             |                        |backup for each        |
|                             |                        |``event``.             |
+-----------------------------+------------------------+-----------------------+
|events.backup.\ **id**       |String                  |ID of the backup.      |
+-----------------------------+------------------------+-----------------------+
|events.backup.\              |String                  |ID of the snapshot.    |
|**snapshot_id**              |                        |                       |
+-----------------------------+------------------------+-----------------------+
|events.\ **restore**         |String                  |Information about the  |
|                             |                        |restore.               |
+-----------------------------+------------------------+-----------------------+
|events.restore.\ **id**      |String                  |ID of the restore.     |
+-----------------------------+------------------------+-----------------------+
|events.restore.\             |String                  |Destination path for   |
|**destination_path**         |                        |the restore.           |
+-----------------------------+------------------------+-----------------------+
|events.restore.\             |String                  |Specifies whether      |
|**overwrite_files**          |                        |existing files were    |
|                             |                        |overwritten during the |
|                             |                        |restore.               |
+-----------------------------+------------------------+-----------------------+
|events.restore.\             |String                  |Resources included in  |
|**inclusions**               |                        |the restore.           |
+-----------------------------+------------------------+-----------------------+
|events.restore.inclusions.\  |String                  |Type of resources      |
|**type**                     |                        |included in the        |
|                             |                        |restore.               |
+-----------------------------+------------------------+-----------------------+
|events.restore.inclusions.\  |String                  |Path to the resources  |
|**path**                     |                        |included in the        |
|                             |                        |restore.               |
+-----------------------------+------------------------+-----------------------+
|events.restore.\             |String                  |Resources excluded     |
|**exclusions**               |                        |from the restore.      |
+-----------------------------+------------------------+-----------------------+
|events.restore.exclusions.\  |String                  |Type of resources      |
|**type**                     |                        |excluded from the      |
|                             |                        |restore.               |
+-----------------------------+------------------------+-----------------------+
|events.restore.exclusions.\  |String                  |Path of the resources  |
|**path**                     |                        |excluded from the      |
|                             |                        |restore.               |
+-----------------------------+------------------------+-----------------------+
|events.\ **request_id**      |String                  |ID of the request.     |
+-----------------------------+------------------------+-----------------------+
|events.\ **bytes_completed** |String                  |Number of bytes        |
|                             |                        |completed.             |
+-----------------------------+------------------------+-----------------------+
|events.\ **bytes_remaining** |String                  |Number of bytes        |
|                             |                        |remaining.             |
+-----------------------------+------------------------+-----------------------+
|events.\ **total_bytes**     |String                  |Number of total bytes. |
+-----------------------------+------------------------+-----------------------+
|events.\ **path**            |String                  |Path for browse        |
|                             |                        |request.               |
+-----------------------------+------------------------+-----------------------+
|events.\ **path_encoded**    |String                  |Encoded path for the   |
|                             |                        |browse request.        |
+-----------------------------+------------------------+-----------------------+
|events.\                     |String                  |Encrypted password in  |
|**encrypted_password_hex**   |                        |hexadecimal notation.  |
+-----------------------------+------------------------+-----------------------+
|\ **links**                  |String                  |Link information for   |
|                             |                        |the next and previous  |
|                             |                        |events.                |
+-----------------------------+------------------------+-----------------------+
|links.\ **href**             |String                  |Location (URI).        |
+-----------------------------+------------------------+-----------------------+
|links.\ **rel**              |String                  |How the href link      |
|                             |                        |provided is related to |
|                             |                        |this resource URI.     |
+-----------------------------+------------------------+-----------------------+







**Example List events for a configuration: JSON response**


.. code::

   200 (OK)
   Content-Type: application/json


.. code::

   {
       "events": [
           {
               "id": "282856406",
               "time": "2014-10-21T15:21:42.971997Z",
               "event": "restore_start_request",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "source_agent": {
                   "vault": {
                       "id": "7cd999c3-a0c3-4985-99d4-42b544685456",
                       "encrypted": true
                   }
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "snapshot_id": 1111
               },
               "restore": {
                   "id": "e87e6f7d-d166-11e4-8689-c8e0eb190e3d",
                   "destination_path": "/tmp/restore",
                   "overwrite_files": false,
                   "inclusions": [
                       {
                           "type": "folder",
                           "path": "/web/"
                       },
                       {
                           "type": "file",
                           "path": "/etc/web/app.conf"
                       }
                   ],
                   "exclusions": [
                       {
                           "type": "folder",
                           "path": "/web/cache/"
                       },
                       {
                           "type": "file",
                           "path": "/web/cache.jpg"
                       }
                   ]
               },
               "request_id": "09be2f14-e9cd-466c-ade8-b3a81d6d12a8"
           },
           {
               "id": "5152883867",
               "time": "2014-08-05T18:22:21.238641Z",
               "event": "backup_start_request",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d"
               },
               "request_id": "d459cff6-777a-4515-b042-9288c841f557"
           },
           {
               "id": "5152883868",
               "time": "2014-08-05T18:22:22.238641Z",
               "event": "backup_queued",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d"
               }
           },
           {
               "id": "5152883922",
               "time": "2014-08-05T18:22:23.238641Z",
               "event": "backup_preparing",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d"
               }
           },
           {
               "id": "5152883969",
               "time": "2014-08-05T18:22:24.238641Z",
               "event": "backup_in_progress",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d"
               }
           },
           {
               "id": "5152883978",
               "time": "2014-08-05T18:22:59.238641Z",
               "event": "backup_progress",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d"
               },
               "bytes_completed": 1,
               "bytes_remaining": 3,
               "total_bytes": 4
           },
           {
               "id": "5152883998",
               "time": "2014-08-05T18:23:50.489715Z",
               "event": "backup_completed",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d"
               }
           },
           {
               "id": "5152883998",
               "time": "2014-08-05T18:23:50.489715Z",
               "event": "backup_failed",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d"
               }
           },
           {
               "id": "5152883998",
               "time": "2014-08-05T18:23:50.489715Z",
               "event": "backup_missed",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d"
               }
           },
           {
               "id": "5152883998",
               "time": "2014-08-05T18:23:50.489715Z",
               "event": "backup_skipped",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d"
               }
           },
           {
               "id": "5152883999",
               "time": "2014-08-05T18:23:51.489715Z",
               "event": "backup_stop_request",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d"
               }
           },
           {
               "id": "5152884000",
               "time": "2014-10-07T14:34:04.376357Z",
               "event": "backup_stopped",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97"
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "id": "0d95d699-d16b-11e4-93bd-c8e0eb190e3d"
               }
           },
           {
               "id": "5152884001",
               "time": "2014-10-07T14:34:05.376357Z",
               "event": "backup_browse",
               "agent": {
                   "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97",
                   "vault": {
                       "id": "7cd999c3-a0c3-4985-99d4-42b544685456",
                       "encrypted": true
                   }
               },
               "configuration": {
                   "id": "7c8ee069-568f-4d5a-932f-fb2af86b5fd5"
               },
               "backup": {
                   "snapshot_id": 1111
               },
               "request_id": "ae7528c8-bcc3-4356-a237-f20fbdd79ee4",
               "path": "/path/to/browse",
               "path_encoded": "/optional/base64encoded/path/if/non-utf-8/characters/present",
               "encrypted_password_hex": "0bff42a526c78076a3d986fa75eecd 83211f166fd7692797cdde2317faee544e3300614fd54b8c0d81f975 3e58cb1ffbd62d3faf0d2bf52e79ce5cd9c6d84b5295e3dea629e71b 0a5e26efda50ff8e05a5475bb7cbd553d238c05655f56ece2df070ce 374ff1e0724827c2300e373241e94c4bc13441561604e3e70b5034eb 58d717864f304c9c73b6d1d46c4276d7ec2f0e2bd9a42a8ab0ba99eb adda84f4cbb5b3611bd319627436246912139c2dde62bd00528b1464 20dceae949d1926ae05fc7df9b474e1ee176f89069fb424b12f8f357 e6e2909ba05152e9f72a68de0046b3e1520838ff5e723af02a96f51a c1e6ef4254226249b872676af76a319cbe"
           }
       ],
       "links": [
           {
               "href": "https://cloudbackupapi.apiary-mock.com/v2/backups/0d95d699-d16b-11e4-93bd-c8e0eb190e3d/events?marker=5152884001",
               "rel": "next"
           },
           {
               "href": "https://cloudbackupapi.apiary-mock.com/v2/backups/0d95d699-d16b-11e4-93bd-c8e0eb190e3d/events?marker=5152883867&sort_dir=desc",
               "rel": "previous"
           }
       ]
   }




