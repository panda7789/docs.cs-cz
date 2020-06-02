---
title: Načítání a úpravy dat
description: V .NET Framework slouží poskytovatelé dat v ADO.NET jako most mezi aplikací a zdrojem dat za účelem čtení a aktualizace dat.
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: f916324dc829526a5e6b0078021b09786755f666
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286608"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="e6f0e-103">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e6f0e-103">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="e6f0e-104">Primární funkce libovolné databázové aplikace se připojuje ke zdroji dat a načítá data, která obsahuje.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-104">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="e6f0e-105">Poskytovatelé dat .NET Framework ADO.NET slouží jako most mezi aplikací a zdrojem dat, což umožňuje provádět příkazy a také načítat data pomocí datového typu **DataReader** nebo **DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-105">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="e6f0e-106">Klíčovou funkcí libovolné databázové aplikace je možnost aktualizovat data uložená v databázi.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-106">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="e6f0e-107">V ADO.NET aktualizace dat zahrnuje použití objektů příkazového řádku **DataAdapter** a a a <xref:System.Data.DataSet> může také zahrnovat použití transakcí. **Command**</span><span class="sxs-lookup"><span data-stu-id="e6f0e-107">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6f0e-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e6f0e-108">In This Section</span></span>  
 [<span data-ttu-id="e6f0e-109">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="e6f0e-109">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="e6f0e-110">Popisuje, jak navázat připojení ke zdroji dat a jak pracovat s událostmi připojení.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-110">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="e6f0e-111">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="e6f0e-111">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="e6f0e-112">Obsahuje témata popisující různé aspekty použití připojovacích řetězců, včetně klíčových slov připojovacích řetězců, bezpečnostních údajů a jejich ukládání a načítání.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-112">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="e6f0e-113">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="e6f0e-113">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="e6f0e-114">Popisuje sdružování připojení pro poskytovatele .NET Framework dat.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-114">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="e6f0e-115">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="e6f0e-115">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="e6f0e-116">Obsahuje témata popisující, jak vytvořit příkazy a tvůrci příkazů, nakonfigurovat parametry a spustit příkazy pro načtení a úpravu dat.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-116">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="e6f0e-117">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="e6f0e-117">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="e6f0e-118">Obsahuje témata popisující datačtecí a dataadaptéry, parametry, zpracování událostí DataAdapter a provádění operací Batch.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-118">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="e6f0e-119">Transakce a souběžnost</span><span class="sxs-lookup"><span data-stu-id="e6f0e-119">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="e6f0e-120">Obsahuje témata popisující, jak provádět místní transakce, distribuované transakce a pracovat s optimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-120">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="e6f0e-121">Načítání hodnot identity nebo automatického číslování</span><span class="sxs-lookup"><span data-stu-id="e6f0e-121">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="e6f0e-122">Poskytuje příklad mapování hodnot generovaných pro sloupec **identity** v SQL Server tabulce nebo pro pole **AutoNumber** v tabulce Microsoft Access, do sloupce vloženého řádku v tabulce.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-122">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="e6f0e-123">Popisuje sloučení hodnot identity v `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="e6f0e-123">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="e6f0e-124">Načítání binárních dat</span><span class="sxs-lookup"><span data-stu-id="e6f0e-124">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="e6f0e-125">Popisuje, jak načíst binární data nebo velké datové struktury pomocí `CommandBehavior` .`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="e6f0e-125">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="e6f0e-126">Chcete-li změnit výchozí chování `DataReader` .</span><span class="sxs-lookup"><span data-stu-id="e6f0e-126">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="e6f0e-127">Úpravy dat pomocí uložených procedur</span><span class="sxs-lookup"><span data-stu-id="e6f0e-127">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="e6f0e-128">Popisuje způsob použití vstupních parametrů a výstupních parametrů uložených procedur pro vložení řádku do databáze a vrácení nové hodnoty identity.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-128">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="e6f0e-129">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="e6f0e-129">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="e6f0e-130">Popisuje, jak získat dostupné databáze nebo katalogy, tabulky a zobrazení v databázi, omezeních, která existují pro tabulky, a další informace o schématu ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-130">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="e6f0e-131">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="e6f0e-131">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="e6f0e-132">Popisuje model továrny poskytovatele a ukazuje, jak používat základní třídy v `System.Data.Common` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-132">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="e6f0e-133">Trasování data v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e6f0e-133">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="e6f0e-134">Popisuje, jak ADO.NET poskytuje integrovanou funkci pro trasování dat.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-134">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="e6f0e-135">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="e6f0e-135">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="e6f0e-136">Popisuje čítače výkonu dostupné pro `SqlClient` a `OracleClient` .</span><span class="sxs-lookup"><span data-stu-id="e6f0e-136">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="e6f0e-137">Asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="e6f0e-137">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="e6f0e-138">Popisuje podporu ADO.NET pro asynchronní programování.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-138">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="e6f0e-139">Podpora streamování SqlClient</span><span class="sxs-lookup"><span data-stu-id="e6f0e-139">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="e6f0e-140">Popisuje, jak psát aplikace, které streamují data z SQL Server bez toho, aby byla plně načtena v paměti.</span><span class="sxs-lookup"><span data-stu-id="e6f0e-140">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f0e-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6f0e-141">See also</span></span>

- [<span data-ttu-id="e6f0e-142">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e6f0e-142">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="e6f0e-143">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="e6f0e-143">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="e6f0e-144">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e6f0e-144">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="e6f0e-145">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e6f0e-145">SQL Server and ADO.NET</span></span>](./sql/index.md)
- [<span data-ttu-id="e6f0e-146">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e6f0e-146">ADO.NET Overview</span></span>](ado-net-overview.md)
