---
title: "Načítání informací o schématu databáze"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 71493eb91415b5f4695e771c7a549244629bb654
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="c1a2f-102">Načítání informací o schématu databáze</span><span class="sxs-lookup"><span data-stu-id="c1a2f-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="c1a2f-103">Získání informací o schématu z databáze se provádí v procesu zjišťování schématu.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="c1a2f-104">Schéma zjišťování umožňuje aplikacím požádá spravovaného zprostředkovatele najít a vrátí informace o schématu databáze, také známé jako *metadata*, dané databáze.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="c1a2f-105">Prvky schématu jiné databázi, například tabulky, sloupce a uložených procedur se zveřejňují přes kolekcemi schémat.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="c1a2f-106">Každá kolekce schéma obsahuje celou řadu specifické pro použitý zprostředkovatel informace o schématu.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="c1a2f-107">Každý z implementace spravovaných zprostředkovatelé rozhraní .NET Framework **GetSchema** metoda v **připojení** třídy a informace o schématu, která je vrácena z **GetSchema**metoda obsahuje ve formě <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="c1a2f-108">**GetSchema** metoda je přetížené metody, která poskytuje volitelné parametry pro zadání kolekce schémat vrátit a omezení množství vrácených informací.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="c1a2f-109">Zadejte zprostředkovatele dat .NET Framework pro OLE DB, rozhraní ODBC, Oracle a SqlClient **GetSchemaTable** metodu, která vrátí DataTable popisující sloupce metadata **DataReader –**.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="c1a2f-110">Zprostředkovatel dat .NET Framework pro OLE DB také zveřejňuje informace o schématu pomocí <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> metodu <xref:System.Data.OleDb.OleDbConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="c1a2f-111">Jako argumenty **Metoda GetOleDbSchemaTable** trvá <xref:System.Data.OleDb.OleDbSchemaGuid> identifikující informace o schématu vrátit, a pole omezení pro ty vrácení sloupce.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="c1a2f-112">**Metoda GetOleDbSchemaTable** vrátí <xref:System.Data.DataTable> naplněn informacemi požadovaný schématu.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1a2f-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c1a2f-113">In This Section</span></span>  
 [<span data-ttu-id="c1a2f-114">GetSchema a kolekcemi schémat</span><span class="sxs-lookup"><span data-stu-id="c1a2f-114">GetSchema and Schema Collections</span></span>](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 <span data-ttu-id="c1a2f-115">Popisuje **GetSchema** metoda a jak může sloužit k načtení a omezit informace o schématu z databáze.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="c1a2f-116">Omezení schématu</span><span class="sxs-lookup"><span data-stu-id="c1a2f-116">Schema Restrictions</span></span>  
 <span data-ttu-id="c1a2f-117">Popisuje schéma omezení, které lze použít s **GetSchema**.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="c1a2f-118">Společné schéma kolekce</span><span class="sxs-lookup"><span data-stu-id="c1a2f-118">Common Schema Collections</span></span>](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 <span data-ttu-id="c1a2f-119">Popisuje všechny společné schéma kolekce nepodporuje všech zprostředkovatelů spravované rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="c1a2f-120">Kolekcemi schémat serveru SQL</span><span class="sxs-lookup"><span data-stu-id="c1a2f-120">SQL Server Schema Collections</span></span>](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 <span data-ttu-id="c1a2f-121">Popisuje kolekci schémat podporována zprostředkovatelem rozhraní .NET Framework pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="c1a2f-122">Kolekce schématu Oracle</span><span class="sxs-lookup"><span data-stu-id="c1a2f-122">Oracle Schema Collections</span></span>](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 <span data-ttu-id="c1a2f-123">Popisuje kolekci schémat podporována zprostředkovatelem rozhraní .NET Framework pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="c1a2f-124">Kolekce schématu rozhraní ODBC</span><span class="sxs-lookup"><span data-stu-id="c1a2f-124">ODBC Schema Collections</span></span>](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 <span data-ttu-id="c1a2f-125">Popisuje kolekcemi schémat ovladačů ODBC.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="c1a2f-126">Kolekcemi schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="c1a2f-126">OLE DB Schema Collections</span></span>](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 <span data-ttu-id="c1a2f-127">Popisuje kolekcemi schémat pro zprostředkovatele OLE DB.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c1a2f-128">Odkaz</span><span class="sxs-lookup"><span data-stu-id="c1a2f-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="c1a2f-129">Popisuje **GetSchema** metodu <xref:System.Data.Common.DbConnection> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="c1a2f-130">Popisuje **GetSchema** metodu <xref:System.Data.Odbc.OdbcConnection> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="c1a2f-131">Popisuje **GetSchema** metodu <xref:System.Data.OleDb.OleDbConnection> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="c1a2f-132">Popisuje **GetSchema** metodu <xref:System.Data.OracleClient.OracleConnection> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="c1a2f-133">Popisuje **GetSchema** metodu <xref:System.Data.SqlClient.SqlConnection> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="c1a2f-134">Popisuje **GetSchemaTable** metodu <xref:System.Data.Common.DbDataReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="c1a2f-135">Popisuje **GetSchemaTable** metodu <xref:System.Data.Odbc.OdbcDataReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="c1a2f-136">Popisuje **GetSchemaTable** metodu <xref:System.Data.OleDb.OleDbDataReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="c1a2f-137">Popisuje **GetSchemaTable** metodu <xref:System.Data.OracleClient.OracleDataReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="c1a2f-138">Popisuje **GetSchemaTable** metodu <xref:System.Data.SqlClient.SqlDataReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="c1a2f-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a2f-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1a2f-139">See Also</span></span>  
 [<span data-ttu-id="c1a2f-140">Načítání a upravovat Data v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c1a2f-140">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="c1a2f-141">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="c1a2f-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
