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
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="93841-102">GetSchema a kolekcemi schémat</span><span class="sxs-lookup"><span data-stu-id="93841-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="93841-103">**Připojení** třídy v každé z implementace spravovaných zprostředkovatelé rozhraní .NET Framework **GetSchema** metodu, která se používá k načtení schématu informace o databázi, která je aktuálně připojen, a informace o schématu vrácená z **GetSchema** metoda obsahuje ve formě <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="93841-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="93841-104">**GetSchema** metoda je přetížené metody, která poskytuje volitelné parametry pro zadání kolekce schémat vrátit a omezení množství vrácených informací.</span><span class="sxs-lookup"><span data-stu-id="93841-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="93841-105">Určení kolekcemi schémat</span><span class="sxs-lookup"><span data-stu-id="93841-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="93841-106">První volitelný parametr **GetSchema** metoda je název kolekce, který je zadán jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="93841-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="93841-107">Existují dva typy kolekcí schémat: běžné kolekcemi schémat, které jsou společné pro všechny poskytovatele a konkrétní schéma kolekce, které jsou specifické pro každého zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="93841-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="93841-108">Můžete zadat dotaz rozhraní .NET Framework spravovaného zprostředkovatele určit seznam podporovaných schématu kolekcí voláním **GetSchema** metoda bez argumentů nebo názvem schématu kolekce "MetaDataCollections".</span><span class="sxs-lookup"><span data-stu-id="93841-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="93841-109">Tato možnost vrátí <xref:System.Data.DataTable> seznam podporovaných schéma kolekce, počet omezení, které každý podporují a počet identifikátor částí, které používají.</span><span class="sxs-lookup"><span data-stu-id="93841-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="93841-110">Načítání schématu kolekce příklad</span><span class="sxs-lookup"><span data-stu-id="93841-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="93841-111">Následující příklady ukazují, jak používat <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metoda zprostředkovatele dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> třída načíst informace o schématu o všechny tabulky obsažené v **AdventureWorks**ukázkové databáze:</span><span class="sxs-lookup"><span data-stu-id="93841-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93841-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="93841-112">See Also</span></span>  
 [<span data-ttu-id="93841-113">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="93841-113">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="93841-114">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="93841-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
