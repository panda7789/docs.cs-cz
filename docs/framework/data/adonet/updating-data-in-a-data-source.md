---
title: Aktualizace dat ve zdroji dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 0926e3c6513a698ae47b9983d0e6ad195394a4df
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780611"
---
# <a name="updating-data-in-a-data-source"></a>Aktualizace dat ve zdroji dat
Příkazy jazyka SQL, které upravují data (například INSERT, UPDATE nebo DELETE), nevrací řádky. Podobně mnoho uložených procedur provádí akci, ale nevrací řádky. Chcete-li provést příkazy, které nevracejí řádky, vytvořte objekt **příkazu** s příslušným příkazem SQL a **připojením**, včetně požadovaných **parametrů**. Spusťte příkaz s metodou **ExecuteNonQuery** objektu **Command** .  
  
 Metoda **ExecuteNonQuery** vrací celé číslo, které představuje počet řádků ovlivněných příkazem nebo uloženou procedurou, která byla provedena. Pokud je spuštěno více příkazů, vrácená hodnota je součet záznamů ovlivněných všemi provedenými příkazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu provede příkaz INSERT pro vložení záznamu do databáze pomocí **ExecuteNonQuery**.  
  
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
  
 Následující příklad kódu provede uloženou proceduru vytvořenou vzorovým kódem při [provádění operací katalogu](performing-catalog-operations.md). Uložený postup nevrátí žádné řádky, takže se použije metoda **ExecuteNonQuery** , ale uložená procedura obdrží vstupní parametr a vrátí výstupní parametr a návratovou hodnotu.  
  
 Pro objekt je nutné nejprve přidat parametr **ReturnValue** do kolekce Parameters. <xref:System.Data.OleDb.OleDbCommand>  
  
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
  
## <a name="see-also"></a>Viz také:

- [Použití příkazů pro změny dat](using-commands-to-modify-data.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](updating-data-sources-with-dataadapters.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Přehled ADO.NET](ado-net-overview.md)
