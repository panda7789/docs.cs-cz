---
title: Zpracování událostí adaptéru dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: d01198d158c4e1c64f12e8a0756c3d4e599fce74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149541"
---
# <a name="handling-dataadapter-events"></a>Zpracování událostí adaptéru dat
ADO.NET <xref:System.Data.Common.DataAdapter> zpřístupňuje tři události, které můžete použít k reakci na změny provedené v datech ve zdroji dat. V následující tabulce `DataAdapter` jsou uvedeny události.  
  
|Událost|Popis|  
|-----------|-----------------|  
|`RowUpdating`|Operace UPDATE, INSERT nebo DELETE na řádku (voláním `Update` jedné z metod) se chystá zahájit.|  
|`RowUpdated`|Operace UPDATE, INSERT nebo DELETE na řádku (voláním `Update` jedné z metod) je dokončena.|  
|`FillError`|Během operace došlo `Fill` k chybě.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating a ŘádekAktualizováno  
 `RowUpdating`je aktivována před jakoukoli aktualizaci řádku z <xref:System.Data.DataSet> byl zpracován ve zdroji dat. `RowUpdated`je aktivována po jakékoli aktualizaci řádku z `DataSet` byl zpracován ve zdroji dat. V důsledku toho můžete `RowUpdating` použít k úpravě chování aktualizace dříve, než k ní dojde, poskytnout další zpracování při aktualizaci dojde, zachovat odkaz na aktualizovaný řádek, zrušit aktuální aktualizaci a naplánovat pro dávkový proces, který má být zpracován později a tak dále. `RowUpdated`je užitečné pro odpovědi na chyby a výjimky, ke kterým dochází během aktualizace. Můžete přidat informace o `DataSet`chybě , stejně jako logiku opakování a tak dále.  
  
 <xref:System.Data.Common.RowUpdatingEventArgs> Argumenty <xref:System.Data.Common.RowUpdatedEventArgs> a předané `RowUpdating` `RowUpdated` událostem a zahrnují `Command` následující: vlastnost, která odkazuje na `Command` objekt používaný k provedení aktualizace; `Row` vlastnost, která odkazuje `DataRow` na objekt obsahující aktualizované informace; `StatementType` vlastnost pro jaký typ aktualizace se provádí; `TableMapping`, případně; `Status` a operace.  
  
 `Status` Vlastnost můžete použít k určení, pokud došlo k chybě během operace a v případě potřeby k řízení akce proti aktuální a výsledné řádky. Když dojde k události, `Status` vlastnost `Continue` se `ErrorsOccurred`rovná buď nebo . V následující tabulce jsou uvedeny hodnoty, na které můžete nastavit `Status` vlastnost, abyste mohli řídit pozdější akce během aktualizace.  
  
|Status|Popis|  
|------------|-----------------|  
|`Continue`|Pokračujte v operaci aktualizace.|  
|`ErrorsOccurred`|Přerušit operaci aktualizace a vyvolat výjimku.|  
|`SkipCurrentRow`|Ignorujte aktuální řádek a pokračujte v operaci aktualizace.|  
|`SkipAllRemainingRows`|Přerušit operaci aktualizace, ale nevyvolat výjimku.|  
  
 Nastavení `Status` vlastnosti `ErrorsOccurred` způsobí, že výjimku vyvolat. Můžete určit, která výjimka je `Errors` vyvolána nastavením vlastnosti na požadovanou výjimku. Použití jedné z dalších hodnot pro `Status` zabraňuje vyvolání výjimky.  
  
 `ContinueUpdateOnError` Vlastnost můžete také použít ke zpracování chyb pro aktualizované řádky. Pokud `DataAdapter.ContinueUpdateOnError` `true`je , pokud aktualizace řádku má za následek vyvolání výjimky, text `RowError` výjimky je umístěn do informací o konkrétní řádek a zpracování pokračuje bez vyvolání výjimky. To umožňuje reagovat na `Update` chyby po dokončení, `RowUpdated` na rozdíl od události, která umožňuje reagovat na chyby, když dojde k chybě.  
  
 Následující ukázka kódu ukazuje, jak přidat i odebrat obslužné rutiny událostí. Obslužná rutina `RowUpdating` události zapíše protokol všech odstraněných záznamů s časovým razítkem. Obslužná `RowUpdated` rutina `RowError` události přidá informace `DataSet`o chybě do vlastnosti řádku v oblasti `ContinueUpdateOnError`  =  `true`, potlačí výjimku a pokračuje ve zpracování (zrcadlení chování ).  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a>Chyba fill  
 Problémy `DataAdapter` `FillError` události, když dojde k `Fill` chybě během operace. K tomuto typu chyby obvykle dochází, když data v řádku, který je přidáván nelze převést na typ rozhraní .NET Framework bez ztráty přesnosti.  
  
 Pokud během `Fill` operace dojde k chybě, aktuální řádek `DataTable`není přidán do . Událost `FillError` umožňuje vyřešit chybu a přidat řádek nebo ignorovat vyloučený řádek `Fill` a pokračovat v operaci.  
  
 Předáno `FillErrorEventArgs` `FillError` události může obsahovat několik vlastností, které umožňují reagovat a řešit chyby. V následující tabulce jsou `FillErrorEventArgs` uvedeny vlastnosti objektu.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`Errors`|To, `Exception` co se stalo.|  
|`DataTable`|Objekt, `DataTable` který se vyplňuje, když došlo k chybě.|  
|`Values`|Pole objektů, které obsahuje hodnoty řádku, který je přidáván, když došlo k chybě. Ordinální odkazy `Values` pole odpovídají řadové odkazy na sloupce řádku, které jsou přidávány. Například `Values[0]` je hodnota, která byla přidána jako první sloupec řádku.|  
|`Continue`|Umožňuje zvolit, zda chcete vyvolat výjimku. Nastavení `Continue` vlastnosti `false` zastaví aktuální `Fill` operaci a bude vyvolána výjimka. Nastavení `Continue` `true` pokračovat `Fill` v operaci i přes chybu.|  
  
 Následující příklad kódu přidá obslužnou rutinu `FillError` události pro událost `DataAdapter`. V `FillError` kódu události příklad určuje, zda existuje potenciál pro ztrátu přesnosti, poskytuje možnost reagovat na výjimku.  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    myRow.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    myRow.RowError =
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Zpracování událostí datové sady](./dataset-datatable-dataview/handling-dataset-events.md)
- [Zpracování událostí datové tabulky](./dataset-datatable-dataview/handling-datatable-events.md)
- [Akce](../../../standard/events/index.md)
- [Přehled ADO.NET](ado-net-overview.md)
