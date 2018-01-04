---
title: "Hromadné kopírování příklad instalace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dafbb4012eabda5eb437ec077d571fc28c3e806b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="04b02-102">Hromadné kopírování příklad instalace</span><span class="sxs-lookup"><span data-stu-id="04b02-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="04b02-103"><xref:System.Data.SqlClient.SqlBulkCopy> Třída slouží k zápisu dat pouze na tabulky serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04b02-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="04b02-104">Ukázky kódu, které jsou uvedené v tomto tématu použijte ukázkové databáze systému SQL Server, **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="04b02-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="04b02-105">Aby se zabránilo Změna stávající tabulce ukázky kódu zápisu dat do tabulky, které je nutné nejprve vytvořit.</span><span class="sxs-lookup"><span data-stu-id="04b02-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="04b02-106">**BulkCopyDemoMatchingColumns** a **BulkCopyDemoDifferentColumns** obou tabulkách jsou založené na **AdventureWorks** **Production.Products**  tabulky.</span><span class="sxs-lookup"><span data-stu-id="04b02-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="04b02-107">V ukázky kódu, které používají tyto tabulky, je přidán dat z **Production.Products** tabulky na jednu z těchto ukázkové tabulky.</span><span class="sxs-lookup"><span data-stu-id="04b02-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="04b02-108">**BulkCopyDemoDifferentColumns** tabulky se používá při ukázku ukazuje, jak k mapování sloupců ze zdrojových dat do cílové tabulky; **BulkCopyDemoMatchingColumns** se používá u většiny ostatních vzorků.</span><span class="sxs-lookup"><span data-stu-id="04b02-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="04b02-109">Několik ukázky kódu ukazují, jak použít jednu <xref:System.Data.SqlClient.SqlBulkCopy> třída pro psaní k několika tabulkám.</span><span class="sxs-lookup"><span data-stu-id="04b02-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="04b02-110">Pro tyto ukázky **BulkCopyDemoOrderHeader** a **BulkCopyDemoOrderDetail** tabulky se používají jako cílové tabulky.</span><span class="sxs-lookup"><span data-stu-id="04b02-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="04b02-111">Tyto tabulky jsou založené na **Sales.SalesOrderHeader** a **Sales.SalesOrderDetail** tabulky v **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="04b02-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04b02-112">**SqlBulkCopy** ukázky kódu jsou k dispozici k předvedení syntaxe pro používání **SqlBulkCopy** pouze.</span><span class="sxs-lookup"><span data-stu-id="04b02-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="04b02-113">Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je snadnější a rychlejší pomocí jazyka Transact-SQL `INSERT … SELECT` příkaz Kopírovat data.</span><span class="sxs-lookup"><span data-stu-id="04b02-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="04b02-114">Nastavení tabulky</span><span class="sxs-lookup"><span data-stu-id="04b02-114">Table Setup</span></span>  
 <span data-ttu-id="04b02-115">Pokud chcete vytvořit tabulky nezbytné pro správné fungování ukázky kódu, musíte spustit následující příkazy jazyka Transact-SQL v databázi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04b02-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="04b02-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="04b02-116">See Also</span></span>  
 [<span data-ttu-id="04b02-117">Operace hromadného kopírování na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="04b02-117">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [<span data-ttu-id="04b02-118">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="04b02-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
