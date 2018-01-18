---
title: "Zpracování událostí DataAdapter"
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
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 71524de2edbedb24cacc6727654aac5be0a48bb7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="handling-dataadapter-events"></a>Zpracování událostí DataAdapter
Technologie ADO.NET <xref:System.Data.Common.DataAdapter> zpřístupní tři události, které můžete použít reagovat na změny dat ve zdroji dat. Následující tabulce je zobrazena `DataAdapter` události.  
  
|Událost|Popis|  
|-----------|-----------------|  
|`RowUpdating`|Operace UPDATE, INSERT nebo DELETE na řádek (voláním mezi `Update` metody) je začít.|  
|`RowUpdated`|Operace UPDATE, INSERT nebo DELETE na řádek (voláním mezi `Update` metody) je dokončena.|  
|`FillError`|Došlo k chybě během `Fill` operaci.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating a RowUpdated  
 `RowUpdating`je vyvolána před všechny aktualizace na řádek z <xref:System.Data.DataSet> ve zdroji dat byla zpracována. `RowUpdated`je vyvolána po žádné aktualizace na řádek z `DataSet` ve zdroji dat byla zpracována. V důsledku toho můžete použít `RowUpdating` chcete upravit chování aktualizace, než se stane, znamená to zajistit další zpracování, když dojde k aktualizaci, chcete-li zachovat odkaz na aktualizované řádek, chcete-li zrušit aktuální aktualizace a plán pro dávku zpracovat na pozdější zpracování , a tak dále. `RowUpdated`je užitečné pro zpracování chyb a výjimek, ke kterým došlo během aktualizace. Můžete přidat informace o chybě do `DataSet`, stejně jako logika opakovaných pokusů a tak dále.  
  
 <xref:System.Data.Common.RowUpdatingEventArgs> a <xref:System.Data.Common.RowUpdatedEventArgs> bylo předáno `RowUpdating` a `RowUpdated` události zahrnují následující: `Command` vlastnost, která odkazuje `Command` objektu používá k provedení aktualizace; `Row` vlastnost, která odkazuje `DataRow` objekt obsahující aktualizované informace; `StatementType` vlastnost, pro jaký typ aktualizace je prováděna; `TableMapping`, pokud je k dispozici; a `Status` operace.  
  
 Můžete použít `Status` vlastnosti k určení, pokud došlo k chybě během operace a v případě potřeby k řízení akce u aktuálních a výsledné řádky. Když dojde k události, `Status` vlastnost rovná buď `Continue` nebo `ErrorsOccurred`. V následující tabulce jsou uvedeny hodnoty, na které můžete nastavit `Status` vlastnost, aby bylo možné řídit novější akcí během aktualizace.  
  
|Stav|Popis|  
|------------|-----------------|  
|`Continue`|Pokračujte v operaci aktualizace.|  
|`ErrorsOccurred`|Zrušení operace aktualizace a způsobí výjimku.|  
|`SkipCurrentRow`|Na aktuálním řádku ignorovat a pokračovat v provádění operace aktualizace.|  
|`SkipAllRemainingRows`|Zrušení operace aktualizace, ale není vyvolána výjimka.|  
  
 Nastavení `Status` vlastnost `ErrorsOccurred` způsobí, že vyvolání výjimky. Můžete řídit, které se výjimka nastavením `Errors` vlastnost požadované výjimku. Pomocí jedné z hodnot pro `Status` zabraňuje vyvolání výjimky.  
  
 Můžete také `ContinueUpdateOnError` vlastnost ke zpracování chyb pro aktualizovat řádky. Pokud `DataAdapter.ContinueUpdateOnError` je `true`, že při aktualizaci výsledků řádek výjimku hlášeny, text výjimky je umístěn do `RowError` informace konkrétního řádku a zpracování pokračuje bez způsobení výjimky. To umožňuje reagují na chyby při `Update` rozdíl k dokončení `RowUpdated` událost, která umožňuje reagovat na chyby, pokud je došlo k chybě.  
  
 Následující příklad kódu ukazuje, jak přidat i odebrat obslužné rutiny událostí. `RowUpdating` Obslužné rutiny události zapíše protokolu všechny odstraněné záznamy s časové razítko. `RowUpdated` Obslužné rutiny události přidá informace o chybě do `RowError` vlastnost řádku v `DataSet`, potlačí výjimku a pokračuje ve zpracování (zrcadlení chování `ContinueUpdateOnError`  =  `true`).  
  
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
 `DataAdapter` Problémy `FillError` událost, když dojde k chybě během `Fill` operaci. Tento typ chyby dochází běžně, když data v řádku, který chcete přidat nebylo možné převést na typ rozhraní .NET Framework bez některé ztrátu přesnosti.  
  
 Pokud dojde k chybě během `Fill` operaci, aktuální řádek není přidán do `DataTable`. `FillError` Událostí vám umožní přidat řádek, a vyřešte chybu nebo vyloučené řádek ignorovat a pokračovat `Fill` operace.  
  
 `FillErrorEventArgs` Předaný `FillError` událostí může obsahovat několik vlastností, které vám umožní reagovat na a vyřešte chyby. V následující tabulce jsou uvedeny vlastnosti `FillErrorEventArgs` objektu.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`Errors`|`Exception` , Došlo k chybě.|  
|`DataTable`|`DataTable` Objektu má číslo, když se stala chyba.|  
|`Values`|Pole objektů, který obsahuje hodnoty řádku přidávají, když se stala chyba. Řadová číslovka odkazuje z `Values` pole odpovídají odkazy na pořadí sloupců na řádek, který chcete přidat. Například `Values[0]` je hodnota, která přidala jako první sloupec řádek.|  
|`Continue`|Umožňuje zvolit, zda má být vyvolána výjimka. Nastavení `Continue` vlastnost `false` se zastaví aktuální `Fill` operace a výjimku bude vyvolána. Nastavení `Continue` k `true` pokračuje `Fill` operaci bez ohledu chyba.|  
  
 Následující příklad kódu přidá obslužnou rutinu události pro `FillError` události `DataAdapter`. V `FillError` příklad o kód události, které určuje, zda je potenciální ztráta přesnosti, poskytuje možnost reagovat na výjimku.  
  
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
    args.RowError = _  
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
    args.RowError =   
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
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
