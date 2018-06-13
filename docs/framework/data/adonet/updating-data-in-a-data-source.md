---
title: Aktualizace dat ve zdroji dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 11c3faa85d6d0b77c4e606815aa8252188b6f67d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357790"
---
# <a name="updating-data-in-a-data-source"></a>Aktualizace dat ve zdroji dat
SQL příkazy, které upravují data (například INSERT, UPDATE nebo DELETE) nevrátí řádků. Podobně mnoho uložené procedury provedení akce, ale nevrátí řádků. Chcete-li provést příkazy, které nevracejí řádky, vytvořte **příkaz** objekt s příslušný příkaz SQL a **připojení**, včetně požadované **parametry**. Spusťte příkaz se **ExecuteNonQuery** metodu **příkaz** objektu.  
  
 **ExecuteNonQuery** metoda vrátí celé číslo představující počet řádků, které jsou ovlivněné příkaz nebo uložené procedury, která byla spuštěna. Pokud jsou vícenásobné příkazy proveden, je hodnota vrácená součet záznamů ovlivněný všechny příkazy provést.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu provede k vložení záznamu do databáze pomocí příkazu INSERT **ExecuteNonQuery**.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
connection.Open()  
  
Dim queryString As String = "INSERT INTO Customers " & _  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')"  
  
Dim command As SqlCommand = New SqlCommand(queryString, connection)  
Dim recordsAffected As Int32 = command.ExecuteNonQuery()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
string queryString = "INSERT INTO Customers " +  
  "(CustomerID, CompanyName) Values('NWIND', 'Northwind Traders')";  
  
SqlCommand command = new SqlCommand(queryString, connection);  
Int32 recordsAffected = command.ExecuteNonQuery();  
```  
  
 Následující příklad kódu provede uloženou proceduru vytvořené ukázkový kód v [provádění operací katalogu](../../../../docs/framework/data/adonet/performing-catalog-operations.md). Žádné řádky se vrátí pomocí uložené procedury, proto **ExecuteNonQuery** metoda se používá, ale uložená procedura přijímat vstupní parametr a vrátí výstupní parametr a návratovou hodnotu.  
  
 Pro <xref:System.Data.OleDb.OleDbCommand> objekt, **ReturnValue** parametr musí být přidán do **parametry** kolekce první.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim command As SqlCommand = _  
   New SqlCommand("InsertCategory" , connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As SqlParameter = _  
 command.Parameters.Add("@RowCount", SqlDbType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@CategoryName", SqlDbType.NChar, 15)  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int)  
parameter.Direction = ParameterDirection.Output  
  
command.Parameters("@CategoryName").Value = "New Category"  
command.ExecuteNonQuery()  
  
Dim categoryID As Int32 = CInt(command.Parameters("@Identity").Value)  
Dim rowCount As Int32 = CInt(command.Parameters("@RowCount").Value)   
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlCommand command = new SqlCommand("InsertCategory" , connection);  
command.CommandType = CommandType.StoredProcedure;  
  
SqlParameter parameter = command.Parameters.Add(  
  "@RowCount", SqlDbType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@CategoryName", SqlDbType.NChar, 15);  
  
parameter = command.Parameters.Add("@Identity", SqlDbType.Int);  
parameter.Direction = ParameterDirection.Output;  
  
command.Parameters["@CategoryName"].Value = "New Category";  
command.ExecuteNonQuery();  
  
Int32 categoryID = (Int32) command.Parameters["@Identity"].Value;  
Int32 rowCount = (Int32) command.Parameters["@RowCount"].Value;  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití příkazů pro změny dat](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
