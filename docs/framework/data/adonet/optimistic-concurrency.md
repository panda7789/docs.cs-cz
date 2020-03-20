---
title: Optimistická metoda souběžného zpracování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: e8d24a3998ca97fdf45e647bc40c1f7d6018ec20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149450"
---
# <a name="optimistic-concurrency"></a>Optimistická metoda souběžného zpracování
Ve víceuživatelském prostředí existují dva modely pro aktualizaci dat v databázi: optimistická souběžnost a pesimistické souběžnosti. Objekt <xref:System.Data.DataSet> je navržen tak, aby podporoval použití optimistické souběžnosti pro dlouhotrvající aktivity, jako je například vzdálené komunikace dat a interakci s daty.  
  
 Pesimistické souběžnosti zahrnuje uzamčení řádků ve zdroji dat zabránit ostatním uživatelům v úpravě dat způsobem, který ovlivňuje aktuálního uživatele. V pesimistickém modelu, když uživatel provede akci, která způsobí použití zámku, ostatní uživatelé nemohou provádět akce, které by byly v konfliktu se zámkem, dokud jej vlastník zámku neuvolní. Tento model se používá především v prostředích, kde je těžké tvrzení pro data, tak, aby náklady na ochranu dat s zámky je menší než náklady na vrácení transakce zpět, pokud dojde ke konfliktům souběžnosti.  
  
 Proto v pesimistické souběžnosti modelu, uživatel, který aktualizuje řádek vytvoří zámek. Dokud uživatel nedokončí aktualizaci a neuvolní zámek, nikdo jiný nemůže tento řádek změnit. Z tohoto důvodu pesimistické souběžnosti je nejlépe implementovat, když bude krátké časy uzamčení, jako v programovém zpracování záznamů. Pesimistické souběžnosti není škálovatelná možnost, když uživatelé jsou interakci s daty a způsobuje záznamy, které mají být uzamčeny pro relativně velké časové období.  
  
> [!NOTE]
> Pokud potřebujete aktualizovat více řádků ve stejné operaci, pak vytvoření transakce je škálovatelnější možnost než pomocí pesimistické zamykání.  
  
 Naproti tomu uživatelé, kteří používají optimistickou souběžnost, neuzamknou řádek při čtení. Pokud chce uživatel aktualizovat řádek, musí aplikace určit, zda jiný uživatel změnil řádek od jeho čtení. Optimistická souběžnost se obvykle používá v prostředích s nízkou kolizí pro data. Optimistická souběžnost zlepšuje výkon, protože není vyžadováno žádné uzamčení záznamů a uzamčení záznamů vyžaduje další prostředky serveru. Chcete-li zachovat uzamčení záznamů, je také vyžadováno trvalé připojení k databázovému serveru. Vzhledem k tomu, že tomu tak není v optimistickém modelu souběžnosti, připojení k serveru mohou obsluhovat větší počet klientů v kratším čase.  
  
 V optimistické souběžnosti modelu porušení se považuje za došlo, pokud poté, co uživatel obdrží hodnotu z databáze, jiný uživatel upraví hodnotu před první uživatel se pokusí upravit. Jak server řeší porušení souběžnosti je nejlépe zobrazit nejprve popisující následující příklad.  
  
 Následující tabulky následují příklad optimistické souběžnosti.  
  
 V 13:00 uživatel1 přečte řádek z databáze s následujícími hodnotami:  
  
 **Jméno příjmení CustID**  
  
 101 Kovář Bob  
  
|Název sloupce|Původní hodnota|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Bob|Bob|  
  
 V 13:01, User2 přečte stejný řádek.  
  
 V 13:03 uživatele změní **Jméno z** "Bob" na "Robert" a aktualizuje databázi.  
  
|Název sloupce|Původní hodnota|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Robert|Bob|  
  
 Aktualizace je úspěšná, protože hodnoty v databázi v době aktualizace odpovídají původním hodnotám, které uživatelmá 2.  
  
 V 13:05 uživatel1 změní křestní jméno "Bob" na "James" a pokusí se aktualizovat řádek.  
  
|Název sloupce|Původní hodnota|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|James|Robert|  
  
 V tomto okamžiku User1 narazí na optimistické narušení souběžnosti, protože hodnota v databázi ("Robert") již neodpovídá původní hodnotu, která User1 očekával ("Bob"). Porušení souběžnosti jednoduše vám umožní vědět, že aktualizace se nezdařila. Nyní je třeba rozhodnout, zda přepsat změny zadané User2 se změnami zadanými User1, nebo zrušit změny uživatelem1.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>Testování pro optimistické porušení souběžnosti  
 Existuje několik technik pro testování pro narušení optimistické souběžnosti. Jeden zahrnuje včetně sloupce časového razítka v tabulce. Databáze běžně poskytují funkce časového razítka, které lze použít k identifikaci data a času, kdy byl záznam naposledy aktualizován. Pomocí této techniky je sloupec časového razítka zahrnut do definice tabulky. Při každé aktualizaci záznamu je časové razítko aktualizováno tak, aby odráželo aktuální datum a čas. V testu pro optimistické porušení souběžnosti sloupec časového razítka je vrácena s libovolný dotaz na obsah tabulky. Při pokusu o aktualizaci je hodnota časového razítka v databázi porovnána s původní hodnotou časového razítka obsaženou v upraveném řádku. Pokud se shodují, aktualizace se provede a sloupec časového razítka se aktualizuje s aktuálním časem tak, aby odrážely aktualizaci. Pokud se neshodují, došlo k narušení optimistické souběžnosti.  
  
 Další technika pro testování pro narušení optimistické souběžnosti je ověřit, že všechny původní hodnoty sloupců v řádku stále odpovídají těm, které jsou nalezeny v databázi. Zvažte například následující dotaz:  
  
