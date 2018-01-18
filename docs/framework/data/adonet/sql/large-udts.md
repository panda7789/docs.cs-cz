---
title: "Velké UDT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6090221981c8aaa894f94ebb7910659a1dbf210c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="large-udts"></a><span data-ttu-id="cc24a-102">Velké UDT</span><span class="sxs-lookup"><span data-stu-id="cc24a-102">Large UDTs</span></span>
<span data-ttu-id="cc24a-103">Uživatelem definované typy (UDT) umožňují vývojář rozšíření systému skalárního typu serveru uložením běžně používané objekty language runtime (CLR) v databázi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cc24a-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="cc24a-104">UDT může obsahovat více elementů a může mít chování, na rozdíl od tradičních alias datové typy, které se skládají z jedné typ dat systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cc24a-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc24a-105">Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) využívat rozšířenou podporu SqlClient pro velké UDT.</span><span class="sxs-lookup"><span data-stu-id="cc24a-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="cc24a-106">Dříve byly UDT omezen na maximální velikost 8 kB.</span><span class="sxs-lookup"><span data-stu-id="cc24a-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="cc24a-107">V systému SQL Server 2008, byla odebrána toto omezení pro UDT, které mají do formátu podle <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span><span class="sxs-lookup"><span data-stu-id="cc24a-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="cc24a-108">Kompletní dokumentaci pro uživatelem definované typy najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cc24a-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="cc24a-109">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="cc24a-109">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="cc24a-110">Uživatelem definované typy CLR</span><span class="sxs-lookup"><span data-stu-id="cc24a-110">CLR User-Defined Types</span></span>](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="cc24a-111">Načítání schémat UDT pomocí GetSchema</span><span class="sxs-lookup"><span data-stu-id="cc24a-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="cc24a-112"><xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Metodu <xref:System.Data.SqlClient.SqlConnection> vrátí informace o schématu v databázi <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="cc24a-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="cc24a-113">Další informace najdete v tématu [kolekcemi schémat SQL serveru](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="cc24a-113">For more information, see [SQL Server Schema Collections](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="cc24a-114">Hodnoty ve sloupcích GetSchemaTable pro uživatelsky definovaný typ</span><span class="sxs-lookup"><span data-stu-id="cc24a-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="cc24a-115"><xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Metodu <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.DataTable> metadata sloupce, který popisuje.</span><span class="sxs-lookup"><span data-stu-id="cc24a-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="cc24a-116">Následující tabulka popisuje rozdíly v metadata sloupce pro velké UDT mezi systému SQL Server 2005 a SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="cc24a-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="cc24a-117">Sloupec SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="cc24a-117">SqlDataReader column</span></span>|<span data-ttu-id="cc24a-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="cc24a-118">SQL Server 2005</span></span>|<span data-ttu-id="cc24a-119">SQL Server 2008 a novější</span><span class="sxs-lookup"><span data-stu-id="cc24a-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="cc24a-120">Je to různé.</span><span class="sxs-lookup"><span data-stu-id="cc24a-120">Varies</span></span>|<span data-ttu-id="cc24a-121">Je to různé.</span><span class="sxs-lookup"><span data-stu-id="cc24a-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="cc24a-122">255</span><span class="sxs-lookup"><span data-stu-id="cc24a-122">255</span></span>|<span data-ttu-id="cc24a-123">255</span><span class="sxs-lookup"><span data-stu-id="cc24a-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="cc24a-124">255</span><span class="sxs-lookup"><span data-stu-id="cc24a-124">255</span></span>|<span data-ttu-id="cc24a-125">255</span><span class="sxs-lookup"><span data-stu-id="cc24a-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="cc24a-126">UDT instance</span><span class="sxs-lookup"><span data-stu-id="cc24a-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="cc24a-127">UDT instance</span><span class="sxs-lookup"><span data-stu-id="cc24a-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="cc24a-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="cc24a-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="cc24a-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="cc24a-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="cc24a-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="cc24a-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="cc24a-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="cc24a-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="cc24a-132">Název zadaný jako část tří *Database.SchemaName.TypeName*.</span><span class="sxs-lookup"><span data-stu-id="cc24a-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="cc24a-133">Je to různé.</span><span class="sxs-lookup"><span data-stu-id="cc24a-133">Varies</span></span>|<span data-ttu-id="cc24a-134">Je to různé.</span><span class="sxs-lookup"><span data-stu-id="cc24a-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="cc24a-135">Aspekty SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="cc24a-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="cc24a-136"><xref:System.Data.SqlClient.SqlDataReader> Bylo rozšířeno od verze systému SQL Server 2008 pro podporu načítání velkých UDT hodnot.</span><span class="sxs-lookup"><span data-stu-id="cc24a-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="cc24a-137">Jak se zpracovávají velké hodnoty UDT <xref:System.Data.SqlClient.SqlDataReader> závisí na verzi systému SQL Server, kterou používáte, stejně jako na `Type System Version` zadaný v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="cc24a-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="cc24a-138">Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc24a-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="cc24a-139">Tyto metody <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.SqlTypes.SqlBinary> místo UDT při `Type System Version` je nastavena na systém SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="cc24a-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="cc24a-140">Následující metody vrátí pole `Byte[]` místo UDT při `Type System Version` je nastavena na systém SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="cc24a-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="cc24a-141">Všimněte si, že žádné převody jsou vytvářeny pro aktuální verzi ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="cc24a-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="cc24a-142">Zadání SqlParameters</span><span class="sxs-lookup"><span data-stu-id="cc24a-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="cc24a-143">Následující <xref:System.Data.SqlClient.SqlParameter> vlastnosti se rozšířily a pracovat s velké UDT.</span><span class="sxs-lookup"><span data-stu-id="cc24a-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="cc24a-144">Vlastnost SqlParameter</span><span class="sxs-lookup"><span data-stu-id="cc24a-144">SqlParameter Property</span></span>|<span data-ttu-id="cc24a-145">Popis</span><span class="sxs-lookup"><span data-stu-id="cc24a-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="cc24a-146">Získá nebo nastaví objekt, který představuje hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="cc24a-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="cc24a-147">Výchozí hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="cc24a-147">The default is null.</span></span> <span data-ttu-id="cc24a-148">Vlastnost, která může být `SqlBinary`, `Byte[]`, nebo spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="cc24a-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="cc24a-149">Získá nebo nastaví objekt, který představuje hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="cc24a-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="cc24a-150">Výchozí hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="cc24a-150">The default is null.</span></span> <span data-ttu-id="cc24a-151">Vlastnost, která může být `SqlBinary`, `Byte[]`, nebo spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="cc24a-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="cc24a-152">Získá nebo nastaví velikost hodnoty parametru vyřešit.</span><span class="sxs-lookup"><span data-stu-id="cc24a-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="cc24a-153">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="cc24a-153">The default value is 0.</span></span> <span data-ttu-id="cc24a-154">Vlastnost může být celé číslo, které představuje velikost hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="cc24a-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="cc24a-155">Pro velké UDT může být skutečná velikost UDT nebo -1 pro neznámý.</span><span class="sxs-lookup"><span data-stu-id="cc24a-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="cc24a-156">Příklad načítání dat</span><span class="sxs-lookup"><span data-stu-id="cc24a-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="cc24a-157">Následující fragment kódu ukazuje, jak načíst velkých objemů dat UDT.</span><span class="sxs-lookup"><span data-stu-id="cc24a-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="cc24a-158">`connectionString` Proměnná předpokládá máte platné připojení k databázi systému SQL Server a `commandString` proměnná předpokládá platný příkaz SELECT s sloupec primárního klíče uvedená jako první.</span><span class="sxs-lookup"><span data-stu-id="cc24a-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
```csharp  
using (SqlConnection connection = new SqlConnection(   
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc24a-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc24a-159">See Also</span></span>  
 [<span data-ttu-id="cc24a-160">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="cc24a-160">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="cc24a-161">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="cc24a-161">Retrieving Database Schema Information</span></span>](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="cc24a-162">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="cc24a-162">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="cc24a-163">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="cc24a-163">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="cc24a-164">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="cc24a-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
