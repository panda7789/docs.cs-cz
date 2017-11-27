---
title: "Omezení schématu"
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
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c254865800694af8eb754c3e8d4072688fd7e89a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="schema-restrictions"></a>Omezení schématu
Druhý parametr volitelný **GetSchema** je metoda vrátí omezení, které se používají k omezení množství informací o schématu, a je předán **GetSchema** metoda jako pole řetězců. . Určuje pozici v poli hodnoty, které můžete předat a jde o ekvivalent číslo omezení.  
  
 Například následující tabulka popisuje omezení kolekcí schémat "Tabulky" pomocí zprostředkovatele dat .NET Framework pro SQL Server podporován. Další omezení pro kolekce schématu systému SQL Server je uvedený na konci tohoto tématu.  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Zadání hodnoty omezení  
 Použít jednu z omezení kolekce schémat "Tabulky", stačí vytvořit pole řetězců se čtyřmi prvky a pak umístit hodnotu elementu, který odpovídá číslu omezení. Například k omezení tabulky vrácený **GetSchema** metodu pouze ty tabulky ve schématu "Prodej", nastavte druhý prvkem pole na "Prodej" před předáním na **GetSchema** metoda.  
  
> [!NOTE]
>  Omezení kolekce pro `SqlClient` a `OracleClient` mají další `ParameterName` sloupce. Výchozí sloupec omezení je stále existuje pro zpětnou kompatibilitu, ale je aktuálně ignorována. Parametrizované dotazy a nikoli náhradní řetězce se má použít k minimalizovat riziko útoku vkládání SQL při zadání hodnoty omezení.  
  
> [!NOTE]
>  Počet prvků v poli musí být menší než nebo rovna počtu omezení, která jsou podporována pro jiný určené schéma kolekce <xref:System.ArgumentException> bude vyvolána. Může být menší než maximální počet omezení. Chybějící omezení se předpokládá, že mít hodnotu null (bez omezení).  
  
 Můžete zadat dotaz rozhraní .NET Framework spravovaného zprostředkovatele určit seznam podporovaných omezení voláním **GetSchema** metoda s názvem kolekce schémat omezení, což je "Omezení". Tato možnost vrátí <xref:System.Data.DataTable> se seznamem názvů kolekcí, názvy omezení, výchozí hodnoty omezení a omezení čísla.  
  
### <a name="example"></a>Příklad  
 Následující příklady ukazují, jak používat <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metoda zprostředkovatele dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> třída načíst informace o schématu o všechny tabulky obsažené v **AdventureWorks**ukázkové databáze, a omezit informace vrátí pouze ty tabulky "Prodeje" schématu:  
  
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
  
## <a name="sql-server-schema-restrictions"></a>SQL Server schématu omezení  
 V následujících tabulkách najdete omezení pro kolekce schématu systému SQL Server.  
  
### <a name="users"></a>Uživatelé  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Uživatelské_jméno|@Name|name|1|  
  
### <a name="databases"></a>Databáze  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Název|@Name|Název|1|  
  
### <a name="tables"></a>Tabulky  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
### <a name="columns"></a>Sloupce  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>StructuredTypeMembers  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>zobrazení  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>ViewColumns  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|VIEW_CATALOG|1|  
|Vlastník|@Owner|VIEW_SCHEMA|2|  
|Tabulka|@Table|VIEW_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>ProcedureParameters  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|SPECIFIC_CATALOG|1|  
|Vlastník|@Owner|SPECIFIC_SCHEMA|2|  
|Název|@Name|SPECIFIC_NAME|3|  
|Parametr|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>Procedury  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|SPECIFIC_CATALOG|1|  
|Vlastník|@Owner|SPECIFIC_SCHEMA|2|  
|Název|@Name|SPECIFIC_NAME|3|  
|Typ|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|db_name()|1|  
|Vlastník|@Owner|user_name()|2|  
|Tabulka|@Table|o.Name|3|  
|ConstraintName|@ConstraintName|x.Name|4|  
|Sloupec|@Column|c.Name|5|  
  
### <a name="indexes"></a>Indexy  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|db_name()|1|  
|Vlastník|@Owner|user_name()|2|  
|Tabulka|@Table|o.Name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|Assemblies.Name|1|  
|udt_name|@UDTName|Types.assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|CONSTRAINT_CATALOG|1|  
|Vlastník|@Owner|CONSTRAINT_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
|Název|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>SQL Server 2008 schématu omezení  
 V následujících tabulkách najdete omezení pro SQL Server 2008 kolekcemi schémat. Tato omezení jsou platné od verze verze systému SQL Server 2008 a rozhraní .NET Framework 3.5 SP1. Nejsou podporovány v dřívějších verzích rozhraní .NET Framework a SQL Server.  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>AllColumns  
  
|Název omezení|Název parametru|Výchozí omezení|Počet omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalogu|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
