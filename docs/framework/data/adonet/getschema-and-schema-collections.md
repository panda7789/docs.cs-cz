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
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="e7997-102">Příkaz GetSchema a kolekce schémat</span><span class="sxs-lookup"><span data-stu-id="e7997-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="e7997-103">Třídy **připojení** v každém z .NET Framework spravovaných zprostředkovatelé implementují metodu **GetSchema** , která se používá k načtení informací o schématu o databázi, která je aktuálně připojená, a informace o schématu vrácené z  **Metoda GetSchema** je dodávána ve formě <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="e7997-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="e7997-104">Metoda **GetSchema** je přetížená metoda, která poskytuje volitelné parametry pro určení kolekce schématu, která se má vrátit, a omezení množství vrácených informací.</span><span class="sxs-lookup"><span data-stu-id="e7997-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="e7997-105">Určení kolekcí schémat</span><span class="sxs-lookup"><span data-stu-id="e7997-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="e7997-106">Prvním volitelným parametrem metody **GetSchema** je název kolekce, který je určen jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="e7997-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="e7997-107">Existují dva typy kolekcí schémat: společné kolekce schémat, které jsou společné pro všechny poskytovatele, a konkrétní kolekce schémat, které jsou specifické pro každého poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="e7997-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="e7997-108">Můžete zadat dotaz na .NET Framework spravovaného poskytovatele a určit seznam podporovaných kolekcí schémat voláním metody **GetSchema** bez argumentů nebo s názvem kolekce schématu "MetaDataCollections".</span><span class="sxs-lookup"><span data-stu-id="e7997-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="e7997-109">Tato akce vrátí <xref:System.Data.DataTable> seznam podporovaných kolekcí schémat, počet omezení, která jednotlivé požadavky podporují, a počet částí identifikátorů, které používají.</span><span class="sxs-lookup"><span data-stu-id="e7997-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="e7997-110">Příklad načítání kolekcí schémat</span><span class="sxs-lookup"><span data-stu-id="e7997-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="e7997-111">Následující příklady ukazují, jak použít <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metodu .NET Framework Zprostředkovatel dat pro třídu SQL Server <xref:System.Data.SqlClient.SqlConnection> k načtení informací o schématu o všech tabulkách obsažených v ukázkové databázi **AdventureWorks** :</span><span class="sxs-lookup"><span data-stu-id="e7997-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7997-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7997-112">See also</span></span>

- [<span data-ttu-id="e7997-113">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="e7997-113">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="e7997-114">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e7997-114">ADO.NET Overview</span></span>](ado-net-overview.md)
