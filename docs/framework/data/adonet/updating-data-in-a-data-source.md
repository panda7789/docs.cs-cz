---
title: Aktualizace dat ve zdroji dat.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c545e5-dcd5-4323-a5b9-3825c2157462
ms.openlocfilehash: d7b57a9572a285dfdc13afb0a520de67e231a1c0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43540513"
---
# <a name="updating-data-in-a-data-source"></a>Aktualizace dat ve zdroji dat.
Příkazy SQL, které upravují data (například vložení, aktualizace nebo odstranění) nevracejí řádky. Podobně mnoho uložené procedury provést akci, ale nevracejí řádky. Ke spuštění příkazů, které nevracejí řádky, vytvořit **příkaz** objekt s příslušný příkaz SQL a **připojení**, včetně požadované **parametry**. Příkaz Spustit **metodu ExecuteNonQuery** metodu **příkaz** objektu.  
  
 **Metodu ExecuteNonQuery** metoda vrátí celé číslo představující počet řádků, které jsou ovlivněny příkazu nebo uložené procedury, která se spustil. Pokud více příkazy jsou spouštěny, vrácená hodnota je součtem záznamů ovlivněný všechny příkazy spuštění.  
  
## <a name="example"></a>Příklad  
 Příkaz INSERT k vložení záznamu do databáze pomocí provádí následující příklad kódu **metodu ExecuteNonQuery**.  
  
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
  
 Následující příklad kódu Spustí uloženou proceduru vytvořen ukázkový kód v [provádění operací katalogu](../../../../docs/framework/data/adonet/performing-catalog-operations.md). Žádné řádky jsou vráceny pomocí uložené procedury, takže **metodu ExecuteNonQuery** metoda se používá, ale zobrazí vstupní parametr uložené procedury a vrátí výstupní parametr a návratové hodnoty.  
  
 Pro <xref:System.Data.OleDb.OleDbCommand> objektu, **ReturnValue** parametr musí být přidané do **parametry** kolekce první.  
  
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
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
