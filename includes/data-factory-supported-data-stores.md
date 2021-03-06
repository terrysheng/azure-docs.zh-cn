数据工厂中的复制活动可以将数据从源数据存储复制到接收器数据存储。 数据工厂支持以下数据存储。 来自任何源的数据都可以写入到任何接收器。 单击某个数据存储即可了解如何将数据复制到该存储，以及如何从该存储复制数据。

| 类别 | 数据存储 | 支持用作源 | 支持用作接收器 |
|:--- |:--- |:--- |:--- |
| Azure |[Azure Blob 存储](../articles/data-factory/data-factory-azure-blob-connector.md) <br/> [Azure Data Lake Store](../articles/data-factory/data-factory-azure-datalake-connector.md) <br/> [Azure SQL 数据库](../articles/data-factory/data-factory-azure-sql-connector.md) <br/> [Azure SQL 数据仓库](../articles/data-factory/data-factory-azure-sql-data-warehouse-connector.md) <br/> [Azure 表存储](../articles/data-factory/data-factory-azure-table-connector.md) <br/> [Azure DocumentDB](../articles/data-factory/data-factory-azure-documentdb-connector.md) <br/> |✓ <br/> ✓ <br/> ✓ <br/> ✓ <br/> ✓ <br/> ✓ |✓ <br/> ✓ <br/> ✓ <br/> ✓ <br/> ✓ <br/> ✓ |
| 数据库 |[SQL Server](../articles/data-factory/data-factory-sqlserver-connector.md)\* <br/> [Oracle](../articles/data-factory/data-factory-onprem-oracle-connector.md)\* <br/> [MySQL](../articles/data-factory/data-factory-onprem-mysql-connector.md)\* <br/> [DB2](../articles/data-factory/data-factory-onprem-db2-connector.md)\* <br/> [Teradata](../articles/data-factory/data-factory-onprem-teradata-connector.md)\* <br/> [PostgreSQL](../articles/data-factory/data-factory-onprem-postgresql-connector.md)\* <br/> [Sybase](../articles/data-factory/data-factory-onprem-sybase-connector.md)\* <br/>[Cassandra](../articles/data-factory/data-factory-onprem-cassandra-connector.md)\* <br/>[MongoDB](../articles/data-factory/data-factory-on-premises-mongodb-connector.md)\*<br/>[Amazon Redshift](../articles/data-factory/data-factory-amazon-redshift-connector.md) |✓ <br/> ✓ <br/> ✓ <br/> ✓ <br/> ✓ <br/> ✓<br/> ✓ <br/> ✓ <br/> ✓ <br/> ✓ |✓ <br/> ✓ <br/> &nbsp; <br/> &nbsp; <br/> &nbsp; <br/> &nbsp;<br/> &nbsp;<br/> &nbsp;<br/> &nbsp; <br/>&nbsp; |
| 文件 |[文件系统](../articles/data-factory/data-factory-onprem-file-system-connector.md)\* <br/> [HDFS](../articles/data-factory/data-factory-hdfs-connector.md)\* <br/> [Amazon S3](../articles/data-factory/data-factory-amazon-simple-storage-service-connector.md) <br/> [FTP](../articles/data-factory/data-factory-ftp-connector.md) |✓ <br/> ✓ <br/> ✓ <br/> ✓ |✓ <br/> &nbsp;<br/>&nbsp; |
| 其他 |[Salesforce](../articles/data-factory/data-factory-salesforce-connector.md)<br/> [泛型 ODBC](../articles/data-factory/data-factory-odbc-connector.md)\* <br/> [泛型 OData](../articles/data-factory/data-factory-odata-connector.md) <br/> [Web 表（HTML 中的表）](../articles/data-factory/data-factory-web-table-connector.md) <br/> [GE Historian](../articles/data-factory/data-factory-odbc-connector.md#ge-historian-store)* |✓ <br/> ✓ <br/> ✓ <br/> ✓ <br/> ✓ |&nbsp; <br/> &nbsp; <br/> &nbsp; <br/> &nbsp;<br/> &nbsp;<br/> &nbsp; |

> [!NOTE]
> 带 * 的数据存储既可位于本地，也可位于 Azure IaaS 上，需要用户在本地/Azure IaaS 计算机上安装[数据管理网关](../articles/data-factory/data-factory-data-management-gateway.md)。
> 
> 



<!--HONumber=Nov16_HO2-->


