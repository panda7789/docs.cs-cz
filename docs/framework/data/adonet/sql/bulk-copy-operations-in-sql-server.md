---
title: Operace hromadného kopírování na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: e538e48400d955a0013a12dbf2d10f1f96c3ddfe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649551"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="49f4d-102">Operace hromadného kopírování na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="49f4d-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="49f4d-103">Microsoft SQL Server obsahuje oblíbené nástroje příkazového řádku s názvem **bcp** pro rychle hromadné kopírování velkých souborů do tabulky a zobrazení v databázích systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="49f4d-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="49f4d-104"><xref:System.Data.SqlClient.SqlBulkCopy> Třída umožňuje zapisovat spravovaného kódu řešení, která poskytuje podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="49f4d-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="49f4d-105">Existují jiné způsoby, jak načíst data do tabulky SQL serveru (například příkazy INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> nabízí výhody výkonu nad nimi.</span><span class="sxs-lookup"><span data-stu-id="49f4d-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="49f4d-106"><xref:System.Data.SqlClient.SqlBulkCopy> Třídy lze použít k zápisu dat jenom do tabulek systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="49f4d-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="49f4d-107">Ale není omezena pouze na serveru SQL Server; zdroj dat můžete použít libovolný zdroj dat, za předpokladu, data je možné načíst do <xref:System.Data.DataTable> instance nebo si přečtěte s <xref:System.Data.IDataReader> instance.</span><span class="sxs-lookup"><span data-stu-id="49f4d-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="49f4d-108">Použití <xref:System.Data.SqlClient.SqlBulkCopy> třídy, můžete provést:</span><span class="sxs-lookup"><span data-stu-id="49f4d-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="49f4d-109">Jeden hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="49f4d-109">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="49f4d-110">Vícečetné operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="49f4d-110">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="49f4d-111">Operaci hromadného kopírování v rámci transakce</span><span class="sxs-lookup"><span data-stu-id="49f4d-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49f4d-112">Při použití rozhraní .NET Framework verze 1.1 nebo starší (což není podporováno <xref:System.Data.SqlClient.SqlBulkCopy> třídy), můžete spustit SQL Server Transact-SQL **BULK INSERT** pomocí příkazu <xref:System.Data.SqlClient.SqlCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="49f4d-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49f4d-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="49f4d-113">In This Section</span></span>  
 [<span data-ttu-id="49f4d-114">Příklad nastavení hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="49f4d-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="49f4d-115">Popisuje tabulky používané v příkladech hromadného kopírování a obsahuje skripty SQL pro vytváření tabulek v databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="49f4d-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="49f4d-116">Jednorázové operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="49f4d-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="49f4d-117">Popisuje, jak provést jedné hromadné kopírování dat do instance SQL serveru pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy a jak provádět operaci hromadného kopírování pomocí příkazů jazyka Transact-SQL a <xref:System.Data.SqlClient.SqlCommand> třídy.</span><span class="sxs-lookup"><span data-stu-id="49f4d-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="49f4d-118">Vícečetné operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="49f4d-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="49f4d-119">Popisuje, jak provést vícečetné operace hromadného kopírování dat do instance SQL serveru pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy.</span><span class="sxs-lookup"><span data-stu-id="49f4d-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="49f4d-120">Operace transakcí a hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="49f4d-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="49f4d-121">Popisuje, jak provést operaci hromadného kopírování v rámci transakce, včetně jak potvrzení nebo vrácení transakce.</span><span class="sxs-lookup"><span data-stu-id="49f4d-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49f4d-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49f4d-122">See also</span></span>

- [<span data-ttu-id="49f4d-123">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="49f4d-123">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="49f4d-124">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="49f4d-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
