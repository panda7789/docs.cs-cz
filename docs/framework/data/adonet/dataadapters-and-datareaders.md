---
title: Adaptéry a čtečky dat
description: Přečtěte si o DataReader ADO.NET, který načte data z databáze a generuje data ze zdroje dat a naplní datovou sadu.
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 17463d65266baa53521bed9603c8abd96923277b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286970"
---
# <a name="dataadapters-and-datareaders"></a><span data-ttu-id="aa2c8-103">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="aa2c8-103">DataAdapters and DataReaders</span></span>
<span data-ttu-id="aa2c8-104">Pomocí objektu **DataReader** ADO.NET můžete načíst proud dat pouze pro čtení z databáze.</span><span class="sxs-lookup"><span data-stu-id="aa2c8-104">You can use the ADO.NET **DataReader** to retrieve a read-only, forward-only stream of data from a database.</span></span> <span data-ttu-id="aa2c8-105">Výsledky jsou vraceny při spuštění dotazu a jsou uloženy v síťové vyrovnávací paměti klienta, dokud je nepožadujete pomocí metody **Read** objektu **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="aa2c8-105">Results are returned as the query executes, and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader**.</span></span> <span data-ttu-id="aa2c8-106">Použití objektu **DataReader** může zvýšit výkon aplikace načtením dat, jakmile jsou k dispozici, a (ve výchozím nastavení) ukládat pouze jeden řádek v čase paměti a snížit zatížení systému.</span><span class="sxs-lookup"><span data-stu-id="aa2c8-106">Using the **DataReader** can increase application performance both by retrieving data as soon as it is available, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="aa2c8-107"><xref:System.Data.Common.DataAdapter>Slouží k načtení dat ze zdroje dat a naplnění tabulek v rámci <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="aa2c8-107">A <xref:System.Data.Common.DataAdapter> is used to retrieve data from a data source and populate tables within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="aa2c8-108">`DataAdapter`Také řeší změny provedené v `DataSet` zpátky na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="aa2c8-108">The `DataAdapter` also resolves changes made to the `DataSet` back to the data source.</span></span> <span data-ttu-id="aa2c8-109">`DataAdapter`Používá `Connection` objekt poskytovatele .NET Framework dat pro připojení ke zdroji dat a používá `Command` objekty k načtení dat z a řešení změn ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="aa2c8-109">The `DataAdapter` uses the `Connection` object of the .NET Framework data provider to connect to a data source, and it uses `Command` objects to retrieve data from and resolve changes to the data source.</span></span>  
  
 <span data-ttu-id="aa2c8-110">Každý .NET Framework poskytovatel dat, který je součástí .NET Framework, má <xref:System.Data.Common.DbDataReader> a a <xref:System.Data.Common.DbDataAdapter> objekt: .NET Framework Zprostředkovatel dat pro OLE DB obsahuje <xref:System.Data.OleDb.OleDbDataReader> objekt a <xref:System.Data.OleDb.OleDbDataAdapter> , .NET Framework Zprostředkovatel dat pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlDataReader> objekt a <xref:System.Data.SqlClient.SqlDataAdapter> , .NET Framework Zprostředkovatel dat pro rozhraní ODBC <xref:System.Data.Odbc.OdbcDataReader> <xref:System.Data.Odbc.OdbcDataAdapter> <xref:System.Data.OracleClient.OracleDataReader> <xref:System.Data.OracleClient.OracleDataAdapter> obsahuje objekt a a .NET Framework Zprostředkovatel dat pro Oracle obsahuje objekt a.</span><span class="sxs-lookup"><span data-stu-id="aa2c8-110">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbDataReader> and a <xref:System.Data.Common.DbDataAdapter> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbDataReader> and an <xref:System.Data.OleDb.OleDbDataAdapter> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlDataReader> and a <xref:System.Data.SqlClient.SqlDataAdapter> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcDataReader> and an <xref:System.Data.Odbc.OdbcDataAdapter> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleDataReader> and an <xref:System.Data.OracleClient.OracleDataAdapter> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa2c8-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="aa2c8-111">In This Section</span></span>  
 [<span data-ttu-id="aa2c8-112">Načítání dat pomocí čtečky dat</span><span class="sxs-lookup"><span data-stu-id="aa2c8-112">Retrieving Data Using a DataReader</span></span>](retrieving-data-using-a-datareader.md)  
 <span data-ttu-id="aa2c8-113">Popisuje objekt **DataReader** ADO.NET a jeho použití k vrácení datového proudu výsledků ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="aa2c8-113">Describes the ADO.NET **DataReader** object and how to use it to return a stream of results from a data source.</span></span>  
  
 [<span data-ttu-id="aa2c8-114">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="aa2c8-114">Populating a DataSet from a DataAdapter</span></span>](populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="aa2c8-115">Popisuje, jak vyplnit `DataSet` tabulky, sloupce a řádky pomocí tabulek, sloupců a řádků `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="aa2c8-115">Describes how to fill a `DataSet` with tables, columns, and rows by using a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="aa2c8-116">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="aa2c8-116">DataAdapter Parameters</span></span>](dataadapter-parameters.md)  
 <span data-ttu-id="aa2c8-117">Popisuje, jak použít parametry s vlastnostmi příkazu, `DataAdapter` včetně způsobu mapování obsahu sloupce v nástroji `DataSet` na parametr příkazu.</span><span class="sxs-lookup"><span data-stu-id="aa2c8-117">Describes how to use parameters with the command properties of a `DataAdapter` including how to map the contents of a column in a `DataSet` to a command parameter.</span></span>  
  
 [<span data-ttu-id="aa2c8-118">Přidání existujících omezení do datové sady</span><span class="sxs-lookup"><span data-stu-id="aa2c8-118">Adding Existing Constraints to a DataSet</span></span>](adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="aa2c8-119">Popisuje, jak přidat existující omezení do `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="aa2c8-119">Describes how to add existing constraints to a `DataSet`.</span></span>  
  
 [<span data-ttu-id="aa2c8-120">Mapování adaptéru dat, datové tabulky a datového sloupce</span><span class="sxs-lookup"><span data-stu-id="aa2c8-120">DataAdapter DataTable and DataColumn Mappings</span></span>](dataadapter-datatable-and-datacolumn-mappings.md)  
 <span data-ttu-id="aa2c8-121">Popisuje, jak nastavit `DataTableMappings` a `ColumnMappings` pro `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="aa2c8-121">Describes how to set up `DataTableMappings` and `ColumnMappings` for a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="aa2c8-122">Stránkování prostřednictvím výsledku dotazu</span><span class="sxs-lookup"><span data-stu-id="aa2c8-122">Paging Through a Query Result</span></span>](paging-through-a-query-result.md)  
 <span data-ttu-id="aa2c8-123">Poskytuje příklad zobrazení výsledků dotazu jako stránek dat.</span><span class="sxs-lookup"><span data-stu-id="aa2c8-123">Provides an example of viewing the results of a query as pages of data.</span></span>  
  
 [<span data-ttu-id="aa2c8-124">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="aa2c8-124">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="aa2c8-125">Popisuje, jak použít `DataAdapter` k vyřešení změn v `DataSet` databázi.</span><span class="sxs-lookup"><span data-stu-id="aa2c8-125">Describes how to use a `DataAdapter` to resolve changes in a `DataSet` back to the database.</span></span>  
  
 [<span data-ttu-id="aa2c8-126">Zpracování událostí adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="aa2c8-126">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)  
 <span data-ttu-id="aa2c8-127">Popisuje `DataAdapter` události a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="aa2c8-127">Describes `DataAdapter` events and how to use them.</span></span>  
  
 [<span data-ttu-id="aa2c8-128">Provádění dávkových operací pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="aa2c8-128">Performing Batch Operations Using DataAdapters</span></span>](performing-batch-operations-using-dataadapters.md)  
 <span data-ttu-id="aa2c8-129">Popisuje zvýšení výkonu aplikace tím, že omezuje počet přenosů, které se SQL Server při aplikování aktualizací z `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="aa2c8-129">Describes enhancing application performance by reducing the number of round trips to SQL Server when applying updates from the `DataSet`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa2c8-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa2c8-130">See also</span></span>

- [<span data-ttu-id="aa2c8-131">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="aa2c8-131">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="aa2c8-132">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="aa2c8-132">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="aa2c8-133">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="aa2c8-133">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="aa2c8-134">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="aa2c8-134">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="aa2c8-135">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="aa2c8-135">ADO.NET Overview</span></span>](ado-net-overview.md)
