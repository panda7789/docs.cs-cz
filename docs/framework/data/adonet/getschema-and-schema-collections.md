---
title: Příkaz GetSchema a kolekce schémat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: 4ac0216ce2965d555f7283ba66a085ea9d7cac3c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783839"
---
# <a name="getschema-and-schema-collections"></a>Příkaz GetSchema a kolekce schémat
Třídy **připojení** v každém z .NET Framework spravovaných zprostředkovatelé implementují metodu **GetSchema** , která se používá k načtení informací o schématu o databázi, která je aktuálně připojená, a informace o schématu vrácené z  **Metoda GetSchema** je dodávána ve formě <xref:System.Data.DataTable>. Metoda **GetSchema** je přetížená metoda, která poskytuje volitelné parametry pro určení kolekce schématu, která se má vrátit, a omezení množství vrácených informací.  
  
## <a name="specifying-the-schema-collections"></a>Určení kolekcí schémat  
 Prvním volitelným parametrem metody **GetSchema** je název kolekce, který je určen jako řetězec. Existují dva typy kolekcí schémat: společné kolekce schémat, které jsou společné pro všechny poskytovatele, a konkrétní kolekce schémat, které jsou specifické pro každého poskytovatele.  
  
 Můžete zadat dotaz na .NET Framework spravovaného poskytovatele a určit seznam podporovaných kolekcí schémat voláním metody **GetSchema** bez argumentů nebo s názvem kolekce schématu "MetaDataCollections". Tato akce vrátí <xref:System.Data.DataTable> seznam podporovaných kolekcí schémat, počet omezení, která jednotlivé požadavky podporují, a počet částí identifikátorů, které používají.  
  
### <a name="retrieving-schema-collections-example"></a>Příklad načítání kolekcí schémat  
 Následující příklady ukazují, jak použít <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metodu .NET Framework Zprostředkovatel dat pro třídu SQL Server <xref:System.Data.SqlClient.SqlConnection> k načtení informací o schématu o všech tabulkách obsažených v ukázkové databázi **AdventureWorks** :  
  
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
  
## <a name="see-also"></a>Viz také:

- [Načítání informací o databázovém schématu](retrieving-database-schema-information.md)
- [Přehled ADO.NET](ado-net-overview.md)
