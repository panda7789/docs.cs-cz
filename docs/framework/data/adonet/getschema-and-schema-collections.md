---
title: Příkaz GetSchema a kolekce schémat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab93b89-1221-427c-84ad-04803b3c64b4
ms.openlocfilehash: 11cfad81e40e76691db9f99efd1d60f5528600d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667042"
---
# <a name="getschema-and-schema-collections"></a><span data-ttu-id="ecb58-102">Příkaz GetSchema a kolekce schémat</span><span class="sxs-lookup"><span data-stu-id="ecb58-102">GetSchema and Schema Collections</span></span>
<span data-ttu-id="ecb58-103">**Připojení** třídami implementace spravovaného zprostředkovatele .NET Framework **GetSchema** metodu, která se používá k načtení informací o schématu databáze, která je aktuálně připojena, a informace o schématu vrácených **GetSchema** metoda je k dispozici ve formě <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="ecb58-103">The **Connection** classes in each of the .NET Framework managed providers implement a **GetSchema** method which is used to retrieve schema information about the database that is currently connected, and the schema information returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="ecb58-104">**GetSchema** je metoda přetížená metoda, která poskytuje volitelných parametrů pro určení kolekce schématu pro vrácení a omezit množství vrácených informací.</span><span class="sxs-lookup"><span data-stu-id="ecb58-104">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
## <a name="specifying-the-schema-collections"></a><span data-ttu-id="ecb58-105">Určení kolekce schémat</span><span class="sxs-lookup"><span data-stu-id="ecb58-105">Specifying the Schema Collections</span></span>  
 <span data-ttu-id="ecb58-106">První nepovinný parametr **GetSchema** metody je název kolekce, který je zadán jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="ecb58-106">The first optional parameter of the **GetSchema** method is the collection name which is specified as a string.</span></span> <span data-ttu-id="ecb58-107">Existují dva typy kolekce schémat: společné kolekce schémat, které jsou společné pro všechny poskytovatele a kolekce určité schéma, které jsou specifické pro každého zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="ecb58-107">There are two types of schema collections: common schema collections that are common to all providers, and specific schema collections which are specific to each provider.</span></span>  
  
 <span data-ttu-id="ecb58-108">Můžete dát dotaz na zprostředkovatele rozhraní .NET Framework spravované určit seznam kolekcí nepodporuje schéma voláním **GetSchema** metody bez argumentů nebo názvem kolekce schématu "MetaDataCollections".</span><span class="sxs-lookup"><span data-stu-id="ecb58-108">You can query a .NET Framework managed provider to determine the list of supported schema collections by calling the **GetSchema** method with no arguments, or with the schema collection name "MetaDataCollections".</span></span> <span data-ttu-id="ecb58-109">Vrátí <xref:System.Data.DataTable> seznam kolekcí nepodporuje schéma, počet omezení, které každá podporují a počet identifikátor částí, které používají.</span><span class="sxs-lookup"><span data-stu-id="ecb58-109">This will return a <xref:System.Data.DataTable> with a list of the supported schema collections, the number of restrictions that they each support, and the number of identifier parts that they use.</span></span>  
  
### <a name="retrieving-schema-collections-example"></a><span data-ttu-id="ecb58-110">Načítání kolekcí příkladu schématu</span><span class="sxs-lookup"><span data-stu-id="ecb58-110">Retrieving Schema Collections Example</span></span>  
 <span data-ttu-id="ecb58-111">Následující příklady ukazují, jak používat <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metoda zprostředkovatele dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> třídy pro načtení schématu informace o všech tabulek, které jsou součástí **AdventureWorks**ukázkovou databázi:</span><span class="sxs-lookup"><span data-stu-id="ecb58-111">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ecb58-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecb58-112">See also</span></span>

- [<span data-ttu-id="ecb58-113">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="ecb58-113">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="ecb58-114">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ecb58-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
