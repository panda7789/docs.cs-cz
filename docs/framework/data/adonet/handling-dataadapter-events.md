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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: cc482e2508dedde88e40390b4e4ce3edcab8189d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="97149-102">Zpracování událostí DataAdapter</span><span class="sxs-lookup"><span data-stu-id="97149-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="97149-103">Technologie ADO.NET <xref:System.Data.Common.DataAdapter> zpřístupní tři události, které můžete použít reagovat na změny dat ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="97149-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="97149-104">Následující tabulce je zobrazena `DataAdapter` události.</span><span class="sxs-lookup"><span data-stu-id="97149-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="97149-105">Událost</span><span class="sxs-lookup"><span data-stu-id="97149-105">Event</span></span>|<span data-ttu-id="97149-106">Popis</span><span class="sxs-lookup"><span data-stu-id="97149-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="97149-107">Operace UPDATE, INSERT nebo DELETE na řádek (voláním mezi `Update` metody) je začít.</span><span class="sxs-lookup"><span data-stu-id="97149-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="97149-108">Operace UPDATE, INSERT nebo DELETE na řádek (voláním mezi `Update` metody) je dokončena.</span><span class="sxs-lookup"><span data-stu-id="97149-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="97149-109">Došlo k chybě během `Fill` operaci.</span><span class="sxs-lookup"><span data-stu-id="97149-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="97149-110">RowUpdating a RowUpdated</span><span class="sxs-lookup"><span data-stu-id="97149-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="97149-111">`RowUpdating`je vyvolána před všechny aktualizace na řádek z <xref:System.Data.DataSet> ve zdroji dat byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="97149-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="97149-112">`RowUpdated`je vyvolána po žádné aktualizace na řádek z `DataSet` ve zdroji dat byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="97149-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="97149-113">V důsledku toho můžete použít `RowUpdating` chcete upravit chování aktualizace, než se stane, znamená to zajistit další zpracování, když dojde k aktualizaci, chcete-li zachovat odkaz na aktualizované řádek, chcete-li zrušit aktuální aktualizace a plán pro dávku zpracovat na pozdější zpracování , a tak dále.</span><span class="sxs-lookup"><span data-stu-id="97149-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="97149-114">`RowUpdated`je užitečné pro zpracování chyb a výjimek, ke kterým došlo během aktualizace.</span><span class="sxs-lookup"><span data-stu-id="97149-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="97149-115">Můžete přidat informace o chybě do `DataSet`, stejně jako logika opakovaných pokusů a tak dále.</span><span class="sxs-lookup"><span data-stu-id="97149-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="97149-116"><xref:System.Data.Common.RowUpdatingEventArgs> a <xref:System.Data.Common.RowUpdatedEventArgs> bylo předáno `RowUpdating` a `RowUpdated` události zahrnují následující: `Command` vlastnost, která odkazuje `Command` objektu používá k provedení aktualizace; `Row` vlastnost, která odkazuje `DataRow` objekt obsahující aktualizované informace; `StatementType` vlastnost, pro jaký typ aktualizace je prováděna; `TableMapping`, pokud je k dispozici; a `Status` operace.</span><span class="sxs-lookup"><span data-stu-id="97149-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="97149-117">Můžete použít `Status` vlastnosti k určení, pokud došlo k chybě během operace a v případě potřeby k řízení akce u aktuálních a výsledné řádky.</span><span class="sxs-lookup"><span data-stu-id="97149-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="97149-118">Když dojde k události, `Status` vlastnost rovná buď `Continue` nebo `ErrorsOccurred`.</span><span class="sxs-lookup"><span data-stu-id="97149-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="97149-119">V následující tabulce jsou uvedeny hodnoty, na které můžete nastavit `Status` vlastnost, aby bylo možné řídit novější akcí během aktualizace.</span><span class="sxs-lookup"><span data-stu-id="97149-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="97149-120">Stav</span><span class="sxs-lookup"><span data-stu-id="97149-120">Status</span></span>|<span data-ttu-id="97149-121">Popis</span><span class="sxs-lookup"><span data-stu-id="97149-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="97149-122">Pokračujte v operaci aktualizace.</span><span class="sxs-lookup"><span data-stu-id="97149-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="97149-123">Zrušení operace aktualizace a způsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="97149-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="97149-124">Na aktuálním řádku ignorovat a pokračovat v provádění operace aktualizace.</span><span class="sxs-lookup"><span data-stu-id="97149-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="97149-125">Zrušení operace aktualizace, ale není vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="97149-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="97149-126">Nastavení `Status` vlastnost `ErrorsOccurred` způsobí, že vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="97149-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="97149-127">Můžete řídit, které se výjimka nastavením `Errors` vlastnost požadované výjimku.</span><span class="sxs-lookup"><span data-stu-id="97149-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="97149-128">Pomocí jedné z hodnot pro `Status` zabraňuje vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="97149-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="97149-129">Můžete také `ContinueUpdateOnError` vlastnost ke zpracování chyb pro aktualizovat řádky.</span><span class="sxs-lookup"><span data-stu-id="97149-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="97149-130">Pokud `DataAdapter.ContinueUpdateOnError` je `true`, že při aktualizaci výsledků řádek výjimku hlášeny, text výjimky je umístěn do `RowError` informace konkrétního řádku a zpracování pokračuje bez způsobení výjimky.</span><span class="sxs-lookup"><span data-stu-id="97149-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="97149-131">To umožňuje reagují na chyby při `Update` rozdíl k dokončení `RowUpdated` událost, která umožňuje reagovat na chyby, pokud je došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="97149-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="97149-132">Následující příklad kódu ukazuje, jak přidat i odebrat obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="97149-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="97149-133">`RowUpdating` Obslužné rutiny události zapíše protokolu všechny odstraněné záznamy s časové razítko.</span><span class="sxs-lookup"><span data-stu-id="97149-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="97149-134">`RowUpdated` Obslužné rutiny události přidá informace o chybě do `RowError` vlastnost řádku v `DataSet`, potlačí výjimku a pokračuje ve zpracování (zrcadlení chování `ContinueUpdateOnError`  =  `true`).</span><span class="sxs-lookup"><span data-stu-id="97149-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
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
  
