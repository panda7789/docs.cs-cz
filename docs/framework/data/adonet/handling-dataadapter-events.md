---
title: Zpracování událostí adaptéru dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: 3c2158e94f936dd2b28fe46310fd96df8dbc50fb
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525549"
---
# <a name="handling-dataadapter-events"></a>Zpracování událostí adaptéru dat
ADO.NET <xref:System.Data.Common.DataAdapter> zpřístupní tři události, které vám umožní reagovat na změny dat ve zdroji dat. Následující tabulka ukazuje `DataAdapter` události.  
  
|Událost|Popis|  
|-----------|-----------------|  
|`RowUpdating`|Operace UPDATE, INSERT nebo DELETE na řádek (voláním do jednoho z `Update` metody) má začít.|  
|`RowUpdated`|Operace UPDATE, INSERT nebo DELETE na řádek (voláním do jednoho z `Update` metody) je dokončena.|  
|`FillError`|Došlo k chybě během `Fill` operace.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating a RowUpdated metody  
 `RowUpdating` je aktivována před všechny aktualizace na řádek z <xref:System.Data.DataSet> ve zdroji dat byla zpracována. `RowUpdated` je aktivována po žádné aktualizace na řádek z `DataSet` ve zdroji dat byla zpracována. V důsledku toho můžete použít `RowUpdating` před ní dojde, poskytnout další zpracování při aktualizaci dojde, pokud chcete zachovat odkaz na aktualizovaný řádek, chcete-li zrušit aktuální aktualizaci a plán pro dávku zpracovat, aby mohly být zpracovány později změnit chování aktualizace , a tak dále. `RowUpdated` je užitečné pro zpracování chyb a výjimek, k nimž došlo při aktualizaci. Můžete přidat informace o chybě `DataSet`, stejně jako logiku opakování a tak dále.  
  
 <xref:System.Data.Common.RowUpdatingEventArgs> a <xref:System.Data.Common.RowUpdatedEventArgs> argumenty předané `RowUpdating` a `RowUpdated` události zahrnují následující: `Command` vlastnost, která odkazuje `Command` objektu se používá k provedení aktualizace; `Row` vlastnost, která odkazuje `DataRow` objekt, který obsahuje aktualizované informace; `StatementType` vlastnost, pro jaký typ aktualizace je prováděna; `TableMapping`, pokud je k dispozici; a `Status` operace.  
  
 Můžete použít `Status` požadované vlastnosti k určení, zda došlo k chybě během operace a pokud pro kontrolu akcí pro aktuální a výsledné řádky. Při výskytu události `Status` vlastnost rovná buď `Continue` nebo `ErrorsOccurred`. V následující tabulce jsou uvedeny hodnoty, na které můžete nastavit `Status` vlastnost, aby bylo možné řídit pozdějších akcích během aktualizace.  
  
|Stav|Popis|  
|------------|-----------------|  
|`Continue`|Pokračujte v provádění operace update.|  
|`ErrorsOccurred`|Přerušte operaci aktualizace a vyvolají výjimku.|  
|`SkipCurrentRow`|Ignorovat aktuální řádek a pokračovat v provádění operace update.|  
|`SkipAllRemainingRows`|Přerušte operaci aktualizace, ale ne vyvolává výjimku.|  
  
 Nastavení `Status` vlastnost `ErrorsOccurred` způsobí vyvolání výjimky. Můžete řídit, které se výjimka tak, že nastavíte `Errors` vlastnost na požadovanou výjimku. Pomocí jedné z hodnot pro `Status` zabraňuje vyvolané výjimky.  
  
 Můžete také použít `ContinueUpdateOnError` vlastnost zpracování chyb pro aktualizovat řádky. Pokud `DataAdapter.ContinueUpdateOnError` je `true`, že při aktualizaci řádků výsledků v k vyvolání výjimky, text výjimky je umístěn do `RowError` informace konkrétního řádku a zpracování bude pokračovat bez vyvolání výjimky. To umožňuje reagovat na chyby při `Update` rozdíl od dokončení `RowUpdated` událost, která umožňuje reagovat na chyby při výskytu chyby.  
  
 Následující příklad kódu ukazuje, jak přidání i odebrání obslužných rutin událostí. `RowUpdating` Obslužná rutina události zapíše protokolu všechny odstraněné záznamy s časovým razítkem. `RowUpdated` Obslužná rutina události přidá informace o chybě `RowError` vlastnosti řádku v `DataSet`, potlačí výjimku a pokračuje ve zpracování (zrcadlení chování `ContinueUpdateOnError`  =  `true`).  
  
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
  
## <a name="fillerror"></a>FillError  
 `DataAdapter` Problémy `FillError` událost, když dojde k chybě během `Fill` operace. Tento typ chyby dochází běžně, když jsou data v řádku přidávaný nelze převést na typ rozhraní .NET Framework bez ztrátu přesnosti.  
  
 Pokud dojde k chybě během `Fill` operaci, aktuální řádek se nepřidal do `DataTable`. `FillError` Události vám umožní vyřešit chyby a přidejte řádek, nebo řádku vyloučené ignorovat a pokračovat `Fill` operace.  
  
 `FillErrorEventArgs` Předán `FillError` událostí může obsahovat několik vlastností, které vám umožní reagovat na a řešení chyb. V následující tabulce jsou uvedeny vlastnosti `FillErrorEventArgs` objektu.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`Errors`|`Exception` , Ke kterým došlo.|  
|`DataTable`|`DataTable` Objektu je vyplněný, když došlo k chybě.|  
|`Values`|Pole objektů, který obsahuje hodnoty řádku přidávají, kdy došlo k chybě. Odkazy na řadová číslovka `Values` pole odpovídá pořadí odkazy na sloupce řádku přidává. Například `Values[0]` je hodnota, která se přidává jako první sloupec řádku.|  
|`Continue`|Umožňuje zvolit, jestli se má vyvolat výjimku. Nastavení `Continue` vlastnost `false` zastaví aktuální `Fill` operace a výjimka bude vyvolána výjimka. Nastavení `Continue` k `true` pokračuje `Fill` operace bez ohledu na chybu.|  
  
 Následující příklad kódu přidá obslužnou rutinu události pro `FillError` událost `DataAdapter`. V `FillError` příklad o kód události, které určuje, zda je potenciální ztráta přesnosti, poskytuje možnost reakce na výjimku.  
  
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
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Zpracování událostí datové sady](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [Zpracování událostí datové tabulky](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [Události](../../../../docs/standard/events/index.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
