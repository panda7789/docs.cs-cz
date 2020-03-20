---
title: Aktualizace dat ve zdroji dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: 18bb03e17b19243ee1bc6e3f7ebd70afb4d4c60b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174443"
---
# <a name="updating-data-in-a-data-source"></a>Aktualizace dat ve zdroji dat
Příkazy SQL, které upravují data (například INSERT, UPDATE nebo DELETE), nevracejí řádky. Podobně mnoho uložené procedury provést akci, ale nevracejí řádky. Chcete-li spouštět příkazy, které nevracejí řádky, vytvořte objekt **Příkaz** s příslušným příkazem SQL a **připojením**, včetně všech **požadovaných parametrů**. Spusťte příkaz metodou **ExecuteNonQuery** objektu **Command.**  
  
 Metoda **ExecuteNonQuery** vrátí celé číslo, které představuje počet řádků ovlivněných příkazem nebo uloženou procedurou, která byla spuštěna. Pokud je provedeno více příkazů, vrácená hodnota je součtem záznamů ovlivněných všemi příkazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu provede příkaz INSERT pro vložení záznamu do databáze pomocí **příkazu ExecuteNonQuery**.  
  
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
  
 Následující příklad kódu provede uloženou proceduru vytvořenou ukázkovým kódem [v provedení operací katalogu](performing-catalog-operations.md). Uložená procedura nevrací žádné řádky, takže se používá metoda **ExecuteNonQuery,** ale uložená procedura obdrží vstupní parametr a vrátí výstupní parametr a vrácenou hodnotu.  
  
 Pro <xref:System.Data.OleDb.OleDbCommand> objekt **returnvalue** parametr musí být přidán do **kolekce Parameters** jako první.  
  
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

- [Použití příkazů pro změny dat](using-commands-to-modify-data.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](updating-data-sources-with-dataadapters.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Přehled ADO.NET](ado-net-overview.md)
