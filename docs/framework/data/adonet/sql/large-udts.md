---
title: Velké uživatelsky definované typy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 012bddc0b4c29a0b50abc3a0df5c3cd34dc4725a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452393"
---
# <a name="large-udts"></a>Velké uživatelsky definované typy
Uživatelsky definované typy (UDT) umožňují vývojářům, aby rozšířili systém skalárního typu serveru tím, že ukládá objekty modulu CLR (Common Language Runtime) do databáze SQL Server. UDT může obsahovat více prvků a může mít chování, na rozdíl od tradičních datových typů aliasů, které se skládají z jednoho SQL Server systémových dat.  
  
> [!NOTE]
> Abyste mohli využívat vylepšenou podporu SqlClient pro velké UDT, musíte nainstalovat .NET Framework 3,5 SP1 (nebo novější).  
  
 Dříve se UDT omezila na maximální velikost 8 kilobajtů. V SQL Server 2008 bylo toto omezení odstraněno pro UDT, které mají formát <xref:Microsoft.SqlServer.Server.Format.UserDefined>.  
  
 Úplnou dokumentaci pro uživatelsky definované typy najdete v tématu verze SQL Server Knihy online pro verzi SQL Server, kterou používáte.  
  
 **Dokumentace SQL Serveru**  
  
1. [Uživatelem definované typy CLR](/sql/relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Načítání schémat UDT pomocí GetSchema  
 Metoda <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> <xref:System.Data.SqlClient.SqlConnection> vrací informace o schématu databáze v <xref:System.Data.DataTable>. Další informace najdete v tématu [SQL Server kolekcí schémat](../sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>Hodnoty sloupce GetSchema pro UDT  
 Metoda <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> <xref:System.Data.SqlClient.SqlDataReader> vrací <xref:System.Data.DataTable>, která popisuje metadata sloupce. Následující tabulka popisuje rozdíly v metadatech sloupců pro velké UDT mezi SQL Server 2005 a SQL Server 2008.  
  
|Sloupec SqlDataReader|SQL Server 2005|SQL Server 2008 a novější|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Různé|Různé|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|Instance UDT|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|Instance UDT|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Název tři části zadaný jako *Database. Schema. TypeName*.|  
|`IsLong`|Různé|Různé|  
  
## <a name="sqldatareader-considerations"></a>SqlDataReader Considerations  
 <xref:System.Data.SqlClient.SqlDataReader> bylo rozšířeno od SQL Server 2008 až po podporu načítání velkých hodnot UDT. Způsob zpracování velkých hodnot UDT pomocí <xref:System.Data.SqlClient.SqlDataReader> závisí na verzi SQL Server, kterou používáte, a na `Type System Version` určeném v připojovacím řetězci. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Následující metody <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.SqlTypes.SqlBinary> namísto UDT, pokud je `Type System Version` nastaveno na SQL Server 2005:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Následující metody vrátí pole `Byte[]` místo typu UDT, pokud je `Type System Version` nastaveno na SQL Server 2005:  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Všimněte si, že pro aktuální verzi ADO.NET nejsou provedeny žádné převody.  
  
## <a name="specifying-sqlparameters"></a>Určení SqlParameters  
 Následující <xref:System.Data.SqlClient.SqlParameter> vlastnosti byly rozšířeny, aby fungovaly s velkými Udty.  
  
|Vlastnost SqlParameter|Popis|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Získá nebo nastaví objekt, který představuje hodnotu parametru. Výchozí hodnota je null. Vlastnost může být `SqlBinary`, `Byte[]`nebo spravovaný objekt.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Získá nebo nastaví objekt, který představuje hodnotu parametru. Výchozí hodnota je null. Vlastnost může být `SqlBinary`, `Byte[]`nebo spravovaný objekt.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Získá nebo nastaví velikost hodnoty parametru, která se má vyřešit. Výchozí hodnota je 0. Vlastnost může být celé číslo, které představuje velikost hodnoty parametru. U velkých UDT může být skutečná velikost UDT nebo-1 pro neznámý.|  
  
## <a name="retrieving-data-example"></a>Příklad načítání dat  
 Následující fragment kódu ukazuje, jak načíst velká data UDT. Proměnná `connectionString` předpokládá platné připojení k databázi SQL Server a proměnná `commandString` předpokládá platný příkaz SELECT se sloupcem primárního klíče uvedeným jako první.  
  
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
