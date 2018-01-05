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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 876ebeb5568ffff0a10aa5a54ce96c256d237d86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="large-udts"></a>Velké UDT
Uživatelem definované typy (UDT) umožňují vývojář rozšíření systému skalárního typu serveru uložením běžně používané objekty language runtime (CLR) v databázi systému SQL Server. UDT může obsahovat více elementů a může mít chování, na rozdíl od tradičních alias datové typy, které se skládají z jedné typ dat systému SQL Server.  
  
> [!NOTE]
>  Musíte nainstalovat rozhraní .NET Framework 3.5 SP1 (nebo novější) využívat rozšířenou podporu SqlClient pro velké UDT.  
  
 Dříve byly UDT omezen na maximální velikost 8 kB. V systému SQL Server 2008, byla odebrána toto omezení pro UDT, které mají do formátu podle <xref:Microsoft.SqlServer.Server.Format.UserDefined>.  
  
 Kompletní dokumentaci pro uživatelem definované typy najdete v tématu verze SQL Server Books Online pro verzi systému SQL Server, kterou používáte.  
  
 **SQL Server Books Online**  
  
1.  [Uživatelem definované typy CLR](http://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Načítání schémat UDT pomocí GetSchema  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Metodu <xref:System.Data.SqlClient.SqlConnection> vrátí informace o schématu v databázi <xref:System.Data.DataTable>. Další informace najdete v tématu [kolekcemi schémat SQL serveru](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).  
  
### <a name="getschematable-column-values-for-udts"></a>Hodnoty ve sloupcích GetSchemaTable pro uživatelsky definovaný typ  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> Metodu <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.DataTable> metadata sloupce, který popisuje. Následující tabulka popisuje rozdíly v metadata sloupce pro velké UDT mezi systému SQL Server 2005 a SQL Server 2008.  
  
|Sloupec SqlDataReader|SQL Server 2005|SQL Server 2008 a novější|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Je to různé.|Je to různé.|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|UDT instance|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|UDT instance|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Název zadaný jako část tří *Database.SchemaName.TypeName*.|  
|`IsLong`|Je to různé.|Je to různé.|  
  
## <a name="sqldatareader-considerations"></a>Aspekty SqlDataReader  
 <xref:System.Data.SqlClient.SqlDataReader> Bylo rozšířeno od verze systému SQL Server 2008 pro podporu načítání velkých UDT hodnot. Jak se zpracovávají velké hodnoty UDT <xref:System.Data.SqlClient.SqlDataReader> závisí na verzi systému SQL Server, kterou používáte, stejně jako na `Type System Version` zadaný v připojovacím řetězci. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
 Tyto metody <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.SqlTypes.SqlBinary> místo UDT při `Type System Version` je nastavena na systém SQL Server 2005:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 Následující metody vrátí pole `Byte[]` místo UDT při `Type System Version` je nastavena na systém SQL Server 2005:  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 Všimněte si, že žádné převody jsou vytvářeny pro aktuální verzi ADO.NET.  
  
## <a name="specifying-sqlparameters"></a>Zadání SqlParameters  
 Následující <xref:System.Data.SqlClient.SqlParameter> vlastnosti se rozšířily a pracovat s velké UDT.  
  
|Vlastnost SqlParameter|Popis|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|Získá nebo nastaví objekt, který představuje hodnotu parametru. Výchozí hodnota je null. Vlastnost, která může být `SqlBinary`, `Byte[]`, nebo spravovaného objektu.|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|Získá nebo nastaví objekt, který představuje hodnotu parametru. Výchozí hodnota je null. Vlastnost, která může být `SqlBinary`, `Byte[]`, nebo spravovaného objektu.|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|Získá nebo nastaví velikost hodnoty parametru vyřešit. Výchozí hodnota je 0. Vlastnost může být celé číslo, které představuje velikost hodnotu parametru. Pro velké UDT může být skutečná velikost UDT nebo -1 pro neznámý.|  
  
## <a name="retrieving-data-example"></a>Příklad načítání dat  
 Následující fragment kódu ukazuje, jak načíst velkých objemů dat UDT. `connectionString` Proměnná předpokládá máte platné připojení k databázi systému SQL Server a `commandString` proměnná předpokládá platný příkaz SELECT s sloupec primárního klíče uvedená jako první.  
  
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
 [Konfigurace parametrů a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Načítání informací o databázovém schématu](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [Mapování datových typů SQL Serveru](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Binární a vysoké hodnoty na SQL Serveru](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
