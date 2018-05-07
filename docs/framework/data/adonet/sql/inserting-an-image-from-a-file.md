---
title: Vkládání obrázek ze souboru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.openlocfilehash: 3b5b6f2f267f19b3ea42c352a8a1e3721a1ceb86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="inserting-an-image-from-a-file"></a>Vkládání obrázek ze souboru
Binární rozsáhlý objekt (binární rozsáhlý OBJEKT) můžete zapisovat jako binární nebo znak dat, v závislosti na typu pole na zdroj dat do databáze. Objekt BLOB je obecný pojem, který odkazuje `text`, `ntext`, a `image` datové typy, které obvykle obsahují dokumenty a obrázky.  
  
 Zapsat hodnotu objektu BLOB do databáze, příkaz odpovídající příkazu INSERT nebo UPDATE a předejte hodnotu objektu BLOB jako vstupní parametr (viz [parametry konfigurace a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)). Pokud objektu BLOB služby se uloží jako text, třeba s SQL serverem `text` pole, můžete předat objekt BLOB jako parametr řetězce. Pokud objekt BLOB se ukládají v binárním formátu, třeba s SQL serverem `image` pole, abyste mohli předávat pole typu `byte` jako binární parametr.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu přidá do tabulky Zaměstnanci v databázi Northwind informace o zaměstnancích. Fotografie zaměstnance je čtení ze souboru a přidat do pole fotografii v tabulce, která je na pole obrázku.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Použití příkazů pro změny dat](../../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [Načítání binárních dat](../../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 [Binární a vysoké hodnoty na SQL Serveru](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [Mapování datových typů SQL Serveru](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
