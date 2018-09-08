---
title: Příklad nastavení hromadného kopírování
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 71daf489fdf5e7e12594e798bc3ac01b1c76b027
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44212552"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="83e14-102">Příklad nastavení hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="83e14-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="83e14-103"><xref:System.Data.SqlClient.SqlBulkCopy> Třídy lze použít k zápisu dat jenom do tabulek systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="83e14-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="83e14-104">Ukázky kódu v tomto tématu použijte ukázkovou databázi systému SQL Server, **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="83e14-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="83e14-105">Ukázky kódu pro neupravujte existující tabulky zapisovat data do tabulek, které je nutné nejprve vytvořit.</span><span class="sxs-lookup"><span data-stu-id="83e14-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="83e14-106">**BulkCopyDemoMatchingColumns** a **BulkCopyDemoDifferentColumns** tabulkách jsou založené na **AdventureWorks** **Production.Products**  tabulky.</span><span class="sxs-lookup"><span data-stu-id="83e14-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="83e14-107">Ukázky kódu, které používají tyto tabulky, data je přidána z **Production.Products** tabulku k jedné z těchto ukázkových tabulek.</span><span class="sxs-lookup"><span data-stu-id="83e14-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="83e14-108">**BulkCopyDemoDifferentColumns** tabulky se používá při vzorek ukazuje, jak namapovat sloupce ze zdroje dat do cílové tabulky; **BulkCopyDemoMatchingColumns** se používá pro většinu ostatních vzorků.</span><span class="sxs-lookup"><span data-stu-id="83e14-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="83e14-109">Některé ukázky kódu demonstrují, jakým způsobem chcete použít jeden <xref:System.Data.SqlClient.SqlBulkCopy> třídu pro zápis k několika tabulkám.</span><span class="sxs-lookup"><span data-stu-id="83e14-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="83e14-110">Pro tyto ukázky **BulkCopyDemoOrderHeader** a **BulkCopyDemoOrderDetail** tabulky se používají jako cílových tabulek.</span><span class="sxs-lookup"><span data-stu-id="83e14-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="83e14-111">Tyto tabulky jsou založeny na **Sales.SalesOrderHeader** a **Sales.SalesOrderDetail** tabulky v **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="83e14-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83e14-112">**SqlBulkCopy** jsou k dispozici ukázky kódu ukazují syntaxi pomocí **SqlBulkCopy** pouze.</span><span class="sxs-lookup"><span data-stu-id="83e14-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="83e14-113">Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je jednodušší a rychlejší použití příkazů jazyka Transact-SQL `INSERT … SELECT` příkaz Kopírovat data.</span><span class="sxs-lookup"><span data-stu-id="83e14-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="83e14-114">Nastavení tabulky</span><span class="sxs-lookup"><span data-stu-id="83e14-114">Table Setup</span></span>  
 <span data-ttu-id="83e14-115">Aby se vytvořily tabulky nezbytné pro ukázky kódu správně spustit, musíte spustit následující příkazy jazyka Transact-SQL v databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="83e14-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83e14-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="83e14-116">See Also</span></span>  
 [<span data-ttu-id="83e14-117">Operace hromadného kopírování na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="83e14-117">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [<span data-ttu-id="83e14-118">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="83e14-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
