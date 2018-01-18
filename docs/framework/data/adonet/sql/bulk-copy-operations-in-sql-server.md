---
title: "Operace hromadného kopírování v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6efca83c6d3157e7fc4ff0e49ad32cab7cee9251
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="2cbd7-102">Operace hromadného kopírování v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="2cbd7-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="2cbd7-103">Microsoft SQL Server obsahuje oblíbených nástroj příkazového řádku s názvem **bcp** pro rychle hromadné kopírování velkých souborů do tabulky a zobrazení databáze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2cbd7-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="2cbd7-104"><xref:System.Data.SqlClient.SqlBulkCopy> Třída umožňuje zapisovat řešení spravovaného kódu, které poskytují podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="2cbd7-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="2cbd7-105">Existují další způsoby, jak načíst data do tabulky SQL Server (například příkazech INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> nabízí výhodu významně zvýšit výkon nad nimi.</span><span class="sxs-lookup"><span data-stu-id="2cbd7-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="2cbd7-106"><xref:System.Data.SqlClient.SqlBulkCopy> Třída slouží k zápisu dat pouze na tabulky serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2cbd7-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="2cbd7-107">Ale zdroj dat není omezený na SQL Server; lze použít libovolný zdroj dat, dokud k můžete načíst data <xref:System.Data.DataTable> instance nebo pro čtení s <xref:System.Data.IDataReader> instance.</span><span class="sxs-lookup"><span data-stu-id="2cbd7-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="2cbd7-108">Pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídu, můžete provést:</span><span class="sxs-lookup"><span data-stu-id="2cbd7-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
-   <span data-ttu-id="2cbd7-109">Jeden hromadné operace kopírování</span><span class="sxs-lookup"><span data-stu-id="2cbd7-109">A single bulk copy operation</span></span>  
  
-   <span data-ttu-id="2cbd7-110">Více operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="2cbd7-110">Multiple bulk copy operations</span></span>  
  
-   <span data-ttu-id="2cbd7-111">Operace hromadného kopírování v rámci transakce.</span><span class="sxs-lookup"><span data-stu-id="2cbd7-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cbd7-112">Při použití rozhraní .NET Framework verze 1.1 nebo starší (který nepodporuje <xref:System.Data.SqlClient.SqlBulkCopy> třída), můžete spustit SQL Server Transact-SQL **BULK INSERT** příkaz pomocí <xref:System.Data.SqlClient.SqlCommand> objekt.</span><span class="sxs-lookup"><span data-stu-id="2cbd7-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2cbd7-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2cbd7-113">In This Section</span></span>  
 [<span data-ttu-id="2cbd7-114">Příklad nastavení hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="2cbd7-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="2cbd7-115">Popisuje tabulky použité v ukázkách hromadné kopírování a poskytuje skripty SQL pro vytvoření tabulky v databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2cbd7-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="2cbd7-116">Jednorázové operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="2cbd7-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="2cbd7-117">Popisuje, jak provést jedné hromadné kopírování dat do instance systému SQL Server pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy a jak provádět hromadné kopírování pomocí příkazů Transact-SQL a <xref:System.Data.SqlClient.SqlCommand> třídy.</span><span class="sxs-lookup"><span data-stu-id="2cbd7-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="2cbd7-118">Vícečetné operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="2cbd7-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="2cbd7-119">Popisuje, jak provést několik operace hromadného kopírování dat do instance systému SQL Server pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy.</span><span class="sxs-lookup"><span data-stu-id="2cbd7-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="2cbd7-120">Operace transakcí a hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="2cbd7-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="2cbd7-121">Popisuje, jak provádět operace hromadného kopírování v rámci transakce, včetně postup potvrzení nebo vrácení transakce.</span><span class="sxs-lookup"><span data-stu-id="2cbd7-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cbd7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="2cbd7-122">See Also</span></span>  
 [<span data-ttu-id="2cbd7-123">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2cbd7-123">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="2cbd7-124">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="2cbd7-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
