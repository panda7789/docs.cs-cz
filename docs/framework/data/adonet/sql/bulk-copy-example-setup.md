---
title: Příklad nastavení hromadného kopírování
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 80350d112da03c00e422432ce271ca5ea3ac58ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148839"
---
# <a name="bulk-copy-example-setup"></a>Příklad nastavení hromadného kopírování
Třídu <xref:System.Data.SqlClient.SqlBulkCopy> lze použít k zápisu dat pouze do tabulek serveru SQL Server. Ukázky kódu zobrazené v tomto tématu používají ukázkovou databázi serveru SQL Server **AdventureWorks**. Chcete-li se vyhnout změně existující tabulky ukázky kódu zápis dat do tabulek, které je nutné vytvořit jako první.  
  
 **BulkCopyDemoMatchingColumns** a **BulkCopyDemoDifferentColumns** tabulky jsou založeny na **AdventureWorks** **Production.Products** tabulky. Ve vzorcích kódu, které používají tyto tabulky, jsou data přidána z tabulky **Production.Products** do jedné z těchto ukázkových tabulek. **BulkCopyDemoDifferentColumns** tabulka se používá, když ukázka ukazuje, jak mapovat sloupce ze zdrojových dat do cílové tabulky; **BulkCopyDemoMatchingColumns** se používá pro většinu ostatních vzorků.  
  
 Několik ukázek kódu ukazuje, jak <xref:System.Data.SqlClient.SqlBulkCopy> použít jednu třídu k zápisu do více tabulek. Pro tyto ukázky **bulkcopydemoorderheader** a **bulkcopydemoorderdetail** tabulky se používají jako cílové tabulky. Tyto tabulky jsou založeny na tabulkách **Sales.SalesOrderHeader** a **Sales.SalesOrderDetail** v **adventureworks**.  
  
> [!NOTE]
> **SqlBulkCopy** kód ukázky jsou k dispozici k předvedení syntaxe pro použití **pouze SqlBulkCopy.** Pokud jsou zdrojové a cílové tabulky umístěny ve stejné instanci serveru SQL `INSERT … SELECT` Server, je jednodušší a rychlejší zkopírovat data příkazu Transact-SQL.  
  
## <a name="table-setup"></a>Nastavení tabulky  
 Chcete-li vytvořit tabulky nezbytné pro správné spuštění ukázek kódu, je nutné spustit následující příkazy Transact-SQL v databázi serveru SQL Server.  
  
```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a>Viz také

- [Operace hromadného kopírování na SQL Serveru](bulk-copy-operations-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
