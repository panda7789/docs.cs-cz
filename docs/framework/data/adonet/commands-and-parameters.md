---
title: "Příkazy a parametry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f28f4ed728ee429a691a0a19b3fc143ac0e832ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="commands-and-parameters"></a><span data-ttu-id="ce3bf-102">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="ce3bf-102">Commands and Parameters</span></span>
<span data-ttu-id="ce3bf-103">Po navázání připojení ke zdroji dat, můžete provést příkazy a vrácení výsledků z zdroje dat pomocí <xref:System.Data.Common.DbCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-103">After establishing a connection to a data source, you can execute commands and return results from the data source using a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="ce3bf-104">Můžete vytvořit příkaz pomocí některé z konstruktorů příkaz zprostředkovatel dat .NET Framework, které pracujete.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-104">You can create a command using one of the command constructors for the .NET Framework data provider you are working with.</span></span> <span data-ttu-id="ce3bf-105">Konstruktory může trvat volitelné argumenty, jako je například příkazu SQL k provedení ve zdroji dat <xref:System.Data.Common.DbConnection> objekt, nebo <xref:System.Data.Common.DbTransaction> objektu.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-105">Constructors can take optional arguments, such as an SQL statement to execute at the data source, a <xref:System.Data.Common.DbConnection> object, or a <xref:System.Data.Common.DbTransaction> object.</span></span> <span data-ttu-id="ce3bf-106">Tyto objekty můžete také nakonfigurovat jako vlastnosti příkazu.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-106">You can also configure those objects as properties of the command.</span></span> <span data-ttu-id="ce3bf-107">Můžete také vytvořit příkaz pro konkrétní připojení pomocí <xref:System.Data.Common.DbConnection.CreateCommand%2A> metodu `DbConnection` objektu.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-107">You can also create a command for a particular connection using the <xref:System.Data.Common.DbConnection.CreateCommand%2A> method of a `DbConnection` object.</span></span> <span data-ttu-id="ce3bf-108">Příkaz jazyka SQL, který je vykonáván příkaz můžete nakonfigurovat pomocí <xref:System.Data.Common.DbCommand.CommandText%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-108">The SQL statement being executed by the command can be configured using the <xref:System.Data.Common.DbCommand.CommandText%2A> property.</span></span>  
  
 <span data-ttu-id="ce3bf-109">Má každý zprostředkovatel dat .NET Framework je součástí rozhraní .NET Framework `Command` objektu.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-109">Each .NET Framework data provider included with the .NET Framework has a `Command` object.</span></span> <span data-ttu-id="ce3bf-110">Zahrnuje zprostředkovatel dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbCommand> objektu, zahrnuje zprostředkovatel dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlCommand> objektu, zahrnuje zprostředkovatel dat .NET Framework pro ODBC <xref:System.Data.Odbc.OdbcCommand> objektu a rozhraní .NET Framework Zprostředkovatel dat pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-110">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce3bf-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ce3bf-111">In This Section</span></span>  
 [<span data-ttu-id="ce3bf-112">Spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="ce3bf-112">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 <span data-ttu-id="ce3bf-113">Popisuje technologie ADO.NET `Command` objekt a způsobu jeho použití k provedení dotazy a příkazy pro datový zdroj.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-113">Describes the ADO.NET `Command` object and how to use it to execute queries and commands against a data source.</span></span>  
  
 [<span data-ttu-id="ce3bf-114">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="ce3bf-114">Configuring Parameters and Parameter Data Types</span></span>](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 <span data-ttu-id="ce3bf-115">Popisuje práci s `Command` parametry, včetně směr, datové typy a syntaxe parametru.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-115">Describes working with `Command` parameters, including direction, data types, and parameter syntax.</span></span>  
  
 [<span data-ttu-id="ce3bf-116">Generování příkazů s CommandBuilders</span><span class="sxs-lookup"><span data-stu-id="ce3bf-116">Generating Commands with CommandBuilders</span></span>](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 <span data-ttu-id="ce3bf-117">Popisuje, jak používat příkaz počítačů k automatickému generování příkazy INSERT, UPDATE a DELETE pro `DataAdapter` má vyberte příkaz jedné tabulky.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-117">Describes how to use command builders to automatically generate INSERT, UPDATE, and DELETE commands for a `DataAdapter` that has a single-table SELECT command.</span></span>  
  
 [<span data-ttu-id="ce3bf-118">Získání jedné hodnoty z databáze</span><span class="sxs-lookup"><span data-stu-id="ce3bf-118">Obtaining a Single Value from a Database</span></span>](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 <span data-ttu-id="ce3bf-119">Popisuje postup použití `ExecuteScalar` metodu `Command` objekt, který chcete vrátit jednu hodnotu z dotazu databáze.</span><span class="sxs-lookup"><span data-stu-id="ce3bf-119">Describes how to use the `ExecuteScalar` method of a `Command` object to return a single value from a database query.</span></span>  
  
 [<span data-ttu-id="ce3bf-120">Použití příkazů pro změny dat</span><span class="sxs-lookup"><span data-stu-id="ce3bf-120">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 <span data-ttu-id="ce3bf-121">Popisuje postup použití zprostředkovatele dat pro spuštění uložené procedury nebo data (příkazy DDL definition language).</span><span class="sxs-lookup"><span data-stu-id="ce3bf-121">Describes how to use a data provider to execute stored procedures or data definition language (DDL) statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce3bf-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce3bf-122">See Also</span></span>  
 [<span data-ttu-id="ce3bf-123">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="ce3bf-123">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="ce3bf-124">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="ce3bf-124">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="ce3bf-125">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="ce3bf-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="ce3bf-126">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="ce3bf-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
