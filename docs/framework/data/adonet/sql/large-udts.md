---
title: Velké uživatelsky definované typy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 015ce896e49b3a6a932c36db867271b4ac4c64c8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303476"
---
# <a name="large-udts"></a><span data-ttu-id="a6b29-102">Velké uživatelsky definované typy</span><span class="sxs-lookup"><span data-stu-id="a6b29-102">Large UDTs</span></span>
<span data-ttu-id="a6b29-103">Uživatelem definované typy (UDT) umožňují vývojářům rozšířit systém skalárního typu na server uložením common language runtime (CLR) objekty v databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a6b29-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="a6b29-104">Uživatelsky definovaný typ může obsahovat několik elementů a může mít chování, na rozdíl od tradičních alias datové typy, které se skládají z jednoho typ dat systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a6b29-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6b29-105">Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) abyste mohli využívat rozšířenou podporu SqlClient pro velké uživatelsky definované typy.</span><span class="sxs-lookup"><span data-stu-id="a6b29-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="a6b29-106">Dříve byly omezené na maximální velikosti 8 kb uživatelsky definované typy.</span><span class="sxs-lookup"><span data-stu-id="a6b29-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="a6b29-107">V systému SQL Server 2008, byla odebrána toto omezení pro uživatelsky definované typy, které mají formát <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span><span class="sxs-lookup"><span data-stu-id="a6b29-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="a6b29-108">Úplnou dokumentaci pro typy definované uživatelem najdete v článku verze SQL Server Books Online pro verzi SQL serveru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="a6b29-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 **<span data-ttu-id="a6b29-109">SQL Server Books Online</span><span class="sxs-lookup"><span data-stu-id="a6b29-109">SQL Server Books Online</span></span>**  
  
