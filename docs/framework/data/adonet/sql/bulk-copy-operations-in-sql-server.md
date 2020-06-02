---
title: Operace hromadného kopírování na SQL Serveru
description: Naučte se používat třídu SqlBulkCopy k psaní řešení spravovaného kódu, která hromadně kopírují velké soubory do tabulek nebo zobrazení v SQL Server databázích.
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 4f877836aa45efe162cce3c42cb5733f86deab2c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286517"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="433a6-103">Operace hromadného kopírování na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="433a6-103">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="433a6-104">Microsoft SQL Server obsahuje oblíbený nástroj příkazového řádku s názvem **BCP** pro rychlé hromadné kopírování velkých souborů do tabulek nebo zobrazení v databázích SQL Server.</span><span class="sxs-lookup"><span data-stu-id="433a6-104">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="433a6-105"><xref:System.Data.SqlClient.SqlBulkCopy>Třída umožňuje psát řešení spravovaného kódu, která poskytují podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="433a6-105">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="433a6-106">Existují i další způsoby, jak načíst data do SQL Server tabulky (například příkazy INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> v nich nabízí významné výhody výkonu.</span><span class="sxs-lookup"><span data-stu-id="433a6-106">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="433a6-107"><xref:System.Data.SqlClient.SqlBulkCopy>Třídu lze použít k zápisu dat pouze do SQL Server tabulek.</span><span class="sxs-lookup"><span data-stu-id="433a6-107">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="433a6-108">Ale zdroj dat není omezen na SQL Server; můžete použít jakýkoliv zdroj dat, pokud data lze načíst do <xref:System.Data.DataTable> instance nebo číst s <xref:System.Data.IDataReader> instancí.</span><span class="sxs-lookup"><span data-stu-id="433a6-108">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="433a6-109">Pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy můžete provádět následující akce:</span><span class="sxs-lookup"><span data-stu-id="433a6-109">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="433a6-110">Jedna operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="433a6-110">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="433a6-111">Více operací hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="433a6-111">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="433a6-112">Operace hromadného kopírování v rámci transakce</span><span class="sxs-lookup"><span data-stu-id="433a6-112">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
> <span data-ttu-id="433a6-113">Při použití .NET Framework verze 1,1 nebo starší (která <xref:System.Data.SqlClient.SqlBulkCopy> třídu nepodporuje) můžete spustit příkaz SQL Server Transact-SQL **Bulk INSERT** pomocí <xref:System.Data.SqlClient.SqlCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="433a6-113">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="433a6-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="433a6-114">In This Section</span></span>  
 [<span data-ttu-id="433a6-115">Příklad nastavení hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="433a6-115">Bulk Copy Example Setup</span></span>](bulk-copy-example-setup.md)  
 <span data-ttu-id="433a6-116">Popisuje tabulky používané v ukázkách hromadného kopírování a poskytuje skripty SQL pro vytváření tabulek v databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="433a6-116">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="433a6-117">Jednorázové operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="433a6-117">Single Bulk Copy Operations</span></span>](single-bulk-copy-operations.md)  
 <span data-ttu-id="433a6-118">Popisuje, jak provést jednu hromadnou kopii dat do instance SQL Server pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy a jak provést operaci hromadného kopírování s použitím příkazů jazyka Transact-SQL a <xref:System.Data.SqlClient.SqlCommand> třídy.</span><span class="sxs-lookup"><span data-stu-id="433a6-118">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="433a6-119">Vícečetné operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="433a6-119">Multiple Bulk Copy Operations</span></span>](multiple-bulk-copy-operations.md)  
 <span data-ttu-id="433a6-120">Popisuje, jak provést více operací hromadného kopírování dat do instance SQL Server pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy.</span><span class="sxs-lookup"><span data-stu-id="433a6-120">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="433a6-121">Operace transakcí a hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="433a6-121">Transaction and Bulk Copy Operations</span></span>](transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="433a6-122">Popisuje, jak provést operaci hromadného kopírování v rámci transakce, včetně toho, jak transakci potvrdit nebo vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="433a6-122">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="433a6-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="433a6-123">See also</span></span>

- [<span data-ttu-id="433a6-124">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="433a6-124">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="433a6-125">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="433a6-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
