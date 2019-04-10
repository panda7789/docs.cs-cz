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
# <a name="large-udts"></a>Velké uživatelsky definované typy
Uživatelem definované typy (UDT) umožňují vývojářům rozšířit systém skalárního typu na server uložením common language runtime (CLR) objekty v databázi serveru SQL Server. Uživatelsky definovaný typ může obsahovat několik elementů a může mít chování, na rozdíl od tradičních alias datové typy, které se skládají z jednoho typ dat systému SQL Server.  
  
> [!NOTE]
>  Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) abyste mohli využívat rozšířenou podporu SqlClient pro velké uživatelsky definované typy.  
  
 Dříve byly omezené na maximální velikosti 8 kb uživatelsky definované typy. V systému SQL Server 2008, byla odebrána toto omezení pro uživatelsky definované typy, které mají formát <xref:Microsoft.SqlServer.Server.Format.UserDefined>.  
  
 Úplnou dokumentaci pro typy definované uživatelem najdete v článku verze SQL Server Books Online pro verzi SQL serveru, který používáte.  
  
 **SQL Server Books Online**  
  
1. [Uživatelem definované typy CLR](https://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Načítání schémat UDT pomocí GetSchema  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Metoda <xref:System.Data.SqlClient.SqlConnection> vrátí informace o schématu v databázi <xref:System.Data.DataTable>. Další informace najdete v tématu [kolekce schémat SQL serveru](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>Hodnoty sloupců GetSchemaTable pro uživatelsky definovaný typ  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Metodu <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.DataTable> popisující sloupce metadat. Následující tabulka popisuje rozdíly mezi metadata sloupce pro velké uživatelsky definované typy mezi systémem SQL Server 2005 a SQL Server 2008.  
  
|SqlDataReader sloupec|SQL Server 2005|SQL Server 2008 nebo novější|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Se liší|Se liší|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|UDT instance|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|UDT instance|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Tři části názvu určenému jako *Database.SchemaName.TypeName*.|  
|`IsLong`|Se liší|Se liší|  
  
## <a name="sqldatareader-considerations"></a>SqlDataReader Considerations  
 <xref:System.Data.SqlClient.SqlDataReader> Se prodloužila, od SQL Server 2008 pro podporu načítání velkých hodnot UDT. Jak velké hodnoty UDT jsou zpracovány <xref:System.Data.SqlClient.SqlDataReader> závisí na verzi systému SQL Server používáte, stejně jako na `Type System Version` zadaná v připojovacím řetězci. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Tyto metody <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.SqlTypes.SqlBinary> místo UDT při `Type System Version` je nastavena na SQL Server 2005:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Následující metody vrátí pole `Byte[]` místo UDT při `Type System Version` je nastavena na SQL Server 2005:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Všimněte si, že žádné převody jsou provedeny pro aktuální verzi ADO.NET.  
  
## <a name="specifying-sqlparameters"></a>Určení SqlParameters  
 Následující <xref:System.Data.SqlClient.SqlParameter> vlastnosti se rozšířily a pracovat s velké uživatelsky definované typy.  
  
|Vlastnost SqlParameter|Popis|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Získá nebo nastaví objekt, který představuje hodnotu parametru. Výchozí hodnota je null. Vlastnost může být `SqlBinary`, `Byte[]`, nebo spravovaný objekt.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Získá nebo nastaví objekt, který představuje hodnotu parametru. Výchozí hodnota je null. Vlastnost může být `SqlBinary`, `Byte[]`, nebo spravovaný objekt.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Získá nebo nastaví velikost hodnotu parametru vyřešit. Výchozí hodnota je 0. Vlastnost může být celé číslo, které představuje velikost hodnotu parametru. Pro velké uživatelsky definované typy může být skutečná velikost UDT nebo -1 pro neznámý.|  
  
## <a name="retrieving-data-example"></a>Příklad načítání dat  
 Následující fragment kódu ukazuje, jak načíst velkých objemů dat UDT. `connectionString` Proměnné předpokládá platné připojení k databázi SQL serveru a `commandString` proměnné předpokládá platným příkazem SELECT s sloupec primárního klíče uvedená jako první.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Konfigurace parametrů a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Načítání informací o databázovém schématu](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [Mapování datových typů SQL Serveru](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [Binární a vysoké hodnoty na SQL Serveru](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