1. [<span data-ttu-id="a6b29-110">Uživatelem definované typy CLR</span><span class="sxs-lookup"><span data-stu-id="a6b29-110">CLR User-Defined Types</span></span>](https://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="a6b29-111">Načítání schémat UDT pomocí GetSchema</span><span class="sxs-lookup"><span data-stu-id="a6b29-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="a6b29-112"><xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Metoda <xref:System.Data.SqlClient.SqlConnection> vrátí informace o schématu v databázi <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="a6b29-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a6b29-113">Další informace najdete v tématu [kolekce schémat SQL serveru](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="a6b29-113">For more information, see [SQL Server Schema Collections](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="a6b29-114">Hodnoty sloupců GetSchemaTable pro uživatelsky definovaný typ</span><span class="sxs-lookup"><span data-stu-id="a6b29-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="a6b29-115"><xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Metodu <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.DataTable> popisující sloupce metadat.</span><span class="sxs-lookup"><span data-stu-id="a6b29-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="a6b29-116">Následující tabulka popisuje rozdíly mezi metadata sloupce pro velké uživatelsky definované typy mezi systémem SQL Server 2005 a SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="a6b29-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="a6b29-117">SqlDataReader sloupec</span><span class="sxs-lookup"><span data-stu-id="a6b29-117">SqlDataReader column</span></span>|<span data-ttu-id="a6b29-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="a6b29-118">SQL Server 2005</span></span>|<span data-ttu-id="a6b29-119">SQL Server 2008 nebo novější</span><span class="sxs-lookup"><span data-stu-id="a6b29-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="a6b29-120">Se liší</span><span class="sxs-lookup"><span data-stu-id="a6b29-120">Varies</span></span>|<span data-ttu-id="a6b29-121">Se liší</span><span class="sxs-lookup"><span data-stu-id="a6b29-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="a6b29-122">255</span><span class="sxs-lookup"><span data-stu-id="a6b29-122">255</span></span>|<span data-ttu-id="a6b29-123">255</span><span class="sxs-lookup"><span data-stu-id="a6b29-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="a6b29-124">255</span><span class="sxs-lookup"><span data-stu-id="a6b29-124">255</span></span>|<span data-ttu-id="a6b29-125">255</span><span class="sxs-lookup"><span data-stu-id="a6b29-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="a6b29-126">UDT instance</span><span class="sxs-lookup"><span data-stu-id="a6b29-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="a6b29-127">UDT instance</span><span class="sxs-lookup"><span data-stu-id="a6b29-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="a6b29-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="a6b29-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="a6b29-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="a6b29-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="a6b29-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="a6b29-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="a6b29-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="a6b29-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="a6b29-132">Tři části názvu určenému jako *Database.SchemaName.TypeName*.</span><span class="sxs-lookup"><span data-stu-id="a6b29-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="a6b29-133">Se liší</span><span class="sxs-lookup"><span data-stu-id="a6b29-133">Varies</span></span>|<span data-ttu-id="a6b29-134">Se liší</span><span class="sxs-lookup"><span data-stu-id="a6b29-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="a6b29-135">SqlDataReader Considerations</span><span class="sxs-lookup"><span data-stu-id="a6b29-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="a6b29-136"><xref:System.Data.SqlClient.SqlDataReader> Se prodloužila, od SQL Server 2008 pro podporu načítání velkých hodnot UDT.</span><span class="sxs-lookup"><span data-stu-id="a6b29-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="a6b29-137">Jak velké hodnoty UDT jsou zpracovány <xref:System.Data.SqlClient.SqlDataReader> závisí na verzi systému SQL Server používáte, stejně jako na `Type System Version` zadaná v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="a6b29-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="a6b29-138">Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6b29-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="a6b29-139">Tyto metody <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.SqlTypes.SqlBinary> místo UDT při `Type System Version` je nastavena na SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="a6b29-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="a6b29-140">Následující metody vrátí pole `Byte[]` místo UDT při `Type System Version` je nastavena na SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="a6b29-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="a6b29-141">Všimněte si, že žádné převody jsou provedeny pro aktuální verzi ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a6b29-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="a6b29-142">Určení SqlParameters</span><span class="sxs-lookup"><span data-stu-id="a6b29-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="a6b29-143">Následující <xref:System.Data.SqlClient.SqlParameter> vlastnosti se rozšířily a pracovat s velké uživatelsky definované typy.</span><span class="sxs-lookup"><span data-stu-id="a6b29-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="a6b29-144">Vlastnost SqlParameter</span><span class="sxs-lookup"><span data-stu-id="a6b29-144">SqlParameter Property</span></span>|<span data-ttu-id="a6b29-145">Popis</span><span class="sxs-lookup"><span data-stu-id="a6b29-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="a6b29-146">Získá nebo nastaví objekt, který představuje hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="a6b29-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="a6b29-147">Výchozí hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="a6b29-147">The default is null.</span></span> <span data-ttu-id="a6b29-148">Vlastnost může být `SqlBinary`, `Byte[]`, nebo spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="a6b29-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="a6b29-149">Získá nebo nastaví objekt, který představuje hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="a6b29-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="a6b29-150">Výchozí hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="a6b29-150">The default is null.</span></span> <span data-ttu-id="a6b29-151">Vlastnost může být `SqlBinary`, `Byte[]`, nebo spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="a6b29-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="a6b29-152">Získá nebo nastaví velikost hodnotu parametru vyřešit.</span><span class="sxs-lookup"><span data-stu-id="a6b29-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="a6b29-153">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="a6b29-153">The default value is 0.</span></span> <span data-ttu-id="a6b29-154">Vlastnost může být celé číslo, které představuje velikost hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="a6b29-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="a6b29-155">Pro velké uživatelsky definované typy může být skutečná velikost UDT nebo -1 pro neznámý.</span><span class="sxs-lookup"><span data-stu-id="a6b29-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="a6b29-156">Příklad načítání dat</span><span class="sxs-lookup"><span data-stu-id="a6b29-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="a6b29-157">Následující fragment kódu ukazuje, jak načíst velkých objemů dat UDT.</span><span class="sxs-lookup"><span data-stu-id="a6b29-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="a6b29-158">`connectionString` Proměnné předpokládá platné připojení k databázi SQL serveru a `commandString` proměnné předpokládá platným příkazem SELECT s sloupec primárního klíče uvedená jako první.</span><span class="sxs-lookup"><span data-stu-id="a6b29-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6b29-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6b29-159">See also</span></span>

- [<span data-ttu-id="a6b29-160">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="a6b29-160">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="a6b29-161">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="a6b29-161">Retrieving Database Schema Information</span></span>](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="a6b29-162">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="a6b29-162">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [<span data-ttu-id="a6b29-163">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="a6b29-163">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="a6b29-164">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="a6b29-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
