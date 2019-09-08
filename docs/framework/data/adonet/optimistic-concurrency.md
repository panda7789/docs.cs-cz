---
title: Optimistická metoda souběžného zpracování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: a8cca707f8fa82e97e988fcbe015b55e35b93499
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794678"
---
# <a name="optimistic-concurrency"></a>Optimistická metoda souběžného zpracování
Ve víceuživatelském prostředí existují dva modely pro aktualizaci dat v databázi: Optimistická souběžnost a pesimistická souběžnost. <xref:System.Data.DataSet> Objekt je navržený tak, aby podporoval použití optimistické souběžnosti pro dlouhotrvající aktivity, jako jsou vzdálená data a interakce s daty.  
  
 Pesimistická souběžnost zahrnuje uzamykání řádků ve zdroji dat, aby ostatní uživatelé nemohli upravovat data způsobem, který má vliv na aktuálního uživatele. V pesimistické modelu, pokud uživatel provede akci, která způsobí použití zámku, nemohou jiní uživatelé provádět akce, které by mohly být v konfliktu s zámkem, dokud ho vlastník zámku neuvolní. Tento model se primárně používá v prostředích, kde se vyskytují silné kolize dat, takže náklady na ochranu dat s zámky jsou nižší než náklady na vracení zpět transakcí, pokud dojde ke konfliktům souběžnosti.  
  
 Proto v pesimistické Concurrency modelu vytvoří uživatel, který aktualizuje řádek, zámek. Dokud uživatel nedokončil aktualizaci a uvolnil zámek, žádný jiný tento řádek nemůže změnit. Z tohoto důvodu je pesimistická souběžnost nejlépe implementována v případě, že doba uzamčení bude krátká, jako při programovém zpracování záznamů. Pesimistická souběžnost není škálovatelná možnost, když uživatelé vzájemně pracují s daty a způsobují, aby byly záznamy uzamčené poměrně velkých časových období.  
  
> [!NOTE]
> Pokud potřebujete aktualizovat více řádků ve stejné operaci, pak vytvoření transakce je pružnější možnost než použití Pesimistické uzamykání.  
  
 Naproti tomu uživatelé, kteří používají optimistické řízení souběžnosti, nezamkne řádek při čtení. Když uživatel chce aktualizovat řádek, aplikace musí určit, jestli jiný uživatel změnil řádek od jeho čtení. Optimistická souběžnost se obecně používá v prostředích s nízkým kolizí dat. Optimistická souběžnost zlepšuje výkon, protože není nutné žádné zamykání záznamů a uzamykání záznamů vyžaduje další prostředky serveru. Aby bylo možné zachovat zámky záznamů, je nutné trvale připojit k databázovému serveru. Vzhledem k tomu, že se nejedná o případ v optimistickém modelu souběžnosti, připojení k serveru jsou zdarma pro poskytování většího počtu klientů v kratší dobu.  
  
 V modelu optimistického souběžnosti se porušení považuje za, pokud poté, co uživatel obdrží hodnotu z databáze, změní jiný uživatel hodnotu předtím, než se první uživatel pokusí ho změnit. Jak server řeší porušení souběžnosti, je nejlepším způsobem, jak nejprve popsat následující příklad.  
  
 Následující tabulky následují jako příklad optimistické souběžnosti.  
  
 V 1:00 hodin uživatel1 přečte řádek z databáze s následujícími hodnotami:  
  
 **CustID příjmení FirstName**  
  
 101 Smith Jan  
  
|Název sloupce|Původní hodnota|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Bob|Bob|  
  
 V 1:01 večer uživatel2 načte stejný řádek.  
  
 V 1:03. uživatel2 uživatel2 změní **FirstName** z "Bob" na "Robert" a aktualizuje databázi.  
  
|Název sloupce|Původní hodnota|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Robert|Bob|  
  
 Aktualizace je úspěšná, protože hodnoty v databázi v době aktualizace odpovídají původním hodnotám, které má uživatel2.  
  
 V 1:05 ODP. uživatel1 změní jméno "Bob" na "James" a pokusí se řádek aktualizovat.  
  