## <a name="fillerror"></a><span data-ttu-id="97149-135">FillError</span><span class="sxs-lookup"><span data-stu-id="97149-135">FillError</span></span>  
 <span data-ttu-id="97149-136">`DataAdapter` Problémy `FillError` událost, když dojde k chybě během `Fill` operaci.</span><span class="sxs-lookup"><span data-stu-id="97149-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="97149-137">Tento typ chyby dochází běžně, když data v řádku, který chcete přidat nebylo možné převést na typ rozhraní .NET Framework bez některé ztrátu přesnosti.</span><span class="sxs-lookup"><span data-stu-id="97149-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="97149-138">Pokud dojde k chybě během `Fill` operaci, aktuální řádek není přidán do `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="97149-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="97149-139">`FillError` Událostí vám umožní přidat řádek, a vyřešte chybu nebo vyloučené řádek ignorovat a pokračovat `Fill` operace.</span><span class="sxs-lookup"><span data-stu-id="97149-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="97149-140">`FillErrorEventArgs` Předaný `FillError` událostí může obsahovat několik vlastností, které vám umožní reagovat na a vyřešte chyby.</span><span class="sxs-lookup"><span data-stu-id="97149-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="97149-141">V následující tabulce jsou uvedeny vlastnosti `FillErrorEventArgs` objektu.</span><span class="sxs-lookup"><span data-stu-id="97149-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="97149-142">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="97149-142">Property</span></span>|<span data-ttu-id="97149-143">Popis</span><span class="sxs-lookup"><span data-stu-id="97149-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="97149-144">`Exception` , Došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="97149-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="97149-145">`DataTable` Objektu má číslo, když se stala chyba.</span><span class="sxs-lookup"><span data-stu-id="97149-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="97149-146">Pole objektů, který obsahuje hodnoty řádku přidávají, když se stala chyba.</span><span class="sxs-lookup"><span data-stu-id="97149-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="97149-147">Řadová číslovka odkazuje z `Values` pole odpovídají odkazy na pořadí sloupců na řádek, který chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="97149-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="97149-148">Například `Values[0]` je hodnota, která přidala jako první sloupec řádek.</span><span class="sxs-lookup"><span data-stu-id="97149-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="97149-149">Umožňuje zvolit, zda má být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="97149-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="97149-150">Nastavení `Continue` vlastnost `false` se zastaví aktuální `Fill` operace a výjimku bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="97149-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="97149-151">Nastavení `Continue` k `true` pokračuje `Fill` operaci bez ohledu chyba.</span><span class="sxs-lookup"><span data-stu-id="97149-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="97149-152">Následující příklad kódu přidá obslužnou rutinu události pro `FillError` události `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="97149-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="97149-153">V `FillError` příklad o kód události, které určuje, zda je potenciální ztráta přesnosti, poskytuje možnost reagovat na výjimku.</span><span class="sxs-lookup"><span data-stu-id="97149-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97149-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="97149-154">See Also</span></span>  
 [<span data-ttu-id="97149-155">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="97149-155">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="97149-156">Zpracování událostí datové sady</span><span class="sxs-lookup"><span data-stu-id="97149-156">Handling DataSet Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [<span data-ttu-id="97149-157">Zpracování událostí datové tabulky</span><span class="sxs-lookup"><span data-stu-id="97149-157">Handling DataTable Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="97149-158">Události</span><span class="sxs-lookup"><span data-stu-id="97149-158">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="97149-159">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="97149-159">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
