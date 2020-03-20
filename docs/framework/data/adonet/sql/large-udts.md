---
title: Velké uživatelsky definované typy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: f55f6eccf3566a2391204e1ca4349ae5dff01954
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148553"
---
# <a name="large-udts"></a><span data-ttu-id="643eb-102">Velké uživatelsky definované typy</span><span class="sxs-lookup"><span data-stu-id="643eb-102">Large UDTs</span></span>
<span data-ttu-id="643eb-103">Uživatelem definované typy (UDT) umožňují vývojáři rozšířit systém skalárního typu serveru uložením objektů CLR (COMMON Language runtime) v databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="643eb-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="643eb-104">UDT s může obsahovat více prvků a může mít chování, na rozdíl od tradičních alias datových typů, které se skládají z jednoho datového typu systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="643eb-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="643eb-105">Chcete-li využít výhod rozšířené podpory rozhraní SqlClient pro velké udts, je nutné nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější).</span><span class="sxs-lookup"><span data-stu-id="643eb-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="643eb-106">Dříve byly udts omezeny na maximální velikost 8 kilobajtů.</span><span class="sxs-lookup"><span data-stu-id="643eb-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="643eb-107">V sql server 2008 toto omezení byla odebrána pro <xref:Microsoft.SqlServer.Server.Format.UserDefined>UDTs, které mají formát .</span><span class="sxs-lookup"><span data-stu-id="643eb-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="643eb-108">Úplnou dokumentaci pro uživatelem definované typy naleznete ve verzi SQL Server Books Online pro verzi serveru SQL Server, který používáte.</span><span class="sxs-lookup"><span data-stu-id="643eb-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="643eb-109">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="643eb-109">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="643eb-110">Uživatelem definované typy CLR</span><span class="sxs-lookup"><span data-stu-id="643eb-110">CLR User-Defined Types</span></span>](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="643eb-111">Načítání schémat UDT pomocí getschema</span><span class="sxs-lookup"><span data-stu-id="643eb-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="643eb-112">Metoda <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> vrátí <xref:System.Data.SqlClient.SqlConnection> informace o schématu databáze <xref:System.Data.DataTable>v .</span><span class="sxs-lookup"><span data-stu-id="643eb-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="643eb-113">Další informace naleznete v tématu [KOLEKCE Schémat serveru SQL Server](../sql-server-schema-collections.md).</span><span class="sxs-lookup"><span data-stu-id="643eb-113">For more information, see [SQL Server Schema Collections](../sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="643eb-114">Hodnoty sloupců schematable pro UDT</span><span class="sxs-lookup"><span data-stu-id="643eb-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="643eb-115">Metoda <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.DataTable> vrátí, který popisuje metadata sloupce.</span><span class="sxs-lookup"><span data-stu-id="643eb-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="643eb-116">Následující tabulka popisuje rozdíly v metadatech sloupce pro velké UDT mezi SQL Server 2005 a SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="643eb-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="643eb-117">Sloupec SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="643eb-117">SqlDataReader column</span></span>|<span data-ttu-id="643eb-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="643eb-118">SQL Server 2005</span></span>|<span data-ttu-id="643eb-119">SQL Server 2008 a novější</span><span class="sxs-lookup"><span data-stu-id="643eb-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="643eb-120">Různé</span><span class="sxs-lookup"><span data-stu-id="643eb-120">Varies</span></span>|<span data-ttu-id="643eb-121">Různé</span><span class="sxs-lookup"><span data-stu-id="643eb-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="643eb-122">255</span><span class="sxs-lookup"><span data-stu-id="643eb-122">255</span></span>|<span data-ttu-id="643eb-123">255</span><span class="sxs-lookup"><span data-stu-id="643eb-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="643eb-124">255</span><span class="sxs-lookup"><span data-stu-id="643eb-124">255</span></span>|<span data-ttu-id="643eb-125">255</span><span class="sxs-lookup"><span data-stu-id="643eb-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="643eb-126">Instance UDT</span><span class="sxs-lookup"><span data-stu-id="643eb-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="643eb-127">Instance UDT</span><span class="sxs-lookup"><span data-stu-id="643eb-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="643eb-128">21`SqlDbType.VarBinary`( )</span><span class="sxs-lookup"><span data-stu-id="643eb-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="643eb-129">29`SqlDbType.Udt`.</span><span class="sxs-lookup"><span data-stu-id="643eb-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="643eb-130">29`SqlDbType.Udt`.</span><span class="sxs-lookup"><span data-stu-id="643eb-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="643eb-131">29`SqlDbType.Udt`.</span><span class="sxs-lookup"><span data-stu-id="643eb-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="643eb-132">Název tři části zadaný jako *Database.SchemaName.TypeName*.</span><span class="sxs-lookup"><span data-stu-id="643eb-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="643eb-133">Různé</span><span class="sxs-lookup"><span data-stu-id="643eb-133">Varies</span></span>|<span data-ttu-id="643eb-134">Různé</span><span class="sxs-lookup"><span data-stu-id="643eb-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="643eb-135">Důležité informace aplikace SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="643eb-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="643eb-136">Byl <xref:System.Data.SqlClient.SqlDataReader> rozšířen počínaje SQL Server 2008 pro podporu načítání velkých hodnot UDT.</span><span class="sxs-lookup"><span data-stu-id="643eb-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="643eb-137">Jak velké hodnoty UDT jsou <xref:System.Data.SqlClient.SqlDataReader> zpracovány a závisí na verzi SQL Server, `Type System Version` který používáte, jakož i na zadané v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="643eb-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="643eb-138">Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="643eb-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="643eb-139">Následující metody <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.SqlTypes.SqlBinary> místo UDT při `Type System Version` je nastavena na SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="643eb-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="643eb-140">Následující metody vrátí pole `Byte[]` namísto UDT při `Type System Version` je nastavena na SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="643eb-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="643eb-141">Všimněte si, že pro aktuální verzi ADO.NET nejsou provedeny žádné převody.</span><span class="sxs-lookup"><span data-stu-id="643eb-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="643eb-142">Určení parametrů SqlParameters</span><span class="sxs-lookup"><span data-stu-id="643eb-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="643eb-143">Následující <xref:System.Data.SqlClient.SqlParameter> vlastnosti byly rozšířeny pro práci s velkými UDTs.</span><span class="sxs-lookup"><span data-stu-id="643eb-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="643eb-144">Vlastnost SqlParameter</span><span class="sxs-lookup"><span data-stu-id="643eb-144">SqlParameter Property</span></span>|<span data-ttu-id="643eb-145">Popis</span><span class="sxs-lookup"><span data-stu-id="643eb-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="643eb-146">Získá nebo nastaví objekt, který představuje hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="643eb-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="643eb-147">Výchozí hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="643eb-147">The default is null.</span></span> <span data-ttu-id="643eb-148">Vlastnost může `SqlBinary`být `Byte[]`, nebo spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="643eb-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="643eb-149">Získá nebo nastaví objekt, který představuje hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="643eb-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="643eb-150">Výchozí hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="643eb-150">The default is null.</span></span> <span data-ttu-id="643eb-151">Vlastnost může `SqlBinary`být `Byte[]`, nebo spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="643eb-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="643eb-152">Získá nebo nastaví velikost hodnoty parametru přeložit.</span><span class="sxs-lookup"><span data-stu-id="643eb-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="643eb-153">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="643eb-153">The default value is 0.</span></span> <span data-ttu-id="643eb-154">Vlastnost může být celé číslo, které představuje velikost hodnoty parametru.</span><span class="sxs-lookup"><span data-stu-id="643eb-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="643eb-155">Pro velké UDTs může být skutečná velikost UDT nebo -1 pro neznámé.</span><span class="sxs-lookup"><span data-stu-id="643eb-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="643eb-156">Příklad načítání dat</span><span class="sxs-lookup"><span data-stu-id="643eb-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="643eb-157">Následující fragment kódu ukazuje, jak načíst velká data UDT.</span><span class="sxs-lookup"><span data-stu-id="643eb-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="643eb-158">Proměnná `connectionString` předpokládá platné připojení k databázi `commandString` serveru SQL Server a proměnná předpokládá platný příkaz SELECT se sloupcem primárního klíče uvedeným jako první.</span><span class="sxs-lookup"><span data-stu-id="643eb-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="643eb-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="643eb-159">See also</span></span>

- [<span data-ttu-id="643eb-160">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="643eb-160">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="643eb-161">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="643eb-161">Retrieving Database Schema Information</span></span>](../retrieving-database-schema-information.md)
- [<span data-ttu-id="643eb-162">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="643eb-162">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="643eb-163">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="643eb-163">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="643eb-164">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="643eb-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
