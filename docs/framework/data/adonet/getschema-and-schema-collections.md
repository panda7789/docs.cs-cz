---
title: Příkaz GetSchema a kolekce schémat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: e18c23e9bbec97a64110aba6eb7241761ecece06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149554"
---
# <a name="getschema-and-schema-collections"></a>Příkaz GetSchema a kolekce schémat
Třídy **Connection** v každém zprostředkovateli spravované ho rozhraní .NET Framework implementují metodu **GetSchema,** která se používá k načtení informací o schématu o databázi, <xref:System.Data.DataTable>která je aktuálně připojena, a informace o schématu vrácené z metody **GetSchema** jsou dodávány ve formě . **Metoda GetSchema** je přetížená metoda, která poskytuje volitelné parametry pro určení kolekce schématu vrátit a omezení množství vrácených informací.  
  
## <a name="specifying-the-schema-collections"></a>Určení kolekcí schématu  
 První volitelný parametr metody **GetSchema** je název kolekce, který je určen jako řetězec. Existují dva typy kolekcí schématu: společné kolekce schématu, které jsou společné pro všechny zprostředkovatele a konkrétní kolekce schématu, které jsou specifické pro každého zprostředkovatele.  
  
 Můžete dotaz zprostředkovatele spravovaného rozhraní .NET Framework určit seznam podporovaných kolekcí schématu voláním **GetSchema** metoda bez argumentů nebo s názvem kolekce schématu "MetaDataCollections". Tím se <xref:System.Data.DataTable> vrátí seznam podporovaných kolekcí schématu, počet omezení, které podporují, a počet částí identifikátoru, které používají.  
  
### <a name="retrieving-schema-collections-example"></a>Příklad načítání kolekcí schématu  
 Následující příklady ukazují, jak <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> použít metodu zprostředkovatele dat rozhraní <xref:System.Data.SqlClient.SqlConnection> .NET Framework pro třídu SQL Server k načtení informací o schématu o všech tabulkách obsažených v ukázkové databázi **AdventureWorks:**  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
   Sub Main()  
      Dim connectionString As String = GetConnectionString()  
      Using connection As New SqlConnection(connectionString)  
         'Connect to the database then retrieve the schema information.  
         connection.Open()  
         Dim table As DataTable = connection.GetSchema("Tables")  
  
         ' Display the contents of the table.  
         DisplayData(table)  
         Console.WriteLine("Press any key to continue.")  
         Console.ReadKey()  
      End Using  
   End Sub  
  
   Private Function GetConnectionString() As String  
      ' To avoid storing the connection string in your code,
      ' you can retrieve it from a configuration file.  
      Return "Data Source=(local);Database=AdventureWorks;" _  
         & "Integrated Security=true;"  
   End Function  
  
   Private Sub DisplayData(ByVal table As DataTable)  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
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
  string connectionString = GetConnectionString();  
  using (SqlConnection connection = new SqlConnection(connectionString))  
  {  
   // Connect to the database then retrieve the schema information.  
   connection.Open();  
   DataTable table = connection.GetSchema("Tables");  
  
   // Display the contents of the table.  
   DisplayData(table);  
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
  
## <a name="see-also"></a>Viz také

- [Načítání informací o databázovém schématu](retrieving-database-schema-information.md)
- [Přehled ADO.NET](ado-net-overview.md)
