### Running application pools as a specific user

You can usually get by running your application pools as the `ApplicationPoolIdentity` accounts. This creates a virtual account for each different application pool automatically, isolating them from each other. On the local machine, you can grant access to resources like the file system to each separate application pool. For remote resources (like a SQL Server on a different machine), the application pool identities act as Network Service, so you can grant access at the machine level. Learn more about [application pool identities](https://www.iis.net/learn/manage/configuring-security/application-pool-identities). 

For more control over what the application pool can do, you should run it under a specific, custom user account. You'll want to use [`aspnet_regiis`](https://msdn.microsoft.com/en-us/library/k6h9cz8h.aspx) to give your custom account all the permissions it needs to run as an application pool and execute ASP.NET requests. You can then set your application pool to run as that user.