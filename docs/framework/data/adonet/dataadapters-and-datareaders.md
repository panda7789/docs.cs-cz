---
title: DataAdapters a DataReaders
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e7a0af0b5fabdfacfcc825258242868b0fbb513
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="dataadapters-and-datareaders"></a><span data-ttu-id="47da0-102">DataAdapters a DataReaders</span><span class="sxs-lookup"><span data-stu-id="47da0-102">DataAdapters and DataReaders</span></span>
<span data-ttu-id="47da0-103">Můžete použít technologie ADO.NET **DataReader** načíst jen pro čtení, dopředné datový proud z databáze.</span><span class="sxs-lookup"><span data-stu-id="47da0-103">You can use the ADO.NET **DataReader** to retrieve a read-only, forward-only stream of data from a database.</span></span> <span data-ttu-id="47da0-104">Výsledky se vrátí jako dotazu se provede a jsou uložené ve vyrovnávací paměti sítě na straně klienta, dokud na žádost uživatele pomocí **čtení** metodu **DataReader –**.</span><span class="sxs-lookup"><span data-stu-id="47da0-104">Results are returned as the query executes, and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader**.</span></span> <span data-ttu-id="47da0-105">Pomocí **DataReader** může zvýšit výkon aplikace načtením dat, jakmile je k dispozici i (ve výchozím nastavení) ukládání pouze jeden řádek v daný okamžik v paměti a snižuje zátěž systému.</span><span class="sxs-lookup"><span data-stu-id="47da0-105">Using the **DataReader** can increase application performance both by retrieving data as soon as it is available, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="47da0-106">A <xref:System.Data.Common.DataAdapter> slouží k načtení dat ze zdroje dat a naplnění tabulky v rámci <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="47da0-106">A <xref:System.Data.Common.DataAdapter> is used to retrieve data from a data source and populate tables within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="47da0-107">`DataAdapter` Rovněž řeší změny provedené `DataSet` zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="47da0-107">The `DataAdapter` also resolves changes made to the `DataSet` back to the data source.</span></span> <span data-ttu-id="47da0-108">`DataAdapter` Používá `Connection` objekt zprostředkovatel dat .NET Framework pro připojení ke zdroji dat a používá `Command` objekty, které chcete načíst data ze a odkazující na zdroj dat změny.</span><span class="sxs-lookup"><span data-stu-id="47da0-108">The `DataAdapter` uses the `Connection` object of the .NET Framework data provider to connect to a data source, and it uses `Command` objects to retrieve data from and resolve changes to the data source.</span></span>  
  
 <span data-ttu-id="47da0-109">Má každý zprostředkovatel dat .NET Framework je součástí rozhraní .NET Framework <xref:System.Data.Common.DbDataReader> a <xref:System.Data.Common.DbDataAdapter> objektu: Zprostředkovatel dat .NET Framework pro OLE DB zahrnuje <xref:System.Data.OleDb.OleDbDataReader> a <xref:System.Data.OleDb.OleDbDataAdapter> objekt, zprostředkovatel dat .NET Framework pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlDataReader> a <xref:System.Data.SqlClient.SqlDataAdapter> objektu, zahrnuje zprostředkovatel dat .NET Framework pro ODBC <xref:System.Data.Odbc.OdbcDataReader> a <xref:System.Data.Odbc.OdbcDataAdapter> objekt a zprostředkovatel dat .NET Framework pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleDataReader> a <xref:System.Data.OracleClient.OracleDataAdapter> objektu.</span><span class="sxs-lookup"><span data-stu-id="47da0-109">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbDataReader> and a <xref:System.Data.Common.DbDataAdapter> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbDataReader> and an <xref:System.Data.OleDb.OleDbDataAdapter> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlDataReader> and a <xref:System.Data.SqlClient.SqlDataAdapter> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcDataReader> and an <xref:System.Data.Odbc.OdbcDataAdapter> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleDataReader> and an <xref:System.Data.OracleClient.OracleDataAdapter> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47da0-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="47da0-110">In This Section</span></span>  
 [<span data-ttu-id="47da0-111">Načítání dat pomocí DataReader –</span><span class="sxs-lookup"><span data-stu-id="47da0-111">Retrieving Data Using a DataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 <span data-ttu-id="47da0-112">Popisuje technologie ADO.NET **DataReader** objekt a způsobu jeho použití vrátit datový proud výsledků ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="47da0-112">Describes the ADO.NET **DataReader** object and how to use it to return a stream of results from a data source.</span></span>  
  
 [<span data-ttu-id="47da0-113">Naplnění datové sady z modul DataAdapter</span><span class="sxs-lookup"><span data-stu-id="47da0-113">Populating a DataSet from a DataAdapter</span></span>](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="47da0-114">Popisuje, jak k vyplnění `DataSet` tabulky, sloupce a řádky pomocí `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="47da0-114">Describes how to fill a `DataSet` with tables, columns, and rows by using a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="47da0-115">Parametry DataAdapter</span><span class="sxs-lookup"><span data-stu-id="47da0-115">DataAdapter Parameters</span></span>](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 <span data-ttu-id="47da0-116">Popisuje, jak používat parametry se příkaz Vlastnosti `DataAdapter` včetně postup mapování obsahu sloupce v `DataSet` pro parametr příkazu.</span><span class="sxs-lookup"><span data-stu-id="47da0-116">Describes how to use parameters with the command properties of a `DataAdapter` including how to map the contents of a column in a `DataSet` to a command parameter.</span></span>  
  
 [<span data-ttu-id="47da0-117">Přidání existující omezení datové sady</span><span class="sxs-lookup"><span data-stu-id="47da0-117">Adding Existing Constraints to a DataSet</span></span>](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="47da0-118">Popisuje, jak přidat do existující omezení `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="47da0-118">Describes how to add existing constraints to a `DataSet`.</span></span>  
  
 [<span data-ttu-id="47da0-119">DataAdapter DataTable a DataColumn mapování</span><span class="sxs-lookup"><span data-stu-id="47da0-119">DataAdapter DataTable and DataColumn Mappings</span></span>](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 <span data-ttu-id="47da0-120">Popisuje, jak nastavit `DataTableMappings` a `ColumnMappings` pro `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="47da0-120">Describes how to set up `DataTableMappings` and `ColumnMappings` for a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="47da0-121">Stránkování prostřednictvím výsledku dotazu</span><span class="sxs-lookup"><span data-stu-id="47da0-121">Paging Through a Query Result</span></span>](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 <span data-ttu-id="47da0-122">Poskytuje příklad zobrazení jako stránky s daty výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="47da0-122">Provides an example of viewing the results of a query as pages of data.</span></span>  
  
 [<span data-ttu-id="47da0-123">Aktualizace zdrojů dat s DataAdapters</span><span class="sxs-lookup"><span data-stu-id="47da0-123">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="47da0-124">Popisuje způsob použití `DataAdapter` změny v řešení `DataSet` zpět do databáze.</span><span class="sxs-lookup"><span data-stu-id="47da0-124">Describes how to use a `DataAdapter` to resolve changes in a `DataSet` back to the database.</span></span>  
  
 [<span data-ttu-id="47da0-125">Zpracování událostí DataAdapter</span><span class="sxs-lookup"><span data-stu-id="47da0-125">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 <span data-ttu-id="47da0-126">Popisuje `DataAdapter` událostí a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="47da0-126">Describes `DataAdapter` events and how to use them.</span></span>  
  
 [<span data-ttu-id="47da0-127">Provádění operací Batch pomocí DataAdapters</span><span class="sxs-lookup"><span data-stu-id="47da0-127">Performing Batch Operations Using DataAdapters</span></span>](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 <span data-ttu-id="47da0-128">Popisuje zlepšení výkonu aplikací, protože se sníží počet zpátečních cest k systému SQL Server při použití aktualizací z `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="47da0-128">Describes enhancing application performance by reducing the number of round trips to SQL Server when applying updates from the `DataSet`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47da0-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="47da0-129">See Also</span></span>  
 [<span data-ttu-id="47da0-130">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="47da0-130">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="47da0-131">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="47da0-131">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="47da0-132">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="47da0-132">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="47da0-133">Datové sady, DataTables a DataView</span><span class="sxs-lookup"><span data-stu-id="47da0-133">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="47da0-134">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="47da0-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
