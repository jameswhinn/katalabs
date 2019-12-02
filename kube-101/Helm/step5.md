Now that Redis is running, let's take it back down.

``helm delete my-redis --purge``{{execute}}

No matter how complex the chart, the delete command will undo everything the install provisioned. The --purge command is used to remove the record. Without the purge the record of the installation will remain for reference.

Next, explore the wealth of charts available.