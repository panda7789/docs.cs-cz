---
title: Optimistická metoda souběžného zpracování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: f2fc69867ae1659a342161b00dfd91852441fa5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126214"
---
# <a name="optimistic-concurrency"></a>Optimistická metoda souběžného zpracování
V prostředí, existují dva modely pro aktualizaci dat v databázi: optimistického řízení souběžnosti a Pesimistická souběžnost. <xref:System.Data.DataSet> Objektu je účelem je podporovat používání optimistického řízení souběžnosti pro dlouho běžící aktivity, jako jsou data vzdálenou komunikaci a interakci s daty.  
  
 Pesimistická souběžnost zahrnuje uzamčení řádků ve zdroji dat k ostatním uživatelům zabránit ve změně data způsobem, který má vliv aktuálního uživatele. Pesimistické modelu když uživatel provede akci, která způsobí, že zámek, který má být použita, nemůže ostatním uživatelům provádět akce, které by byla v konfliktu s uzamčením dokud ho vlastník zámku uvolní. Tento model se používá především v prostředích, kde je těžké kolizí pro data, aby náklady na ochranu dat pomocí zámků je nižší než náklady na transakce vrácení zpět, jestliže se vyskytnou konflikty souběžnosti.  
  
 V modelu Pesimistická souběžnost, proto uživatel, který aktualizuje řádek vytvoří zámek. Dokud uživatel dokončení aktualizace a vydání zámek, nikdo jiný změňte tento řádek. Z tohoto důvodu je Pesimistická souběžnost nejlépe implementována, pokud bude zámek časy krátký, stejně jako v programové zpracování záznamů. Pesimistická souběžnost není škálovatelné možnost, když jsou uživatelé interakci s daty a způsobí záznamů, které mají být uzamčen pro relativně velké časová období.  
  
> [!NOTE]
>  Pokud je potřeba aktualizovat v rámci jedné operace více řádků, pak vytváření transakcí je možnost a větší škálovatelnost než použití pesimistické zamykání.  
  
 Oproti tomu uživatelé, kteří používají optimistického řízení souběžnosti nepoužívejte zámky řádku při čtení. Když chce uživatel aktualizace řádku, musíte aplikaci určit, zda jiný uživatel změnil řádek, protože byl načten. Optimistického řízení souběžnosti se obvykle používá v prostředích s nízkou kolizí pro data. Optimistická souběžnost zlepší výkon, protože žádné uzamčení záznamů je povinná a klauzule zamykání záznamů vyžaduje dalších serverových prostředků. Aby zůstalo zachované uzamčení záznamů, je také požadované trvalé připojení k databázovému serveru. Protože to není případ v modelu optimistického řízení souběžnosti, připojení k serveru je zdarma pro obsluhu větší počet klientů v méně času.  
  
 V modelu optimistického řízení souběžnosti porušení se považuje za došlo, pokud, jakmile uživatel obdrží hodnotu z databáze, jiný uživatel změní hodnotu před první uživatel se pokusil změnit. Jak server odstraňuje narušení souběžného zpracování se nejlíp zobrazí první popsáním v následujícím příkladu.  
  
 V následujících tabulkách použijte příklad optimistického řízení souběžnosti.  
  
 Uživatel1 v 13:00:00, načte řádek z databáze s použitím následujících hodnot:  
  
 **Jméno příjmení CustID**  
  
 101 Smith Bob  
  
|Název sloupce|Původní hodnota|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Bob|Bob|  
  
 V 13:01:00 uživatel2 přečte na stejném řádku.  
  
 Ve 13:03:00, uživatel2 změní **FirstName** z "Bob" řetězec "Robert" a aktualizaci databáze.  
  
|Název sloupce|Původní hodnota|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Robert|Bob|  
  
 Tato aktualizace bude úspěšné, protože původní hodnoty, které má uživatel2 shodovat s hodnotami v databázi v době aktualizace.  
  
 V 13:05:00 uživatel1 "Bob" jméno se změní na "James" a pokus o aktualizaci řádku.  
  
