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
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="6d238-102">Příklad nastavení hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="6d238-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="6d238-103">Třídu <xref:System.Data.SqlClient.SqlBulkCopy> lze použít k zápisu dat pouze do tabulek serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6d238-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="6d238-104">Ukázky kódu zobrazené v tomto tématu používají ukázkovou databázi serveru SQL Server **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="6d238-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="6d238-105">Chcete-li se vyhnout změně existující tabulky ukázky kódu zápis dat do tabulek, které je nutné vytvořit jako první.</span><span class="sxs-lookup"><span data-stu-id="6d238-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="6d238-106">**BulkCopyDemoMatchingColumns** a **BulkCopyDemoDifferentColumns** tabulky jsou založeny na **AdventureWorks** **Production.Products** tabulky.</span><span class="sxs-lookup"><span data-stu-id="6d238-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="6d238-107">Ve vzorcích kódu, které používají tyto tabulky, jsou data přidána z tabulky **Production.Products** do jedné z těchto ukázkových tabulek.</span><span class="sxs-lookup"><span data-stu-id="6d238-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="6d238-108">**BulkCopyDemoDifferentColumns** tabulka se používá, když ukázka ukazuje, jak mapovat sloupce ze zdrojových dat do cílové tabulky; **BulkCopyDemoMatchingColumns** se používá pro většinu ostatních vzorků.</span><span class="sxs-lookup"><span data-stu-id="6d238-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="6d238-109">Několik ukázek kódu ukazuje, jak <xref:System.Data.SqlClient.SqlBulkCopy> použít jednu třídu k zápisu do více tabulek.</span><span class="sxs-lookup"><span data-stu-id="6d238-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="6d238-110">Pro tyto ukázky **bulkcopydemoorderheader** a **bulkcopydemoorderdetail** tabulky se používají jako cílové tabulky.</span><span class="sxs-lookup"><span data-stu-id="6d238-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="6d238-111">Tyto tabulky jsou založeny na tabulkách **Sales.SalesOrderHeader** a **Sales.SalesOrderDetail** v **adventureworks**.</span><span class="sxs-lookup"><span data-stu-id="6d238-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d238-112">**SqlBulkCopy** kód ukázky jsou k dispozici k předvedení syntaxe pro použití **pouze SqlBulkCopy.**</span><span class="sxs-lookup"><span data-stu-id="6d238-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="6d238-113">Pokud jsou zdrojové a cílové tabulky umístěny ve stejné instanci serveru SQL `INSERT … SELECT` Server, je jednodušší a rychlejší zkopírovat data příkazu Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="6d238-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="6d238-114">Nastavení tabulky</span><span class="sxs-lookup"><span data-stu-id="6d238-114">Table Setup</span></span>  
 <span data-ttu-id="6d238-115">Chcete-li vytvořit tabulky nezbytné pro správné spuštění ukázek kódu, je nutné spustit následující příkazy Transact-SQL v databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6d238-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d238-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d238-116">See also</span></span>

- [<span data-ttu-id="6d238-117">Operace hromadného kopírování na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="6d238-117">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="6d238-118">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6d238-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
