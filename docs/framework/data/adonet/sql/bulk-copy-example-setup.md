---
title: Příklad nastavení hromadného kopírování
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 28fa5cde1dcbaf9f38450116a56fc11d904edc1c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040254"
---
# <a name="bulk-copy-example-setup"></a>Příklad nastavení hromadného kopírování
Třídu <xref:System.Data.SqlClient.SqlBulkCopy> lze použít k zápisu dat pouze do tabulek SQL Server. Ukázky kódu uvedené v tomto tématu používají ukázkovou databázi SQL Server **AdventureWorks**. Aby nedošlo ke změně kódů stávajících tabulek, zapište data do tabulek, které je třeba vytvořit jako první.  
  
 Tabulky **BulkCopyDemoMatchingColumns** a **BulkCopyDemoDifferentColumns** jsou založené na tabulce **AdventureWorks** **produkce. Products** . V ukázkách kódu, které používají tyto tabulky, jsou data přidána z tabulky **produkčních produktů** do jedné z těchto ukázkových tabulek. Tabulka **BulkCopyDemoDifferentColumns** se používá, když Ukázka ukazuje, jak namapovat sloupce ze zdrojových dat do cílové tabulky. **BulkCopyDemoMatchingColumns** se používá pro většinu ostatních vzorků.  
  
 Několik ukázek kódu ukazuje, jak použít jednu <xref:System.Data.SqlClient.SqlBulkCopy> třídu k zápisu do více tabulek. Pro tyto ukázky se jako cílové tabulky používají tabulky **BulkCopyDemoOrderHeader** a **BulkCopyDemoOrderDetail** . Tyto tabulky jsou založené na tabulkách **Sales. SalesOrderHeader** a **Sales. SalesOrderDetail** v **AdventureWorks**.  
  
> [!NOTE]
> Ukázky kódu **SqlBulkCopy** jsou k dispozici k předvedení syntaxe pouze použití **SqlBulkCopy** . Pokud se zdrojové a cílové tabulky nacházejí ve stejné instanci SQL Server, je snazší a rychlejší použít příkaz Transact-SQL `INSERT … SELECT` ke zkopírování dat.  
  
## <a name="table-setup"></a>Nastavení tabulky  
 Chcete-li vytvořit tabulky potřebné pro správné spuštění ukázek kódu, je nutné spustit následující příkazy jazyka Transact-SQL v databázi SQL Server.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Operace hromadného kopírování na SQL Serveru](bulk-copy-operations-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
