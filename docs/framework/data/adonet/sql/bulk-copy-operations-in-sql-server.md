---
title: Operace hromadného kopírování na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: efa13eb1633fce3b59040ef8da79dba0f6ea81d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918067"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="43435-102">Operace hromadného kopírování na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="43435-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="43435-103">Microsoft SQL Server obsahuje oblíbený nástroj příkazového řádku s názvem **BCP** pro rychlé hromadné kopírování velkých souborů do tabulek nebo zobrazení v databázích SQL Server.</span><span class="sxs-lookup"><span data-stu-id="43435-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="43435-104"><xref:System.Data.SqlClient.SqlBulkCopy> Třída umožňuje psát řešení spravovaného kódu, která poskytují podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="43435-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="43435-105">Existují i další způsoby, jak načíst data do SQL Server tabulky (například příkazy INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> v nich nabízí významné výhody výkonu.</span><span class="sxs-lookup"><span data-stu-id="43435-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="43435-106"><xref:System.Data.SqlClient.SqlBulkCopy> Třídu lze použít k zápisu dat pouze do SQL Server tabulek.</span><span class="sxs-lookup"><span data-stu-id="43435-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="43435-107">Ale zdroj dat není omezen na SQL Server; můžete použít jakýkoliv zdroj dat, pokud data lze načíst do <xref:System.Data.DataTable> instance nebo číst <xref:System.Data.IDataReader> s instancí.</span><span class="sxs-lookup"><span data-stu-id="43435-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="43435-108"><xref:System.Data.SqlClient.SqlBulkCopy> Pomocí třídy můžete provádět následující akce:</span><span class="sxs-lookup"><span data-stu-id="43435-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="43435-109">Jedna operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="43435-109">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="43435-110">Více operací hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="43435-110">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="43435-111">Operace hromadného kopírování v rámci transakce</span><span class="sxs-lookup"><span data-stu-id="43435-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43435-112">Při použití .NET Framework verze 1,1 nebo starší (která <xref:System.Data.SqlClient.SqlBulkCopy> třídu nepodporuje) můžete spustit příkaz SQL Server Transact-SQL **Bulk INSERT** pomocí <xref:System.Data.SqlClient.SqlCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="43435-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43435-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="43435-113">In This Section</span></span>  
 [<span data-ttu-id="43435-114">Příklad nastavení hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="43435-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="43435-115">Popisuje tabulky používané v ukázkách hromadného kopírování a poskytuje skripty SQL pro vytváření tabulek v databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="43435-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="43435-116">Jednorázové operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="43435-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="43435-117">Popisuje, jak provést jednu hromadnou kopii dat do instance SQL Server pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy a jak provést operaci hromadného kopírování s použitím příkazů jazyka Transact-SQL <xref:System.Data.SqlClient.SqlCommand> a třídy.</span><span class="sxs-lookup"><span data-stu-id="43435-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="43435-118">Vícečetné operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="43435-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="43435-119">Popisuje, jak provést více operací hromadného kopírování dat do instance SQL Server pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy.</span><span class="sxs-lookup"><span data-stu-id="43435-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="43435-120">Operace transakcí a hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="43435-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="43435-121">Popisuje, jak provést operaci hromadného kopírování v rámci transakce, včetně toho, jak transakci potvrdit nebo vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="43435-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43435-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43435-122">See also</span></span>

- [<span data-ttu-id="43435-123">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43435-123">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="43435-124">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="43435-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