|Název sloupce|Původní hodnota|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|James|Robert|  
  
 V tomto okamžiku User1 dojde k narušení optimistického řízení souběžnosti protože hodnota v databázi ("Robert") už odpovídá původní hodnotu, že User1 očekávané ("Bob"). Narušení souběžného zpracování jednoduše poznáte, že aktualizace nebyla úspěšná. Rozhodnutí teď je potřeba provést, zda chcete přepsat změny poskytnutých uživatel2 změnami poskytnutých uživatel1, nebo zrušit změny uživatele User1.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>Testování pro porušení optimistického řízení souběžnosti  
 Existuje několik postupů pro testování na narušení optimistického řízení souběžnosti. Zahrnuje jeden, včetně sloupec časového razítka v tabulce. Databáze obvykle poskytují funkce časového razítka, který můžete použít k identifikaci datum a čas poslední aktualizace záznamu. Tímto způsobem je sloupec časového razítka zahrnuta v definici tabulky. Pokaždé, když se tento záznam se aktualizuje, časové razítko se aktualizuje tak, aby odrážela aktuální datum a čas. V rámci testu pro porušení optimistického řízení souběžnosti je vrácen sloupec časového razítka s jakýkoli dotaz obsah tabulky. Při pokusu o aktualizaci hodnotu časového razítka v databázi je ve srovnání s původní hodnotu časového razítka v řádku upravené. Pokud se shodují, se provádí aktualizace a sloupec časového razítka se aktualizuje s aktuálním časem tak, aby odrážely aktualizace. Pokud shodné nejsou, došlo k narušení optimistického řízení souběžnosti.  
  
 Další možností, jak testování pro narušení optimistického řízení souběžnosti se k ověření, že všechny původní hodnoty sloupce v řádku stále shodovat s hodnotami v databázi nalezen. Zvažte například následující dotaz:  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 Pro testování narušení optimistického řízení souběžnosti při aktualizaci řádku **Tabulka1**, by vydat příkaz následující aktualizace:  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Za předpokladu, původní hodnoty shodují s hodnotami v databázi, provádí se aktualizace. Pokud se změnila hodnotu, nebude aktualizace změnit řádku, protože klauzule WHERE nenajde shoda.  
  
 Mějte na paměti, doporučuje se vždycky vrátit jedinečné hodnoty primárního klíče v dotazu. Předchozí příkaz UPDATE v opačném případě může aktualizovat více než jeden řádek, který nemusí být vašich představ.  
  
 Pokud sloupec na zdroj dat se povoluje hodnoty Null, budete muset rozšířit vaše klauzule WHERE, která pro odpovídající odkaz s hodnotou null v lokální tabulce a ve zdroji dat. Zkontrolujte. Například následující příkaz aktualizace ověřuje, že odkaz s hodnotou null v řádku místní stále odpovídá nulový odkaz na zdroj dat, nebo jestli hodnotu v řádku místní stále odpovídá hodnotě ve zdroji dat.  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 Můžete také použít méně omezující kritéria při použití modelu optimistického řízení souběžnosti. Například použití pouze primární klíčových sloupců v klauzuli WHERE způsobí, že data, která mají být přepsány bez ohledu na to, zda další sloupce, které byly aktualizovány od posledního dotazu. Můžete také použít klauzuli WHERE pouze na konkrétní sloupce, což vede k přepsání Pokud konkrétních polích byly aktualizovány od posledního dotazovat data.  
  
### <a name="the-dataadapterrowupdated-event"></a>DataAdapter.RowUpdated události  
 **RowUpdated** událost <xref:System.Data.Common.DataAdapter> objekt lze použít ve spojení pomocí technik popsaných výše, k poskytování oznámení do vaší aplikace porušení optimistického řízení souběžnosti. **RowUpdated** dojde poté, co každý pokus o aktualizaci **změněné** řádek z **datovou sadu**. To umožňuje přidat zvláštní zpracování kódu, včetně zpracování, když dojde k výjimce, přidání vlastních informací o chybě, přidání logiky pro opakování a tak dále. <xref:System.Data.Common.RowUpdatedEventArgs> Vrátí objekt **RecordsAffected** vlastnost obsahuje počet řádků, které jsou ovlivněny příkazu konkrétní update pro upravené řádek v tabulce. Nastavením příkaz aktualizace pro testování optimistického řízení souběžnosti **RecordsAffected** vlastnost, v důsledku toho vrátí hodnotu 0 při došlo k narušení optimistického řízení souběžnosti, protože byly aktualizovány žádné záznamy. Pokud je to tento případ, je vyvolána výjimka. **RowUpdated** událostí umožňuje zpracovávat tento výskyt a vyhnout se výjimka nastavením odpovídající **RowUpdatedEventArgs.Status** hodnoty, jako například  **UpdateStatus.SkipCurrentRow**. Další informace o **RowUpdated** událostí, naleznete v tématu [zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
 Volitelně můžete nastavit **DataAdapter.ContinueUpdateOnError** k **true**, před voláním **aktualizace**a reagovat na chybové informace uložené v **RowError** vlastnost konkrétní řádek, kdy **aktualizace** je dokončena. Další informace najdete v tématu [informace o chybě řádek](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>Příklad optimistického řízení souběžnosti  
 Tady je jednoduchý příklad, který nastaví **událost UpdateCommand** z **DataAdapter** pro testování optimistického řízení souběžnosti a potom použije **RowUpdated** události pro testování porušení optimistického řízení souběžnosti. Když je zjištěna narušení optimistického řízení souběžnosti, aplikace nastaví **RowError** řádku, na který aktualizace byl vydán pro tak, aby odrážely narušení optimistického řízení souběžnosti.  
  
 Všimněte si, že se parametr hodnoty předané do klauzule WHERE příkazu pro aktualizaci se mapují na **původní** hodnoty jejich odpovídajících sloupců.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [Informace o chybě na řádku](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)
- [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
