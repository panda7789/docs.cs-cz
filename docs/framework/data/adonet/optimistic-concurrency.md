---
title: "Optimistickou metodu souběžného zpracování"
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
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 45939dcec8b8db8e1b06ebfc67d89bfead67575a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optimistic-concurrency"></a>Optimistickou metodu souběžného zpracování
V prostředí, jsou dva modely pro aktualizace dat v databázi: optimistickou metodu souběžného a pesimistické souběžnosti. <xref:System.Data.DataSet> Objekt je navržen pro podporu použití optimistickou metodu souběžného pro dlouho běžící aktivity, jako je vzdálené komunikace dat a práce s daty.  
  
 Pesimistické souběžnosti zahrnuje uzamčení řádků ve zdroji dat k ostatním uživatelům zabránit upravovat data způsobem, který ovlivňuje aktuálního uživatele. V pesimistické modelu když uživatel provede akci, která způsobí zámek má být použita, nelze jiní uživatelé provádět akce, které by byl v konfliktu s zámek dokud uvolněním vlastníka zámku. Tento model se používá hlavně v prostředích, kde je těžká kolizí pro data, aby náklady na ochranu dat s zámky je menší než náklady na transakce vrácení zpět, jestliže dojde ke konfliktu souběžnosti.  
  
 Proto v modelu pesimistické souběžnosti vytvoří uživatel, který aktualizuje řádek zámek. Dokud se uživatel má dokončení aktualizace a vydání zámek, nikdo jiný, můžete změnit příslušném řádku. Z tohoto důvodu je pesimistické souběžnosti nejlépe implementována, pokud doby uzamčení bude krátký jako programový zpracování záznamů. Pesimistické souběžnosti není škálovatelné možnost, když jsou uživatelé interakci s daty a způsobuje záznamů se uzamkne za relativně velké období.  
  
> [!NOTE]
>  Pokud je potřeba aktualizovat více řádků v rámci jedné operace, pak vytvoření transakce je více škálovatelného než použití pesimistické zamykání.  
  
 Uživatelé, kteří používají optimistickou metodu souběžného naopak neblokují řádku při jeho čtení. Pokud chce uživatel o aktualizaci řádku, aplikace musí určit, zda jiný uživatel změnil řádek od čtení. Optimistickou metodu souběžného se obvykle používá v prostředích s nízkou kolizí pro data. Optimistickou metodu souběžného zvyšuje výkon, protože se vyžaduje žádné uzamčení záznamů a zamykání záznamů vyžaduje další server prostředků. Aby byla zachována uzamčení záznamů, je taky požadované trvalé připojení k databázovému serveru. Protože to není případu v modelu optimistickou metodu souběžného, připojení k serveru jsou zdarma k obsluze větší počet klientů v méně času.  
  
 Ve model optimistickou metodu souběžného narušení je považován za došlo, pokud po uživatel obdrží hodnotu z databáze, jiný uživatel změní hodnotu před první uživatel se pokusil upravit. Jak server přeloží narušení souběžného zpracování se zobrazí nejlépe prostřednictvím první popisu v následujícím příkladu.  
  
 V následujících tabulkách použijte příklad optimistickou metodu souběžného.  
  
 Uživatel1 v 13:00:00, čte řádek z databáze s následujícími hodnotami:  
  
 **CustID příjmení jméno**  
  
 101 Bob Smith  
  
|Název sloupce|Původní hodnotu|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|Příjmení|Smith|Smith|Smith|  
|FirstName|Bob|Bob|Bob|  
  
 V 13:01:00 uživatel2 přečte na stejném řádku.  
  
 V 13:03:00, uživatel2 změny **FirstName** z "Bob" na "Robert" a aktualizaci databáze.  
  
|Název sloupce|Původní hodnotu|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|Příjmení|Smith|Smith|Smith|  
|FirstName|Bob|Robert|Bob|  
  
 Aktualizace úspěšná, protože původní hodnoty, které má uživatel2 shodují s hodnotami v databázi v době aktualizace.  
  
 V 13:05:00 uživatel1 změny jméno "Bob" na "James" a pokus o aktualizaci řádku.  
  
