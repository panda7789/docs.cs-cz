---
title: Adaptéry a čtečky dat
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 20c6d514e70d2e4db451e0fff02e72688bf7d0ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786647"
---
# <a name="dataadapters-and-datareaders"></a><span data-ttu-id="b1ea7-102">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="b1ea7-102">DataAdapters and DataReaders</span></span>
<span data-ttu-id="b1ea7-103">Pomocí objektu **DataReader** ADO.NET můžete načíst proud dat pouze pro čtení z databáze.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-103">You can use the ADO.NET **DataReader** to retrieve a read-only, forward-only stream of data from a database.</span></span> <span data-ttu-id="b1ea7-104">Výsledky jsou vraceny při spuštění dotazu a jsou uloženy v síťové vyrovnávací paměti klienta, dokud je nepožadujete pomocí metody **Read** objektu **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-104">Results are returned as the query executes, and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader**.</span></span> <span data-ttu-id="b1ea7-105">Použití objektu **DataReader** může zvýšit výkon aplikace načtením dat, jakmile jsou k dispozici, a (ve výchozím nastavení) ukládat pouze jeden řádek v čase paměti a snížit zatížení systému.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-105">Using the **DataReader** can increase application performance both by retrieving data as soon as it is available, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="b1ea7-106">Slouží k načtení dat ze zdroje dat a naplnění tabulek <xref:System.Data.DataSet>v rámci. <xref:System.Data.Common.DataAdapter></span><span class="sxs-lookup"><span data-stu-id="b1ea7-106">A <xref:System.Data.Common.DataAdapter> is used to retrieve data from a data source and populate tables within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b1ea7-107">Také řeší změny provedené v `DataSet` zpátky na zdroj dat. `DataAdapter`</span><span class="sxs-lookup"><span data-stu-id="b1ea7-107">The `DataAdapter` also resolves changes made to the `DataSet` back to the data source.</span></span> <span data-ttu-id="b1ea7-108">Používá objekt poskytovatele .NET Framework dat pro připojení ke zdroji dat a používá `Command` objekty k načtení dat z a řešení změn ve zdroji dat. `Connection` `DataAdapter`</span><span class="sxs-lookup"><span data-stu-id="b1ea7-108">The `DataAdapter` uses the `Connection` object of the .NET Framework data provider to connect to a data source, and it uses `Command` objects to retrieve data from and resolve changes to the data source.</span></span>  
  
 <span data-ttu-id="b1ea7-109">Každý .NET Framework poskytovatel dat, který je součástí .NET Framework, <xref:System.Data.Common.DbDataReader> má <xref:System.Data.Common.DbDataAdapter> a a objekt: .NET Framework <xref:System.Data.OleDb.OleDbDataReader> zprostředkovatel dat pro <xref:System.Data.OleDb.OleDbDataAdapter> OLE DB obsahuje objekt a, .NET Framework Zprostředkovatel dat pro SQL. Server obsahuje <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataAdapter> objekt a a .NET Framework <xref:System.Data.Odbc.OdbcDataReader> zprostředkovatel dat pro <xref:System.Data.Odbc.OdbcDataAdapter> rozhraní ODBC obsahuje objekt a a .NET Framework Zprostředkovatel dat pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleDataReader> a. <xref:System.Data.OracleClient.OracleDataAdapter> objekt.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-109">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbDataReader> and a <xref:System.Data.Common.DbDataAdapter> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbDataReader> and an <xref:System.Data.OleDb.OleDbDataAdapter> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlDataReader> and a <xref:System.Data.SqlClient.SqlDataAdapter> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcDataReader> and an <xref:System.Data.Odbc.OdbcDataAdapter> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleDataReader> and an <xref:System.Data.OracleClient.OracleDataAdapter> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1ea7-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b1ea7-110">In This Section</span></span>  
 [<span data-ttu-id="b1ea7-111">Načítání dat pomocí čtečky dat</span><span class="sxs-lookup"><span data-stu-id="b1ea7-111">Retrieving Data Using a DataReader</span></span>](retrieving-data-using-a-datareader.md)  
 <span data-ttu-id="b1ea7-112">Popisuje objekt **DataReader** ADO.NET a jeho použití k vrácení datového proudu výsledků ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-112">Describes the ADO.NET **DataReader** object and how to use it to return a stream of results from a data source.</span></span>  
  
 [<span data-ttu-id="b1ea7-113">Naplnění datové sady z adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="b1ea7-113">Populating a DataSet from a DataAdapter</span></span>](populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="b1ea7-114">Popisuje, jak vyplnit `DataSet` tabulky, sloupce a řádky pomocí tabulek, sloupců a řádků. `DataAdapter`</span><span class="sxs-lookup"><span data-stu-id="b1ea7-114">Describes how to fill a `DataSet` with tables, columns, and rows by using a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="b1ea7-115">Parametry adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="b1ea7-115">DataAdapter Parameters</span></span>](dataadapter-parameters.md)  
 <span data-ttu-id="b1ea7-116">Popisuje, jak použít parametry s vlastnostmi `DataAdapter` příkazu, včetně způsobu mapování obsahu sloupce `DataSet` v nástroji na parametr příkazu.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-116">Describes how to use parameters with the command properties of a `DataAdapter` including how to map the contents of a column in a `DataSet` to a command parameter.</span></span>  
  
 [<span data-ttu-id="b1ea7-117">Přidání existujících omezení do datové sady</span><span class="sxs-lookup"><span data-stu-id="b1ea7-117">Adding Existing Constraints to a DataSet</span></span>](adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="b1ea7-118">Popisuje, jak přidat existující omezení do `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-118">Describes how to add existing constraints to a `DataSet`.</span></span>  
  
 [<span data-ttu-id="b1ea7-119">Mapování adaptéru dat, datové tabulky a datového sloupce</span><span class="sxs-lookup"><span data-stu-id="b1ea7-119">DataAdapter DataTable and DataColumn Mappings</span></span>](dataadapter-datatable-and-datacolumn-mappings.md)  
 <span data-ttu-id="b1ea7-120">Popisuje, jak nastavit `DataTableMappings` a `ColumnMappings` pro `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-120">Describes how to set up `DataTableMappings` and `ColumnMappings` for a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="b1ea7-121">Stránkování prostřednictvím výsledku dotazu</span><span class="sxs-lookup"><span data-stu-id="b1ea7-121">Paging Through a Query Result</span></span>](paging-through-a-query-result.md)  
 <span data-ttu-id="b1ea7-122">Poskytuje příklad zobrazení výsledků dotazu jako stránek dat.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-122">Provides an example of viewing the results of a query as pages of data.</span></span>  
  
 [<span data-ttu-id="b1ea7-123">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="b1ea7-123">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="b1ea7-124">Popisuje, jak použít `DataAdapter` k vyřešení změn `DataSet` v databázi.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-124">Describes how to use a `DataAdapter` to resolve changes in a `DataSet` back to the database.</span></span>  
  
 [<span data-ttu-id="b1ea7-125">Zpracování událostí adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="b1ea7-125">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)  
 <span data-ttu-id="b1ea7-126">Popisuje `DataAdapter` události a jejich použití.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-126">Describes `DataAdapter` events and how to use them.</span></span>  
  
 [<span data-ttu-id="b1ea7-127">Provádění dávkových operací pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="b1ea7-127">Performing Batch Operations Using DataAdapters</span></span>](performing-batch-operations-using-dataadapters.md)  
 <span data-ttu-id="b1ea7-128">Popisuje zvýšení výkonu aplikace tím, že omezuje počet přenosů, které se SQL Server při aplikování `DataSet`aktualizací z.</span><span class="sxs-lookup"><span data-stu-id="b1ea7-128">Describes enhancing application performance by reducing the number of round trips to SQL Server when applying updates from the `DataSet`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ea7-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1ea7-129">See also</span></span>

- [<span data-ttu-id="b1ea7-130">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="b1ea7-130">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="b1ea7-131">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="b1ea7-131">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="b1ea7-132">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="b1ea7-132">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="b1ea7-133">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="b1ea7-133">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="b1ea7-134">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b1ea7-134">ADO.NET Overview</span></span>](ado-net-overview.md)
