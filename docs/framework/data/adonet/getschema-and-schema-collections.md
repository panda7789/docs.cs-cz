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
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="a37e0-102">Příkaz GetSchema a kolekce schémat</span><span class="sxs-lookup"><span data-stu-id="a37e0-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="a37e0-103">Třídy **Connection** v každém zprostředkovateli spravované ho rozhraní .NET Framework implementují metodu **GetSchema,** která se používá k načtení informací o schématu o databázi, <xref:System.Data.DataTable>která je aktuálně připojena, a informace o schématu vrácené z metody **GetSchema** jsou dodávány ve formě .</span><span class="sxs-lookup"><span data-stu-id="a37e0-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a37e0-104">**Metoda GetSchema** je přetížená metoda, která poskytuje volitelné parametry pro určení kolekce schématu vrátit a omezení množství vrácených informací.</span><span class="sxs-lookup"><span data-stu-id="a37e0-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="a37e0-105">Určení kolekcí schématu</span><span class="sxs-lookup"><span data-stu-id="a37e0-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="a37e0-106">První volitelný parametr metody **GetSchema** je název kolekce, který je určen jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="a37e0-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="a37e0-107">Existují dva typy kolekcí schématu: společné kolekce schématu, které jsou společné pro všechny zprostředkovatele a konkrétní kolekce schématu, které jsou specifické pro každého zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="a37e0-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="a37e0-108">Můžete dotaz zprostředkovatele spravovaného rozhraní .NET Framework určit seznam podporovaných kolekcí schématu voláním **GetSchema** metoda bez argumentů nebo s názvem kolekce schématu "MetaDataCollections".</span><span class="sxs-lookup"><span data-stu-id="a37e0-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="a37e0-109">Tím se <xref:System.Data.DataTable> vrátí seznam podporovaných kolekcí schématu, počet omezení, které podporují, a počet částí identifikátoru, které používají.</span><span class="sxs-lookup"><span data-stu-id="a37e0-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="a37e0-110">Příklad načítání kolekcí schématu</span><span class="sxs-lookup"><span data-stu-id="a37e0-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="a37e0-111">Následující příklady ukazují, jak <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> použít metodu zprostředkovatele dat rozhraní <xref:System.Data.SqlClient.SqlConnection> .NET Framework pro třídu SQL Server k načtení informací o schématu o všech tabulkách obsažených v ukázkové databázi **AdventureWorks:**</span><span class="sxs-lookup"><span data-stu-id="a37e0-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a37e0-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a37e0-112">See also</span></span>

- [<span data-ttu-id="a37e0-113">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="a37e0-113">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="a37e0-114">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a37e0-114">ADO.NET Overview</span></span>](ado-net-overview.md)
