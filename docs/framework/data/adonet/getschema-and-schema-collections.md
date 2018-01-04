---
title: "GetSchema a kolekcemi schémat"
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
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d982964b596528b091f5367edd38e0cee5f923c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getschema-and-schema-collections"></a>GetSchema a kolekcemi schémat
**Připojení** třídy v každé z implementace spravovaných zprostředkovatelé rozhraní .NET Framework **GetSchema** metodu, která se používá k načtení schématu informace o databázi, která je aktuálně připojen, a informace o schématu vrácená z **GetSchema** metoda obsahuje ve formě <xref:System.Data.DataTable>. **GetSchema** metoda je přetížené metody, která poskytuje volitelné parametry pro zadání kolekce schémat vrátit a omezení množství vrácených informací.  
  
## <a name="specifying-the-schema-collections"></a>Určení kolekcemi schémat  
 První volitelný parametr **GetSchema** metoda je název kolekce, který je zadán jako řetězec. Existují dva typy kolekcí schémat: běžné kolekcemi schémat, které jsou společné pro všechny poskytovatele a konkrétní schéma kolekce, které jsou specifické pro každého zprostředkovatele.  
  
 Můžete zadat dotaz rozhraní .NET Framework spravovaného zprostředkovatele určit seznam podporovaných schématu kolekcí voláním **GetSchema** metoda bez argumentů nebo názvem schématu kolekce "MetaDataCollections". Tato možnost vrátí <xref:System.Data.DataTable> seznam podporovaných schéma kolekce, počet omezení, které každý podporují a počet identifikátor částí, které používají.  
  
### <a name="retrieving-schema-collections-example"></a>Načítání schématu kolekce příklad  
 Následující příklady ukazují, jak používat <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metoda zprostředkovatele dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> třída načíst informace o schématu o všechny tabulky obsažené v **AdventureWorks**ukázkové databáze:  
  
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
 [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
