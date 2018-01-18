---
title: "Vkládání obrázek ze souboru"
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
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a913e660292713d4c728da75e91d812a285edc51
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="inserting-an-image-from-a-file"></a><span data-ttu-id="4273d-102">Vkládání obrázek ze souboru</span><span class="sxs-lookup"><span data-stu-id="4273d-102">Inserting an Image from a File</span></span>
<span data-ttu-id="4273d-103">Binární rozsáhlý objekt (binární rozsáhlý OBJEKT) můžete zapisovat jako binární nebo znak dat, v závislosti na typu pole na zdroj dat do databáze.</span><span class="sxs-lookup"><span data-stu-id="4273d-103">You can write a binary large object (BLOB) to a database as either binary or character data, depending on the type of field at your data source.</span></span> <span data-ttu-id="4273d-104">Objekt BLOB je obecný pojem, který odkazuje `text`, `ntext`, a `image` datové typy, které obvykle obsahují dokumenty a obrázky.</span><span class="sxs-lookup"><span data-stu-id="4273d-104">BLOB is a generic term that refers to the `text`, `ntext`, and `image` data types, which typically contain documents and pictures.</span></span>  
  
 <span data-ttu-id="4273d-105">Zapsat hodnotu objektu BLOB do databáze, příkaz odpovídající příkazu INSERT nebo UPDATE a předejte hodnotu objektu BLOB jako vstupní parametr (viz [parametry konfigurace a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)).</span><span class="sxs-lookup"><span data-stu-id="4273d-105">To write a BLOB value to your database, issue the appropriate INSERT or UPDATE statement and pass the BLOB value as an input parameter (see [Configuring Parameters and Parameter Data Types](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)).</span></span> <span data-ttu-id="4273d-106">Pokud objektu BLOB služby se uloží jako text, třeba s SQL serverem `text` pole, můžete předat objekt BLOB jako parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="4273d-106">If your BLOB is stored as text, such as a SQL Server `text` field, you can pass the BLOB as a string parameter.</span></span> <span data-ttu-id="4273d-107">Pokud objekt BLOB se ukládají v binárním formátu, třeba s SQL serverem `image` pole, abyste mohli předávat pole typu `byte` jako binární parametr.</span><span class="sxs-lookup"><span data-stu-id="4273d-107">If the BLOB is stored in binary format, such as a SQL Server `image` field, you can pass an array of type `byte` as a binary parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4273d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="4273d-108">Example</span></span>  
 <span data-ttu-id="4273d-109">Následující příklad kódu přidá do tabulky Zaměstnanci v databázi Northwind informace o zaměstnancích.</span><span class="sxs-lookup"><span data-stu-id="4273d-109">The following code example adds employee information to the Employees table in the Northwind database.</span></span> <span data-ttu-id="4273d-110">Fotografie zaměstnance je čtení ze souboru a přidat do pole fotografii v tabulce, která je na pole obrázku.</span><span class="sxs-lookup"><span data-stu-id="4273d-110">A photo of the employee is read from a file and added to the Photo field in the table, which is an image field.</span></span>  
  
```vb  
Public Shared Sub AddEmployee( _  
  lastName As String, _  
  firstName As String, _  
  title As String, _  
  hireDate As DateTime, _  
  reportsTo As Integer, _  
  photoFilePath As String, _  
  connectionString As String)  
  
  Dim photo() as Byte = GetPhoto(photoFilePath)  
  
  Using connection As SqlConnection = New SqlConnection( _  
    connectionString)  
  
  Dim command As SqlCommand = New SqlCommand( _  
    "INSERT INTO Employees (LastName, FirstName, Title, " & _  
    "HireDate, ReportsTo, Photo) " & _  
    "Values(@LastName, @FirstName, @Title, " & _  
    "@HireDate, @ReportsTo, @Photo)", connection)   
  
  command.Parameters.Add("@LastName",  _  
    SqlDbType.NVarChar, 20).Value = lastName  
  command.Parameters.Add("@FirstName", _  
    SqlDbType.NVarChar, 10).Value = firstName  
  command.Parameters.Add("@Title", _  
    SqlDbType.NVarChar, 30).Value = title  
  command.Parameters.Add("@HireDate", _  
    SqlDbType.DateTime).Value = hireDate  
  command.Parameters.Add("@ReportsTo", _  
    SqlDbType.Int).Value = reportsTo  
  
  command.Parameters.Add("@Photo", _  
    SqlDbType.Image, photo.Length).Value = photo  
  
  connection.Open()  
  command.ExecuteNonQuery()  
  
  End Using  
End Sub  
  
Public Shared Function GetPhoto(filePath As String) As Byte()  
  Dim stream As FileStream = new FileStream( _  
     filePath, FileMode.Open, FileAccess.Read)  
  Dim reader As BinaryReader = new BinaryReader(stream)  
  
  Dim photo() As Byte = reader.ReadBytes(stream.Length)  
  
  reader.Close()  
  stream.Close()  
  
  Return photo  
End Function  
```  
  
```csharp  
public static void AddEmployee(  
  string lastName,   
  string firstName,   
  string title,   
  DateTime hireDate,   
  int reportsTo,   
  string photoFilePath,   
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);   
  
  command.Parameters.Add("@LastName",    
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",   
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",       
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",   
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",   
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4273d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="4273d-111">See Also</span></span>  
 [<span data-ttu-id="4273d-112">Použití příkazů pro změny dat</span><span class="sxs-lookup"><span data-stu-id="4273d-112">Using Commands to Modify Data</span></span>](../../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [<span data-ttu-id="4273d-113">Načítání binárních dat</span><span class="sxs-lookup"><span data-stu-id="4273d-113">Retrieving Binary Data</span></span>](../../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 [<span data-ttu-id="4273d-114">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="4273d-114">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="4273d-115">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="4273d-115">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="4273d-116">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="4273d-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