```sql
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 Chcete-li otestovat optimistické porušení souběžnosti při aktualizaci řádku v **tabulce1**, vydáte následující příkaz UPDATE:  
  
```sql
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Tak dlouho, dokud původní hodnoty odpovídají hodnotám v databázi, aktualizace se provádí. Pokud byla změněna hodnota, aktualizace nebude měnit řádek, protože klauzule WHERE nenajde shodu.  
  
 Všimněte si, že se doporučuje vždy vrátit jedinečnou hodnotu primárního klíče v dotazu. V opačném případě předchozí příkaz UPDATE může aktualizovat více než jeden řádek, což nemusí být váš záměr.  
  
 Pokud sloupec ve zdroji dat umožňuje null, bude pravděpodobně nutné rozšířit klauzuli WHERE, abyste zkontrolovali odpovídající nulový odkaz v místní tabulce a ve zdroji dat. Například následující příkaz UPDATE ověří, zda nulový odkaz v místním řádku stále odpovídá nulovému odkazu ve zdroji dat nebo že hodnota v místním řádku stále odpovídá hodnotě ve zdroji dat.  
  
```sql
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 Můžete také použít méně omezující kritéria při použití optimistického modelu souběžnosti. Například použití pouze sloupce primárníklíč v where klauzule způsobí, že data přepsat bez ohledu na to, zda ostatní sloupce byly aktualizovány od posledního dotazu. Klauzuli WHERE můžete také použít pouze pro určité sloupce, což vede k přepsání dat, pokud nebyla od posledního dotazování aktualizována určitá pole.  
  
### <a name="the-dataadapterrowupdated-event"></a>Událost DataAdapter.RowUpdated  
 **RowUpdated** událost objektu <xref:System.Data.Common.DataAdapter> lze použít ve spojení s technikami popsanými výše, poskytnout oznámení o použití optimistické porušení souběžnosti. **RowUpdated** dochází po každém pokusu o **aktualizaci upravený** řádek z **DataSet**. To umožňuje přidat speciální kód zpracování, včetně zpracování, když dojde k výjimce, přidání vlastní chudinských informací, přidání logiky opakování a tak dále. Objekt <xref:System.Data.Common.RowUpdatedEventArgs> vrátí **vlastnost RecordsAffected** obsahující počet řádků ovlivněných určitým příkazem aktualizace pro upravený řádek v tabulce. Nastavením příkazu update pro testování optimistické souběžnosti vrátí vlastnost **RecordsAffected** hodnotu 0, když došlo k narušení optimistické souběžnosti, protože nebyly aktualizovány žádné záznamy. Pokud se jedná o tento případ, je vyvolána výjimka. Událost **RowUpdated** umožňuje zpracovat tento výskyt a vyhnout se výjimce nastavením příslušné hodnoty **RowUpdatedEventArgs.Status,** například **UpdateStatus.SkipCurrentRow**. Další informace o události **RowUpdated** naleznete v [tématu Zpracování událostí datového adaptéru](handling-dataadapter-events.md).  
  
 Volitelně můžete nastavit **DataAdapter.ContinueUpdateOnError** na **true**, před voláním **Update**a reagovat na informace o chybě uložené ve vlastnosti **RowError** určitého řádku po dokončení **aktualizace.** Další informace naleznete v [tématu Informace o chybě řádku](./dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>Optimistický příklad souběžnosti  
 Následuje jednoduchý příklad, který nastaví **UpdateCommand** **DataAdapter** otestovat optimistické souběžnosti a potom používá **RowUpdated** událost k testování optimistických porušení souběžnosti. Při výskytu narušení optimistické souběžnosti aplikace nastaví **RowError** řádku, který byla vydána aktualizace tak, aby odrážela optimistické porušení souběžnosti.  
  
 Všimněte si, že hodnoty parametrů předané klauzuli WHERE příkazu UPDATE jsou mapovány na **původní** hodnoty příslušných sloupců.  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](updating-data-sources-with-dataadapters.md)
- [Informace o chybě na řádku](./dataset-datatable-dataview/row-error-information.md)
- [Transakce a souběžnost](transactions-and-concurrency.md)
- [Přehled ADO.NET](ado-net-overview.md)