|Název sloupce|Původní hodnota|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Petr|Robert|  
  
 V tomto okamžiku uživatel1 narazí na porušení optimistické souběžnosti, protože hodnota v databázi ("Robert") se už neshoduje s původní hodnotou, kterou uživatel1 očekával ("Bob"). Porušení souběžnosti vám stačí, když zjistíte, že se aktualizace nezdařila. Rozhodnutí teď musí být provedeno bez ohledu na to, jestli se změny dodávají v rámci aplikace uživatel2, a změny poskytované uživatelem user1, nebo změny podle uživatele user1 zrušit.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>Testování pro porušení optimistické souběžnosti  
 K dispozici je několik technik pro testování v případě porušení optimistické souběžnosti. Jedna zahrnuje zahrnutí sloupce časového razítka do tabulky. Databáze běžně poskytují funkci časového razítka, která se dá použít k identifikaci data a času poslední aktualizace záznamu. Pomocí této techniky je v definici tabulky zahrnut sloupec časového razítka. Pokaždé, když se záznam aktualizuje, časové razítko se aktualizuje tak, aby odráželo aktuální datum a čas. V testu pro porušení optimistické souběžnosti je sloupec časového razítka vrácen libovolným dotazem na obsah tabulky. Při pokusu o aktualizaci je hodnota časového razítka v databázi porovnána s původní hodnotou časového razítka obsaženou ve změněném řádku. Pokud se shodují, provede se aktualizace a sloupec časového razítka se aktualizuje aktuálním časem, aby odrážel aktualizaci. Pokud se neshodují, došlo k narušení optimistické souběžnosti.  
  
 Další technikou pro testování pro porušení optimistické souběžnosti je ověřit, zda všechny původní hodnoty sloupců v řádku stále odpovídají hodnotám nalezeným v databázi. Zvažte například následující dotaz:  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 Chcete-li provést test optimistického chování souběžnosti při aktualizaci řádku ve vlastnosti **Tabulka1**, vydejte následující příkaz Update:  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Pokud se původní hodnoty shodují s hodnotami v databázi, provede se aktualizace. Pokud byla hodnota změněna, nebude tato aktualizace řádek upravovat, protože klauzule WHERE nenajde shodu.  
  
 Všimněte si, že se doporučuje vždycky vracet jedinečnou hodnotu primárního klíče v dotazu. V opačném případě může předchozí příkaz UPDATE aktualizovat více než jeden řádek, který nemusí být vaším záměrem.  
  
 Pokud sloupec v datovém zdroji povoluje hodnoty null, může být nutné zvětšit klauzuli WHERE, aby kontrolovala shodný odkaz null v místní tabulce a ve zdroji dat. Například následující příkaz UPDATE ověřuje, že odkaz s hodnotou null v místním řádku se stále shoduje s nulovým odkazem ve zdroji dat nebo že hodnota v místním řádku se stále shoduje s hodnotou ve zdroji dat.  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 Při použití optimistického modelu souběžnosti můžete také zvolit, že se mají použít méně omezující kritéria. Například použití pouze sloupců primárního klíče v klauzuli WHERE způsobí, že data budou přepsána bez ohledu na to, zda byly od posledního dotazu aktualizovány ostatní sloupce. Klauzuli WHERE můžete také použít pouze na konkrétní sloupce a výsledná data budou přepsána, pokud nebyla aktualizována konkrétní pole od posledního dotazu.  
  
### <a name="the-dataadapterrowupdated-event"></a>Událost DataAdapter. RowUpdated metody Update  
 Událost<xref:System.Data.Common.DataAdapter> **RowUpdated metody Update** objektu lze použít ve spojení s výše popsanými postupy, aby bylo možné poskytnout oznámení vaší aplikaci s porušením optimistické souběžnosti. K **RowUpdated metody Update** dochází po každém pokusu o aktualizaci **upraveného** řádku z **datové sady**. To umožňuje přidat speciální kód pro zpracování, včetně zpracování, když dojde k výjimce, přidání vlastních informací o chybě, přidání logiky opakování atd. Objekt vrátí vlastnost RecordsAffected obsahující počet řádků ovlivněných určitým příkazem aktualizace pro upravený řádek v tabulce. <xref:System.Data.Common.RowUpdatedEventArgs> Nastavením příkazu Update na test pro optimistickou souběžnost bude vlastnost **RecordsAffected** v důsledku toho vracet hodnotu 0, pokud došlo k narušení optimistické souběžnosti, protože nebyly aktualizovány žádné záznamy. Pokud se jedná o tento případ, je vyvolána výjimka. Událost **RowUpdated metody Update** umožňuje zpracovat tento výskyt a vyhnout se výjimce nastavením příslušné hodnoty **RowUpdatedEventArgs. status** , například **UpdateStatus. SkipCurrentRow**. Další informace o události **RowUpdated metody Update** naleznete v tématu [zpracování událostí DataAdapter](handling-dataadapter-events.md).  
  
 Volitelně můžete nastavit vlastnost **DataAdapter. ContinueUpdateOnError** na **hodnotu true**, před voláním metody **Update**a reagovat na informace o chybě uložené ve vlastnosti **RowError** určitého řádku po dokončení **aktualizace** . Další informace najdete v tématu [informace o chybě řádku](./dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>Příklad optimistického řízení souběžnosti  
 Následuje jednoduchý příklad, který nastaví **událost UpdateCommand** **na test** pro optimistickou souběžnost a poté používá událost **RowUpdated metody Update** k otestování optimistického chování souběžnosti. Když dojde k narušení optimistického řízení souběžnosti, aplikace nastaví **RowError** řádku, pro který byla aktualizace vystavena, aby odrážela optimistické porušení souběžnosti.  
  
 Všimněte si, že hodnoty parametrů předané do klauzule WHERE příkazu UPDATE jsou namapovány na **původní** hodnoty příslušných sloupců.  
  
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

- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Aktualizace zdrojů dat pomocí adaptérů dat](updating-data-sources-with-dataadapters.md)
- [Informace o chybě na řádku](./dataset-datatable-dataview/row-error-information.md)
- [Transakce a souběžnost](transactions-and-concurrency.md)
- [Přehled ADO.NET](ado-net-overview.md)
