---
title: Hromadné kopírování příklad instalace
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: cb4e92529c8e68bd7e47e5943f7e79dcc97603e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362436"
---
# <a name="bulk-copy-example-setup"></a>Hromadné kopírování příklad instalace
<xref:System.Data.SqlClient.SqlBulkCopy> Třída slouží k zápisu dat pouze na tabulky serveru SQL Server. Ukázky kódu, které jsou uvedené v tomto tématu použijte ukázkové databáze systému SQL Server, **AdventureWorks**. Aby se zabránilo Změna stávající tabulce ukázky kódu zápisu dat do tabulky, které je nutné nejprve vytvořit.  
  
 **BulkCopyDemoMatchingColumns** a **BulkCopyDemoDifferentColumns** obou tabulkách jsou založené na **AdventureWorks** **Production.Products**  tabulky. V ukázky kódu, které používají tyto tabulky, je přidán dat z **Production.Products** tabulky na jednu z těchto ukázkové tabulky. **BulkCopyDemoDifferentColumns** tabulky se používá při ukázku ukazuje, jak k mapování sloupců ze zdrojových dat do cílové tabulky; **BulkCopyDemoMatchingColumns** se používá u většiny ostatních vzorků.  
  
 Několik ukázky kódu ukazují, jak použít jednu <xref:System.Data.SqlClient.SqlBulkCopy> třída pro psaní k několika tabulkám. Pro tyto ukázky **BulkCopyDemoOrderHeader** a **BulkCopyDemoOrderDetail** tabulky se používají jako cílové tabulky. Tyto tabulky jsou založené na **Sales.SalesOrderHeader** a **Sales.SalesOrderDetail** tabulky v **AdventureWorks**.  
  
> [!NOTE]
>  **SqlBulkCopy** ukázky kódu jsou k dispozici k předvedení syntaxe pro používání **SqlBulkCopy** pouze. Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je snadnější a rychlejší pomocí jazyka Transact-SQL `INSERT … SELECT` příkaz Kopírovat data.  
  
## <a name="table-setup"></a>Nastavení tabulky  
 Pokud chcete vytvořit tabulky nezbytné pro správné fungování ukázky kódu, musíte spustit následující příkazy jazyka Transact-SQL v databázi systému SQL Server.  
  
```  
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
 [Operace hromadného kopírování na SQL Serveru](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
