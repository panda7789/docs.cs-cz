---
title: Omezení schématu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: d0250e573dc24bfcad97a2f2606cb2e6c8e520da
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782756"
---
# <a name="schema-restrictions"></a>Omezení schématu
Druhý volitelný parametr metody **GetSchema** je omezení, která slouží k omezení množství vrácených informací o schématu a je předána metodě **GetSchema** jako poli řetězců. Pozice v poli určuje hodnoty, které lze předat, a to je ekvivalentní k číslu omezení.  
  
 Například následující tabulka popisuje omezení podporovaná kolekcí schémat "Tables" pomocí Zprostředkovatel dat .NET Framework pro SQL Server. Další omezení pro kolekce schémat SQL Server jsou uvedena na konci tohoto tématu.  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Určení hodnot omezení  
 Chcete-li použít jedno z omezení kolekce schématu "Tables", jednoduše vytvořte pole řetězců se čtyřmi prvky a potom umístěte hodnotu do prvku, který odpovídá číslu omezení. Chcete-li například omezit tabulky vrácené metodou **GetSchema** pouze na tabulky ve schématu "Sales", nastavte druhý prvek pole na "Sales", než jej předáte metodě **GetSchema** .  
  
> [!NOTE]
> Kolekce omezení pro `SqlClient` a `OracleClient` mají další `ParameterName` sloupec. Výchozí sloupec omezení je stále pro zpětnou kompatibilitu, ale v současné době se ignoruje. Parametrizované dotazy místo nahrazení řetězců by měly být použity k minimalizaci rizika útoku prostřednictvím injektáže SQL při zadávání hodnot omezení.  
  
> [!NOTE]
> Počet elementů v poli musí být menší nebo roven počtu omezení podporovaných pro zadanou kolekci schémat, jinak <xref:System.ArgumentException> bude vyvolána výjimka. Může jich být méně, než je maximální počet omezení. U chybějících omezení se předpokládá, že mají hodnotu null (neomezeno).  
  
 Můžete zadat dotaz na .NET Framework spravovaného poskytovatele a určit seznam podporovaných omezení voláním metody **GetSchema** s názvem kolekce schématu omezení, což je "omezení". Tato akce vrátí <xref:System.Data.DataTable> seznam názvů kolekcí, názvy omezení, výchozí hodnoty omezení a čísla omezení.  
  
### <a name="example"></a>Příklad  
 Následující příklady ukazují, jak použít <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metodu .NET Framework Zprostředkovatel dat pro třídu SQL Server <xref:System.Data.SqlClient.SqlConnection> k načtení informací o schématu o všech tabulkách obsažených v ukázkové databázi **AdventureWorks** , a omezení vrácených informací pouze do tabulek ve schématu prodej:  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a>SQL Server omezení schématu  
 V následujících tabulkách jsou uvedeny omezení pro SQL Server kolekcí schémat.  
  
### <a name="users"></a>Uživatelé  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Uživatelské jméno|@Name|name|1|  
  
### <a name="databases"></a>Databáze  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Name|@Name|Name|1|  
  
### <a name="tables"></a>Tabulky  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>Sloupce  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Zobrazení  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|VIEW_CATALOG|1|  
|Owner|@Owner|VIEW_SCHEMA|2|  
|Tabulka|@Table|VIEW_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|SPECIFIC_CATALOG|1|  
|Owner|@Owner|SPECIFIC_SCHEMA|2|  
|Name|@Name|SPECIFIC_NAME|3|  
|Parametr|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>Procedury  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|SPECIFIC_CATALOG|1|  
|Owner|@Owner|SPECIFIC_SCHEMA|2|  
|Name|@Name|SPECIFIC_NAME|3|  
|type|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1|  
|Owner|@Owner|user_name()|2|  
|Tabulka|@Table|o.name|3|  
|Omezení|@ConstraintName|x.name|4|  
|Sloupec|@Column|c.name|5|  
  
### <a name="indexes"></a>Indexy  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1|  
|Owner|@Owner|user_name()|2|  
|Tabulka|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|types.assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|CONSTRAINT_CATALOG|1|  
|Owner|@Owner|CONSTRAINT_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
|Name|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>SQL Server 2008 Schema Restrictions  
 V následujících tabulkách jsou uvedeny omezení pro kolekce schémat SQL Server 2008. Tato omezení platí od verze 3,5 SP1 .NET Framework a SQL Server 2008. Nejsou podporované v dřívějších verzích .NET Framework a SQL Server.  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](ado-net-overview.md)
