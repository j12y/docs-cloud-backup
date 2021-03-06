
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-start-a-cleanup-v2-project-id-cleanups:

Start a cleanup
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v2/{project_id}/cleanups

Starts a cleanup. 

This operation starts a cleanup. Start a cleanup by specifying one of the following states: 

* ``start_requested`` : A manual cleanup is requested by a user.
* ``start_scheduled`` : A scheduled cleanup is started by the agent.






This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |                         |
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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|\ **agent_id**            |String *(Required)*      |ID of the agent.         |
+--------------------------+-------------------------+-------------------------+
|\ **state**               |String *(Required)*      |Cleanup state, either    |
|                          |                         |``start_requested``, a   |
|                          |                         |manual backup requested  |
|                          |                         |by a user, or            |
|                          |                         |``start_scheduled``, a   |
|                          |                         |scheduled backup started |
|                          |                         |by the agent.            |
+--------------------------+-------------------------+-------------------------+





**Example Start a cleanup: JSON request**


.. code::

   POST https://dfw.backup.api.rackspacecloud.com/v2/110011/cleanups HTTP/1.1
   Host: dfw.backup.api.rackspacecloud.com
   X-Auth-Token: 0f6e9f63600142f0a970911583522217
   Content-type: application/json


.. code::

   {
       "agent_id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97",
       "state": "start_requested"
   }





Response
""""""""""""""""





This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|\ **project_id**          |String                   |ID of the project.       |
+--------------------------+-------------------------+-------------------------+
|\ **id**                  |String                   |ID of the cleanup.       |
+--------------------------+-------------------------+-------------------------+
|\ **agent**               |String                   |Information about the    |
|                          |                         |agent for the cleanup.   |
+--------------------------+-------------------------+-------------------------+
|agent.\ **id**            |String                   |ID of the agent.         |
+--------------------------+-------------------------+-------------------------+
|agent.\ **links**         |String                   |Link information about   |
|                          |                         |the agent.               |
+--------------------------+-------------------------+-------------------------+
|agent.links.\ **href**    |String                   |Location (URI) of the    |
|                          |                         |agent.                   |
+--------------------------+-------------------------+-------------------------+
|agent.links.\ **rel**     |String                   |How the href link        |
|                          |                         |provided is related to   |
|                          |                         |this resource URI.       |
+--------------------------+-------------------------+-------------------------+
|\ **state**               |String                   |State of the cleanup,    |
|                          |                         |for example,             |
|                          |                         |``start_requested``.     |
+--------------------------+-------------------------+-------------------------+
|\ **started_time**        |String                   |Time the cleanup started.|
+--------------------------+-------------------------+-------------------------+
|\ **ended_time**          |String                   |Time the cleanup ended.  |
+--------------------------+-------------------------+-------------------------+
|\ **snapshot_ids**        |String                   |IDs of the snapshots.    |
+--------------------------+-------------------------+-------------------------+
|\ **errors**              |String                   |Information about errors.|
+--------------------------+-------------------------+-------------------------+
|errors.\ **count**        |String                   |Number of errors.        |
+--------------------------+-------------------------+-------------------------+
|errors.\ **reason**       |String                   |Cause of the error; for  |
|                          |                         |example, ``Error         |
|                          |                         |deleting object. Server  |
|                          |                         |returned HTTP 503.``     |
+--------------------------+-------------------------+-------------------------+
|errors.\ **diagnostics**  |String                   |Additional information   |
|                          |                         |about the cause of the   |
|                          |                         |error if available.      |
+--------------------------+-------------------------+-------------------------+
|errors.\ **links**        |String                   |Links for information    |
|                          |                         |about the errors.        |
+--------------------------+-------------------------+-------------------------+
|errors.links.\ **href**   |String                   |Location (URI) of the    |
|                          |                         |errors.                  |
+--------------------------+-------------------------+-------------------------+
|errors.links.\ **rel**    |String                   |How the href link        |
|                          |                         |provided is related to   |
|                          |                         |this resource URI.       |
+--------------------------+-------------------------+-------------------------+
|\ **bytes_before**        |String                   |Number of bytes before   |
|                          |                         |the cleanup.             |
+--------------------------+-------------------------+-------------------------+
|\ **bytes_after**         |String                   |Number of bytes after    |
|                          |                         |the cleanup.             |
+--------------------------+-------------------------+-------------------------+
|\ **links**               |String                   |Links with information   |
|                          |                         |about the cleanups.      |
+--------------------------+-------------------------+-------------------------+
|links.\ **href**          |String                   |Location (URI) of the    |
|                          |                         |cleanups.                |
+--------------------------+-------------------------+-------------------------+
|links.\ **rel**           |String                   |How the href link        |
|                          |                         |provided is related to   |
|                          |                         |this resource URI.       |
+--------------------------+-------------------------+-------------------------+







**Example Start a cleanup: JSON response**


.. code::

   201 (Created)
   Location: https://cloudbackupapi.apiary-mock.com/v2/cleanups/2f8708b3-d16b-11e4-bc22-c8e0eb190e3d


.. code::

   {
       "project_id": "123456",
       "id": "2f8708b3-d16b-11e4-bc22-c8e0eb190e3d",
       "agent": {
           "id": "8f135b4f-7a69-4b8a-947f-5e80d772fd97",
           "links": [
               {
                   "href": "https://cloudbackupapi.apiary-mock.com/v2/agents/8f135b4f-7a69-4b8a-947f-5e80d772fd97", 
                   "rel": "full"
               }
           ]
       },
       "state": "start_requested",
       "started_time": null,
       "ended_time": null,
       "snapshot_ids": [],
       "errors": {
           "count": 0,
           "reason": "",
           "diagnostics": "",
           "links": [
               {
                   "href": "https://cloudbackupapi.apiary-mock.com/v2/cleanups/2f8708b3-d16b-11e4-bc22-c8e0eb190e3d/errors",
                   "rel": "full"
               }
           ]
       },
       "bytes_before": 0,
       "bytes_after": 0,
       "links": [
           {
               "href": "https://cloudbackupapi.apiary-mock.com/v2/cleanups/2f8708b3-d16b-11e4-bc22-c8e0eb190e3d",
               "rel": "self"
           },
           {
               "href": "https://cloudbackupapi.apiary-mock.com/v2/cleanups/2f8708b3-d16b-11e4-bc22-c8e0eb190e3d/events",
               "rel": "events"
           }
       ]
   }




