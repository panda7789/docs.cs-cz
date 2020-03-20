---
title: Omezení schématu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 17c42c5131252993d1f16e4a2f7a6450f0984d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149008"
---
# <a name="schema-restrictions"></a>Omezení schématu
Druhý volitelný parametr **Metody GetSchema** je omezení, které se používají k omezení množství informací o schématu vrácena a je předán **a GetSchema** metoda jako pole řetězců. Pozice v poli určuje hodnoty, které můžete předat, a to je ekvivalentní číslo omezení.  
  
 V následující tabulce jsou například popsána omezení podporovaná kolekcí schématu Tabulky pomocí zprostředkovatele dat rozhraní .NET Framework pro SQL Server. Další omezení pro kolekce schématu sql serveru jsou uvedeny na konci tohoto tématu.  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Table|@Name|TABLE_NAME|3|  
|Typ tabulky|@TableType|Table_type|4|  
  
## <a name="specifying-restriction-values"></a>Určení hodnot omezení  
 Chcete-li použít jedno z omezení kolekce schématu "Tabulky", jednoduše vytvořte pole řetězců se čtyřmi prvky a umístěte hodnotu do prvku, který odpovídá číslu omezení. Chcete-li například omezit tabulky vrácené metodou **GetSchema** pouze na ty tabulky ve schématu "Prodej", nastavte druhý prvek pole na "Prodej" před jeho předáním metodě **GetSchema.**  
  
> [!NOTE]
> Kolekce omezení pro `SqlClient` `OracleClient` a mají `ParameterName` další sloupec. Výchozí sloupec omezení je stále k dispozici pro zpětnou kompatibilitu, ale je aktuálně ignorován. Parametrizované dotazy spíše než nahrazení řetězce by měly být použity k minimalizaci rizika útoku injektáže SQL při zadávání hodnot omezení.  
  
> [!NOTE]
> Počet prvků v poli musí být menší nebo rovno počtu omezení podporovaných pro zadanou kolekci schématu, jinak <xref:System.ArgumentException> bude vyvolána. Může být menší než maximální počet omezení. Chybějící omezení jsou považovány za null (bez omezení).  
  
 Můžete dotaz zprostředkovatele spravovaného rozhraní .NET Framework určit seznam podporovaných omezení voláním **GetSchema** metoda s názvem kolekce schématu omezení, což je "Omezení". Tím se <xref:System.Data.DataTable> vrátí seznam názvů kolekcí, názvy omezení, výchozí hodnoty omezení a čísla omezení.  
  
### <a name="example"></a>Příklad  
 Následující příklady ukazují, jak <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> použít metodu zprostředkovatele dat rozhraní <xref:System.Data.SqlClient.SqlConnection> .NET Framework pro třídu SQL Server k načtení informací o schématu o všech tabulkách obsažených v ukázkové databázi **AdventureWorks** a omezit informace vrácené pouze do těchto tabulek ve schématu Prodej:  
  
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
  
## <a name="sql-server-schema-restrictions"></a>Omezení schématu serveru SQL Server  
 V následujících tabulkách jsou uvedena omezení pro kolekce schématu serveru SQL Server.  
  
### <a name="users"></a>Uživatelé  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|User_name|@Name|jméno|1|  
  
### <a name="databases"></a>Databáze  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Name (Název)|@Name|Name (Název)|1|  
  
### <a name="tables"></a>Tabulky  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Table|@Name|TABLE_NAME|3|  
|Typ tabulky|@TableType|Table_type|4|  
  
### <a name="columns"></a>Sloupce  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
### <a name="structuredtypemembers"></a>Členové structuredTypeMembers  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
### <a name="views"></a>Zobrazení  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
  
### <a name="viewcolumns"></a>Zobrazit sloupce  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|VIEW_CATALOG|1|  
|Vlastník|@Owner|VIEW_SCHEMA|2|  
|Table|@Table|VIEW_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
### <a name="procedureparameters"></a>Parametry procedury  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|SPECIFIC_CATALOG|1|  
|Vlastník|@Owner|SPECIFIC_SCHEMA|2|  
|Name (Název)|@Name|SPECIFIC_NAME|3|  
|Parametr|@Parameter|PARAMETER_NAME|4|  
  
### <a name="procedures"></a>Procedury  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|SPECIFIC_CATALOG|1|  
|Vlastník|@Owner|SPECIFIC_SCHEMA|2|  
|Name (Název)|@Name|SPECIFIC_NAME|3|  
|Typ|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexSloupce  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1|  
|Vlastník|@Owner|user_name()|2|  
|Table|@Table|o.name|3|  
|Název_omezení|@ConstraintName|x.name|4|  
|Sloupec|@Column|c.name|5|  
  
### <a name="indexes"></a>Indexy  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1|  
|Vlastník|@Owner|user_name()|2|  
|Table|@Table|o.name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|assembly_name|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|types.assembly_class|2|  
  
### <a name="foreignkeys"></a>Cizí klíče  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|CONSTRAINT_CATALOG|1|  
|Vlastník|@Owner|CONSTRAINT_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|Name (Název)|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>Omezení schématu serveru SQL Server 2008  
 V následujících tabulkách jsou uvedena omezení pro kolekce schématu serveru SQL Server 2008. Tato omezení jsou platná počínaje verzí 3.5 SP1 rozhraní .NET Framework a SQL Server 2008. Nejsou podporovány v dřívějších verzích rozhraní .NET Framework a SQL Server.  
  
### <a name="columnsetcolumns"></a>ColumnSetColumns  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
  
### <a name="allcolumns"></a>Všechny sloupce  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Vlastník|@Owner|TABLE_SCHEMA|2|  
|Table|@Table|TABLE_NAME|3|  
|Sloupec|@Column|COLUMN_NAME|4|  
  
## <a name="see-also"></a>Viz také

- [Přehled ADO.NET](ado-net-overview.md)
