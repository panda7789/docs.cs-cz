---
title: Zpracování událostí adaptéru dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: a63e65289a51a7647270a978cec11ef6bc201e45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962758"
---
# <a name="handling-dataadapter-events"></a>Zpracování událostí adaptéru dat
ADO.NET <xref:System.Data.Common.DataAdapter> zpřístupňuje tři události, které můžete použít k reakci na změny dat ve zdroji dat. `DataAdapter` Události jsou uvedeny v následující tabulce.  
  
|Událost|Popis|  
|-----------|-----------------|  
|`RowUpdating`|Bude zahájena operace aktualizace, vložení nebo odstranění na řádku (volání jedné z `Update` metod).|  
|`RowUpdated`|Operace aktualizace, vložení nebo odstranění na řádku (volání jedné z `Update` metod) je dokončena.|  
|`FillError`|Během `Fill` operace došlo k chybě.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating a RowUpdated metody Update  
 `RowUpdating`je aktivována před provedením jakékoli aktualizace řádku z, <xref:System.Data.DataSet> která byla zpracována ve zdroji dat. `RowUpdated`je aktivována po provedení jakékoli aktualizace řádku z, `DataSet` která byla zpracována ve zdroji dat. V důsledku toho můžete použít `RowUpdating` ke změně chování aktualizace před tím, než se stane, aby se zajistilo další zpracování, když dojde k aktualizaci, k uchování odkazu na aktualizovaný řádek, ke zrušení aktuální aktualizace a naplánování pro zpracování dávkového procesu později. a tak dále. `RowUpdated`je vhodný pro reakci na chyby a výjimky, ke kterým dojde během aktualizace. Do `DataSet`můžete přidat informace o chybě a také logiku opakování atd.  
  
 `RowUpdated` `Command` `Row` `Command` Argumenty <xref:System.Data.Common.RowUpdatingEventArgs> a<xref:System.Data.Common.RowUpdatedEventArgs> předané`RowUpdating` událostem a zahrnují následující: vlastnost, která odkazuje na objekt používaný k provedení aktualizace. vlastnost, která odkazuje `DataRow` na objekt obsahující aktualizované informace `StatementType` ; vlastnost pro typ aktualizace `TableMapping`, je-li k dispozici, a `Status` na operaci.  
  
 `Status` Vlastnost můžete použít k určení, zda během operace došlo k chybě, a v případě potřeby k řízení akcí proti aktuálnímu a výslednému řádku. Pokud dojde k události, `Status` vlastnost se rovná buď `Continue` nebo `ErrorsOccurred`. Následující tabulka uvádí hodnoty, na které můžete nastavit `Status` vlastnost, aby bylo možné řídit pozdější akce během aktualizace.  
  
|Stav|Popis|  
|------------|-----------------|  
|`Continue`|Pokračujte v operaci aktualizace.|  
|`ErrorsOccurred`|Přerušte operaci aktualizace a vyvolejte výjimku.|  
|`SkipCurrentRow`|Ignoruje aktuální řádek a pokračuje v operaci aktualizace.|  
|`SkipAllRemainingRows`|Přerušte operaci aktualizace, ale Nevolejte výjimku.|  
  
 Nastavení vlastnosti pro `ErrorsOccurred` způsobí vyvolání výjimky. `Status` Můžete řídit, která výjimka je vyvolána, nastavením `Errors` vlastnosti na požadovanou výjimku. Použití jedné z dalších hodnot pro `Status` brání vyvolání výjimky.  
  
 `ContinueUpdateOnError` Vlastnost můžete použít také ke zpracování chyb pro aktualizované řádky. Pokud `DataAdapter.ContinueUpdateOnError` `RowError` je `true`v případě, že při aktualizaci řádku dojde k výjimce, je text výjimky umístěn do informací o konkrétním řádku a zpracování pokračuje bez vyvolání výjimky. To vám umožní reagovat na chyby `Update` , až se dokončí, a to na rozdíl `RowUpdated` od události, což vám umožní reagovat na chyby, když dojde k chybě.  
  
 Následující ukázka kódu ukazuje, jak přidat a odebrat obslužné rutiny událostí. Obslužná `RowUpdating` rutina události zapíše protokol všech odstraněných záznamů s časovým razítkem.  =  `DataSet` `RowError` `true`Obslužná rutina `RowUpdated` události přidá informace o chybě do vlastnosti řádku v, potlačí výjimku `ContinueUpdateOnError`a pokračuje ve zpracování (zrcadlení chování).  
  
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
 Vyvolá událost, `FillError` když dojde k chybě během `Fill` operace. `DataAdapter` K tomuto typu chyby obvykle dochází, když nelze data v přidávaném řádku převést na typ .NET Framework bez ztráty přesnosti.  
  
 Pokud během `Fill` operace dojde k chybě, aktuální řádek není přidán `DataTable`do. Událost umožňuje vyřešit chybu a přidat řádek nebo ignorovat vyloučený řádek a pokračovat v `Fill` operaci. `FillError`  
  
 Předaná`FillError` událost může obsahovat několik vlastností, které vám umožní reagovat na a vyřešit chyby. `FillErrorEventArgs` V následující tabulce jsou uvedeny vlastnosti `FillErrorEventArgs` objektu.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`Errors`|K `Exception` nimž došlo.|  
|`DataTable`|Objekt `DataTable` , který je vyplněn, když došlo k chybě.|  
|`Values`|Pole objektů, které obsahují hodnoty řádku přidávaného při výskytu chyby. Řadové odkazy `Values` v poli odpovídají řadovým odkazům na sloupce přidávaného řádku. Například `Values[0]` je hodnota, která byla přidána jako první sloupec řádku.|  
|`Continue`|Umožňuje zvolit, zda má být vyvolána výjimka. Nastavením vlastnosti na `false` zastavíte aktuální `Fill` operaci a vyvolá se výjimka. `Continue` Nastavení `Continue` na `true` pokračování`Fill` operace bez ohledu na chybu.|  
  
 Následující příklad kódu přidá obslužnou rutinu události pro `FillError` událost. `DataAdapter` V kódu `FillError` události příklad určuje, zda existuje potenciál pro ztrátu přesnosti, a poskytuje příležitost reagovat na výjimku.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Zpracování událostí datové sady](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)
- [Zpracování událostí datové tabulky](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [Události](../../../standard/events/index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