|Název sloupce|Původní hodnotu|Aktuální hodnota|Hodnota v databázi|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|Příjmení|Smith|Smith|Smith|  
|FirstName|Bob|James|Robert|  
  
 V tomto okamžiku uživatel1 zaznamená porušení optimistickou metodu souběžného, protože hodnota v databázi ("Robert") už odpovídá původní hodnotu Uživatel1 byl očekáván ("Bob"). Porušení souběžnosti jednoduše umožňuje vědět, že aktualizace se nezdařila. Teď rozhodnutí musí být zda přepsat změny poskytl uživatel2 se změnami poskytl uživatel1, nebo zrušit změny provedené User1.  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>Testování pro porušení optimistickou metodu souběžného zpracování  
 Existuje několik postupů pro testování pro porušení optimistickou metodu souběžného. Jeden zahrnuje, včetně sloupec časového razítka v tabulce. Databáze obvykle poskytují funkce časové razítko, které lze použít k identifikaci datum a čas poslední aktualizace záznamu. Touto technikou sloupec časového razítka je součástí definice tabulky. Při každé aktualizaci záznamu časové razítko je aktualizována tak, aby odrážela aktuální datum a čas. V testu pro optimistickou metodu souběžného narušení je vrácena sloupec časového razítka s jakýkoli dotaz obsahu tabulky. Při pokusu o aktualizaci, hodnota časového razítka v databázi se porovná na původní hodnotu časové razítko, které jsou obsažené v upravené řádek. Pokud se shodují, se provádí aktualizace a sloupec časového razítka je aktualizována tak, aby odrážela aktualizace aktuální čas. Pokud se neshodují, došlo k porušení optimistickou metodu souběžného.  
  
 Jiné technika pro testování pro porušení optimistickou metodu souběžného je ověřit, jestli všechny původní hodnoty sloupce v řádku stále shodují s těmi nalezen v databázi. Zvažte například následující dotaz:  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 Chcete otestovat porušení optimistickou metodu souběžného při aktualizaci řádek v **tabulky1**, by vydat příkaz následující aktualizace:  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 Tak dlouho, dokud původní hodnoty shodují s hodnotami v databázi, se provádí aktualizace. Pokud byla hodnota změněna, aktualizace nebude řádek upravit, protože klauzule WHERE nebude možné najít shoda.  
  
 Všimněte si, že se doporučuje se vždy vrátit jedinečné hodnoty primárního klíče v dotazu. Předchozí příkaz UPDATE, jinak může aktualizovat více než jeden řádek, který nemusí být vašich představ.  
  
 Pokud sloupec na zdroj dat umožňuje hodnoty Null, musíte rozšířit vaše klauzule WHERE Zkontrolujte odpovídající odkaz s hodnotou null v místní tabulky a ve zdroji dat. Například následující příkaz UPDATE ověřuje, že odkaz s hodnotou null v místní řádku stále odpovídá odkaz na zdroj dat s hodnotou null, nebo hodnotu v místní řádku stále odpovídá hodnotě ve zdroji dat.  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 Můžete také použít obecnější kritéria při použití model optimistickou metodu souběžného. Například použití pouze primární klíčových sloupců v klauzuli WHERE způsobí, že data, která mají být přepsány bez ohledu na to, jestli ostatních sloupců byly aktualizovány od posledního dotazu. Klauzule WHERE můžete taky použít pouze na konkrétní sloupce, výsledkem dat přepsáním Pokud konkrétní pole byly aktualizovány od jejich poslední dotaz.  
  
### <a name="the-dataadapterrowupdated-event"></a>Událost DataAdapter.RowUpdated  
 **RowUpdated** události <xref:System.Data.Common.DataAdapter> objekt lze použít ve spojení s technik popsaných výše, k poskytování oznámení do vaší aplikace optimistickou metodu souběžného porušení zásad. **RowUpdated** dojde po každém pokusu o aktualizaci **změněné** řádek z **datovou sadu**. To umožňuje přidat kód pro zvláštní zpracování, včetně zpracováním, když dojde k výjimce, přidání informace o vlastní chybě, přidání logika opakovaných pokusů a tak dále. <xref:System.Data.Common.RowUpdatedEventArgs> Objektu vrátí **RecordsAffected** vlastnost obsahující počet řádků, které jsou ovlivněné příkaz konkrétní aktualizace pro upravené řádek v tabulce. Příkaz update chcete otestovat optimistickou metodu souběžného nastavením **RecordsAffected** vlastnost, výsledkem je, vrátí hodnotu 0 při došlo k porušení optimistickou metodu souběžného, protože žádné záznamy se aktualizovaly. Pokud je to tento případ, je vyvolána výjimka. **RowUpdated** událostí umožňuje zpracovávat tento výskyt a vyhnout se výjimka nastavením odpovídající **RowUpdatedEventArgs.Status** hodnotu, jako například  **UpdateStatus.SkipCurrentRow**. Další informace o **RowUpdated** událostí, najdete v části [zpracování události DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
 Volitelně můžete nastavit **DataAdapter.ContinueUpdateOnError** k **true**, před voláním **aktualizace**a reagovat na informace o chybě uložené v **RowError** vlastnost konkrétní řádek, kdy **aktualizace** byla dokončena. Další informace najdete v tématu [informace o chybě řádek](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).  
  
## <a name="optimistic-concurrency-example"></a>Příklad optimistickou metodu souběžného zpracování  
 Tady je jednoduchý příklad, který nastaví **vlastnost UpdateCommand** z **DataAdapter** chcete otestovat optimistickou metodu souběžného a použije je **RowUpdated** událostí k testování pro optimistickou metodu souběžného porušení. Když dojde k porušení optimistickou metodu souběžného, nastaví aplikace **RowError** řádku, který aktualizace byl vydán pro tak, aby odrážela porušení optimistickou metodu souběžného.  
  
 Všimněte si, že hodnoty parametru předána do klauzule WHERE příkazu UPDATE jsou namapované na **původní** hodnoty jejich odpovídajících sloupců.  
  
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
Dim parameter As SqlParameter = dataSet.UpdateCommand.Parameters.Add( _  
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
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName, connection);  
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
 [Načítání a upravovat Data v technologii ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Aktualizace zdrojů dat s DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [Informace o chybě řádek](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
