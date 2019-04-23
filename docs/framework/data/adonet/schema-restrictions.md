---
title: Omezení schématu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: b5044d39d1dc5d2fa7d2ce691cdda7075fa0e32a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151200"
---
# <a name="schema-restrictions"></a>Omezení schématu
Druhý volitelný parametr **GetSchema** metoda je vrácena omezení, které se používají a omezit tak množství informací o schématu, a je předán **GetSchema** metody jako pole řetězců . Pozice v poli určuje hodnoty, které můžete předat, a to je ekvivalentní hodnotě parametru omezení.  
  
 Například následující tabulka popisuje omezení kolekcí schémat "Tabulky" pomocí zprostředkovatele dat .NET Framework pro SQL Server podporován. Další omezení kolekce schémat SQL Server jsou uvedeny na konci tohoto tématu.  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|TABLE_CATALOG|1|  
|Owner|@Owner|TABLE_SCHEMA|2|  
|Tabulka|@Name|TABLE_NAME|3|  
|TableType|@TableType|TABLE_TYPE|4|  
  
## <a name="specifying-restriction-values"></a>Určení hodnoty omezení  
 Použijte jednu z těchto omezení kolekce schémat "Tabulky", jednoduše vytvořit pole řetězců, které se čtyřmi prvky a potom umístili hodnotu v elementu, který se shoduje s počtem omezení. Například k omezení tabulky vrácené **GetSchema** metodu pouze tabulky ve schématu "Prodeje" nastavit druhý prvek pole, které chcete "Prodeje" před předáním do **GetSchema** metody.  
  
> [!NOTE]
>  Omezení kolekce pro `SqlClient` a `OracleClient` mají další `ParameterName` sloupce. Výchozí sloupec omezení je stále pro zpětnou kompatibilitu, ale aktuálně je ignorována. Chcete-li minimalizovat riziko útoků prostřednictvím injektáže SQL, při zadávání hodnoty omezení by měla sloužit parametrizovaných dotazů místo nahrazení řetězce.  
  
> [!NOTE]
>  Počet prvků v poli musí být menší nebo rovna počtu omezení pro ostatní zadané schéma kolekce nepodporuje <xref:System.ArgumentException> bude vyvolána výjimka. Může být méně než maximální počet omezení. Chybí omezení jsou považován za hodnotu null (bez omezení).  
  
 Můžete dát dotaz na zprostředkovatele rozhraní .NET Framework spravované k určení seznamu podporovaných omezení voláním **GetSchema** metodu s názvem kolekce schémat omezení, což je "Omezení". Vrátí <xref:System.Data.DataTable> seznam názvy kolekcí, omezení názvů, omezení výchozí hodnoty a omezení čísla.  
  
### <a name="example"></a>Příklad  
 Následující příklady ukazují, jak používat <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metoda zprostředkovatele dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> třídy pro načtení schématu informace o všech tabulek, které jsou součástí **AdventureWorks**ukázková databáze a omezit informace vrátí pouze ty tabulky ve schématu "Prodeje":  
  
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
  
## <a name="sql-server-schema-restrictions"></a>Omezení schématu SQL serveru  
 Omezení pro kolekce schémat SQL Server naleznete v následujících tabulkách.  
  
### <a name="users"></a>Uživatelé  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Uživatelské_jméno|@Name|name|1|  
  
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
|Type|@Type|ROUTINE_TYPE|4|  
  
### <a name="indexcolumns"></a>IndexColumns  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1|  
|Owner|@Owner|user_name()|2|  
|Tabulka|@Table|o.Name|3|  
|ConstraintName|@ConstraintName|x.Name|4|  
|Sloupec|@Column|c.Name|5|  
  
### <a name="indexes"></a>Indexy  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|db_name()|1|  
|Owner|@Owner|user_name()|2|  
|Tabulka|@Table|o.Name|3|  
  
### <a name="userdefinedtypes"></a>UserDefinedTypes  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|název_sestavení|@AssemblyName|assemblies.name|1|  
|udt_name|@UDTName|types.assembly_class|2|  
  
### <a name="foreignkeys"></a>ForeignKeys  
  
|Název omezení|Název parametru|Výchozí omezení|Číslo omezení|  
|----------------------|--------------------|-------------------------|------------------------|  
|Katalog|@Catalog|CONSTRAINT_CATALOG|1|  
|Owner|@Owner|CONSTRAINT_SCHEMA|2|  
|Tabulka|@Table|TABLE_NAME|3|  
|Name|@Name|CONSTRAINT_NAME|4|  
  
## <a name="sql-server-2008-schema-restrictions"></a>SQL Server 2008 Schema Restrictions  
 Omezení pro kolekce schémat SQL Server 2008 naleznete v následujících tabulkách. Tato omezení jsou platné od verze SQL Server 2008 a rozhraní .NET Framework 3.5 SP1. Nejsou podporovány v dřívějších verzích rozhraní .NET Framework a systému SQL Server.  
  
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

- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
