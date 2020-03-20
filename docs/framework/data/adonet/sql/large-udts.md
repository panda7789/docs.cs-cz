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
# <a name="large-udts"></a>Velké uživatelsky definované typy
Uživatelem definované typy (UDT) umožňují vývojáři rozšířit systém skalárního typu serveru uložením objektů CLR (COMMON Language runtime) v databázi serveru SQL Server. UDT s může obsahovat více prvků a může mít chování, na rozdíl od tradičních alias datových typů, které se skládají z jednoho datového typu systému SQL Server.  
  
> [!NOTE]
> Chcete-li využít výhod rozšířené podpory rozhraní SqlClient pro velké udts, je nutné nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější).  
  
 Dříve byly udts omezeny na maximální velikost 8 kilobajtů. V sql server 2008 toto omezení byla odebrána pro <xref:Microsoft.SqlServer.Server.Format.UserDefined>UDTs, které mají formát .  
  
 Úplnou dokumentaci pro uživatelem definované typy naleznete ve verzi SQL Server Books Online pro verzi serveru SQL Server, který používáte.  
  
 **Dokumentace SQL Serveru**  
  
1. [Uživatelem definované typy CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Načítání schémat UDT pomocí getschema  
 Metoda <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> vrátí <xref:System.Data.SqlClient.SqlConnection> informace o schématu databáze <xref:System.Data.DataTable>v . Další informace naleznete v tématu [KOLEKCE Schémat serveru SQL Server](../sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>Hodnoty sloupců schematable pro UDT  
 Metoda <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.DataTable> vrátí, který popisuje metadata sloupce. Následující tabulka popisuje rozdíly v metadatech sloupce pro velké UDT mezi SQL Server 2005 a SQL Server 2008.  
  
|Sloupec SqlDataReader|SQL Server 2005|SQL Server 2008 a novější|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Různé|Různé|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|Instance UDT|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|Instance UDT|  
|`ProviderType`|21`SqlDbType.VarBinary`( )|29`SqlDbType.Udt`.|  
|`NonVersionedProviderType`|29`SqlDbType.Udt`.|29`SqlDbType.Udt`.|  
|`DataTypeName`|`SqlDbType.VarBinary`|Název tři části zadaný jako *Database.SchemaName.TypeName*.|  
|`IsLong`|Různé|Různé|  
  
## <a name="sqldatareader-considerations"></a>Důležité informace aplikace SqlDataReader  
 Byl <xref:System.Data.SqlClient.SqlDataReader> rozšířen počínaje SQL Server 2008 pro podporu načítání velkých hodnot UDT. Jak velké hodnoty UDT jsou <xref:System.Data.SqlClient.SqlDataReader> zpracovány a závisí na verzi SQL Server, `Type System Version` který používáte, jakož i na zadané v připojovacím řetězci. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Následující metody <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.SqlTypes.SqlBinary> místo UDT při `Type System Version` je nastavena na SQL Server 2005:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Následující metody vrátí pole `Byte[]` namísto UDT při `Type System Version` je nastavena na SQL Server 2005:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Všimněte si, že pro aktuální verzi ADO.NET nejsou provedeny žádné převody.  
  
## <a name="specifying-sqlparameters"></a>Určení parametrů SqlParameters  
 Následující <xref:System.Data.SqlClient.SqlParameter> vlastnosti byly rozšířeny pro práci s velkými UDTs.  
  
|Vlastnost SqlParameter|Popis|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Získá nebo nastaví objekt, který představuje hodnotu parametru. Výchozí hodnota je null. Vlastnost může `SqlBinary`být `Byte[]`, nebo spravovaný objekt.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Získá nebo nastaví objekt, který představuje hodnotu parametru. Výchozí hodnota je null. Vlastnost může `SqlBinary`být `Byte[]`, nebo spravovaný objekt.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Získá nebo nastaví velikost hodnoty parametru přeložit. Výchozí hodnota je 0. Vlastnost může být celé číslo, které představuje velikost hodnoty parametru. Pro velké UDTs může být skutečná velikost UDT nebo -1 pro neznámé.|  
  
## <a name="retrieving-data-example"></a>Příklad načítání dat  
 Následující fragment kódu ukazuje, jak načíst velká data UDT. Proměnná `connectionString` předpokládá platné připojení k databázi `commandString` serveru SQL Server a proměnná předpokládá platný příkaz SELECT se sloupcem primárního klíče uvedeným jako první.  
  
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
  
## <a name="see-also"></a>Viz také

- [Konfigurace parametrů a datové typy parametrů](../configuring-parameters-and-parameter-data-types.md)
- [Načítání informací o databázovém schématu](../retrieving-database-schema-information.md)
- [Mapování datových typů SQL Serveru](../sql-server-data-type-mappings.md)
- [Binární a vysoké hodnoty na SQL Serveru](sql-server-binary-and-large-value-data.md)
- [Přehled ADO.NET](../ado-net-overview.md)
