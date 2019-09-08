---
title: Načítání informací o databázovém schématu
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 26b234e35a0d0849914d87b61f4e8c8a87599448
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782739"
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="94ed0-102">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="94ed0-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="94ed0-103">Získání informací o schématu z databáze je provedeno procesem zjišťování schématu.</span><span class="sxs-lookup"><span data-stu-id="94ed0-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="94ed0-104">Zjišťování schématu umožňuje aplikacím požádat, aby se spravované zprostředkovatele vyhledali a vraceli informace o schématu databáze, označované také jako *metadata*dané databáze.</span><span class="sxs-lookup"><span data-stu-id="94ed0-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="94ed0-105">Různé prvky schématu databáze, jako jsou tabulky, sloupce a uložené procedury, se zveřejňují prostřednictvím kolekcí schémat.</span><span class="sxs-lookup"><span data-stu-id="94ed0-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="94ed0-106">Každá kolekce schémat obsahuje nejrůznější informace o schématu specifické pro používaného poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="94ed0-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="94ed0-107">Každé z .NET Framework spravovaných zprostředkovatelů implementuje ve třídě **Connection** metodu **GetSchema** a informace o schématu vrácené z metody **GetSchema** jsou <xref:System.Data.DataTable>v podobě.</span><span class="sxs-lookup"><span data-stu-id="94ed0-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="94ed0-108">Metoda **GetSchema** je přetížená metoda, která poskytuje volitelné parametry pro určení kolekce schématu, která se má vrátit, a omezení množství vrácených informací.</span><span class="sxs-lookup"><span data-stu-id="94ed0-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="94ed0-109">Poskytovatelé dat .NET Framework pro OLE DB, ODBC, Oracle a SqlClient poskytují metodu **GetSchema** , která vrací objekt DataTable popisující metadata sloupce **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="94ed0-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="94ed0-110">Zprostředkovatel dat .NET Framework pro OLE DB také zpřístupňuje informace o schématu pomocí <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> metody <xref:System.Data.OleDb.OleDbConnection> objektu.</span><span class="sxs-lookup"><span data-stu-id="94ed0-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="94ed0-111">Jako argumenty **GetOleDbSchemaTable** přebírá <xref:System.Data.OleDb.OleDbSchemaGuid> , který identifikuje informace o schématu, které se mají vrátit, a pole omezení u těchto vrácených sloupců.</span><span class="sxs-lookup"><span data-stu-id="94ed0-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="94ed0-112">**GetOleDbSchemaTable** vrátí hodnotu <xref:System.Data.DataTable> , která je vyplněna požadovanými informacemi o schématu.</span><span class="sxs-lookup"><span data-stu-id="94ed0-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94ed0-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="94ed0-113">In This Section</span></span>  
 [<span data-ttu-id="94ed0-114">Příkaz GetSchema a kolekce schémat</span><span class="sxs-lookup"><span data-stu-id="94ed0-114">GetSchema and Schema Collections</span></span>](getschema-and-schema-collections.md)  
 <span data-ttu-id="94ed0-115">Popisuje metodu **GetSchema** a způsob, jak ji lze použít k načtení a omezení informací o schématu z databáze.</span><span class="sxs-lookup"><span data-stu-id="94ed0-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="94ed0-116">Omezení schématu</span><span class="sxs-lookup"><span data-stu-id="94ed0-116">Schema Restrictions</span></span>  
 <span data-ttu-id="94ed0-117">Popisuje omezení schématu, která lze použít s **GetSchema**.</span><span class="sxs-lookup"><span data-stu-id="94ed0-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="94ed0-118">Společné kolekce schémat</span><span class="sxs-lookup"><span data-stu-id="94ed0-118">Common Schema Collections</span></span>](common-schema-collections.md)  
 <span data-ttu-id="94ed0-119">Popisuje všechny společné kolekce schémat podporované všemi .NET Framework spravovanými zprostředkovateli.</span><span class="sxs-lookup"><span data-stu-id="94ed0-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="94ed0-120">Kolekce schémat SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="94ed0-120">SQL Server Schema Collections</span></span>](sql-server-schema-collections.md)  
 <span data-ttu-id="94ed0-121">Popisuje kolekci schémat podporovanou poskytovatelem .NET Framework pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="94ed0-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="94ed0-122">Kolekce schémat Oracle</span><span class="sxs-lookup"><span data-stu-id="94ed0-122">Oracle Schema Collections</span></span>](oracle-schema-collections.md)  
 <span data-ttu-id="94ed0-123">Popisuje kolekci schémat podporovanou poskytovatelem .NET Framework pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="94ed0-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="94ed0-124">Kolekce schémat ODBC</span><span class="sxs-lookup"><span data-stu-id="94ed0-124">ODBC Schema Collections</span></span>](odbc-schema-collections.md)  
 <span data-ttu-id="94ed0-125">Popisuje kolekce schémat pro ovladače rozhraní ODBC.</span><span class="sxs-lookup"><span data-stu-id="94ed0-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="94ed0-126">Kolekce schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="94ed0-126">OLE DB Schema Collections</span></span>](ole-db-schema-collections.md)  
 <span data-ttu-id="94ed0-127">Popisuje kolekce schémat pro poskytovatele OLE DB.</span><span class="sxs-lookup"><span data-stu-id="94ed0-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="94ed0-128">Reference</span><span class="sxs-lookup"><span data-stu-id="94ed0-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="94ed0-129">Popisuje <xref:System.Data.Common.DbConnection> metodu **GetSchema** třídy.</span><span class="sxs-lookup"><span data-stu-id="94ed0-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="94ed0-130">Popisuje <xref:System.Data.Odbc.OdbcConnection> metodu **GetSchema** třídy.</span><span class="sxs-lookup"><span data-stu-id="94ed0-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="94ed0-131">Popisuje <xref:System.Data.OleDb.OleDbConnection> metodu **GetSchema** třídy.</span><span class="sxs-lookup"><span data-stu-id="94ed0-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="94ed0-132">Popisuje <xref:System.Data.OracleClient.OracleConnection> metodu **GetSchema** třídy.</span><span class="sxs-lookup"><span data-stu-id="94ed0-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="94ed0-133">Popisuje <xref:System.Data.SqlClient.SqlConnection> metodu **GetSchema** třídy.</span><span class="sxs-lookup"><span data-stu-id="94ed0-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="94ed0-134">Popisuje <xref:System.Data.Common.DbDataReader> metodu **GetSchema** třídy třídy.</span><span class="sxs-lookup"><span data-stu-id="94ed0-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="94ed0-135">Popisuje <xref:System.Data.Odbc.OdbcDataReader> metodu **GetSchema** třídy třídy.</span><span class="sxs-lookup"><span data-stu-id="94ed0-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="94ed0-136">Popisuje <xref:System.Data.OleDb.OleDbDataReader> metodu **GetSchema** třídy třídy.</span><span class="sxs-lookup"><span data-stu-id="94ed0-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="94ed0-137">Popisuje <xref:System.Data.OracleClient.OracleDataReader> metodu **GetSchema** třídy třídy.</span><span class="sxs-lookup"><span data-stu-id="94ed0-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="94ed0-138">Popisuje <xref:System.Data.SqlClient.SqlDataReader> metodu **GetSchema** třídy třídy.</span><span class="sxs-lookup"><span data-stu-id="94ed0-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94ed0-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94ed0-139">See also</span></span>

- [<span data-ttu-id="94ed0-140">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="94ed0-140">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="94ed0-141">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="94ed0-141">ADO.NET Overview</span></span>](ado-net-overview.md)
