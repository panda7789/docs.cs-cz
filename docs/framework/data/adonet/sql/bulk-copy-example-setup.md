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
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="3821a-102">Příklad nastavení hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="3821a-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="3821a-103">Třídu <xref:System.Data.SqlClient.SqlBulkCopy> lze použít k zápisu dat pouze do tabulek SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3821a-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="3821a-104">Ukázky kódu uvedené v tomto tématu používají ukázkovou databázi SQL Server **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="3821a-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="3821a-105">Aby nedošlo ke změně kódů stávajících tabulek, zapište data do tabulek, které je třeba vytvořit jako první.</span><span class="sxs-lookup"><span data-stu-id="3821a-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="3821a-106">Tabulky **BulkCopyDemoMatchingColumns** a **BulkCopyDemoDifferentColumns** jsou založené na tabulce **AdventureWorks** **produkce. Products** .</span><span class="sxs-lookup"><span data-stu-id="3821a-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="3821a-107">V ukázkách kódu, které používají tyto tabulky, jsou data přidána z tabulky **produkčních produktů** do jedné z těchto ukázkových tabulek.</span><span class="sxs-lookup"><span data-stu-id="3821a-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="3821a-108">Tabulka **BulkCopyDemoDifferentColumns** se používá, když Ukázka ukazuje, jak namapovat sloupce ze zdrojových dat do cílové tabulky. **BulkCopyDemoMatchingColumns** se používá pro většinu ostatních vzorků.</span><span class="sxs-lookup"><span data-stu-id="3821a-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="3821a-109">Několik ukázek kódu ukazuje, jak použít jednu <xref:System.Data.SqlClient.SqlBulkCopy> třídu k zápisu do více tabulek.</span><span class="sxs-lookup"><span data-stu-id="3821a-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="3821a-110">Pro tyto ukázky se jako cílové tabulky používají tabulky **BulkCopyDemoOrderHeader** a **BulkCopyDemoOrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="3821a-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="3821a-111">Tyto tabulky jsou založené na tabulkách **Sales. SalesOrderHeader** a **Sales. SalesOrderDetail** v **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="3821a-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3821a-112">Ukázky kódu **SqlBulkCopy** jsou k dispozici k předvedení syntaxe pouze použití **SqlBulkCopy** .</span><span class="sxs-lookup"><span data-stu-id="3821a-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="3821a-113">Pokud se zdrojové a cílové tabulky nacházejí ve stejné instanci SQL Server, je snazší a rychlejší použít příkaz Transact-SQL `INSERT … SELECT` ke zkopírování dat.</span><span class="sxs-lookup"><span data-stu-id="3821a-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="3821a-114">Nastavení tabulky</span><span class="sxs-lookup"><span data-stu-id="3821a-114">Table Setup</span></span>  
 <span data-ttu-id="3821a-115">Chcete-li vytvořit tabulky potřebné pro správné spuštění ukázek kódu, je nutné spustit následující příkazy jazyka Transact-SQL v databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3821a-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3821a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3821a-116">See also</span></span>

- [<span data-ttu-id="3821a-117">Operace hromadného kopírování na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="3821a-117">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="3821a-118">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3821a-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
