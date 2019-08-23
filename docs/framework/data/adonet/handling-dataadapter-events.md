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
# <a name="handling-dataadapter-events"></a><span data-ttu-id="408c2-102">Zpracování událostí adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="408c2-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="408c2-103">ADO.NET <xref:System.Data.Common.DataAdapter> zpřístupňuje tři události, které můžete použít k reakci na změny dat ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="408c2-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="408c2-104">`DataAdapter` Události jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="408c2-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="408c2-105">Událost</span><span class="sxs-lookup"><span data-stu-id="408c2-105">Event</span></span>|<span data-ttu-id="408c2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="408c2-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="408c2-107">Bude zahájena operace aktualizace, vložení nebo odstranění na řádku (volání jedné z `Update` metod).</span><span class="sxs-lookup"><span data-stu-id="408c2-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="408c2-108">Operace aktualizace, vložení nebo odstranění na řádku (volání jedné z `Update` metod) je dokončena.</span><span class="sxs-lookup"><span data-stu-id="408c2-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="408c2-109">Během `Fill` operace došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="408c2-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="408c2-110">RowUpdating a RowUpdated metody Update</span><span class="sxs-lookup"><span data-stu-id="408c2-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="408c2-111">`RowUpdating`je aktivována před provedením jakékoli aktualizace řádku z, <xref:System.Data.DataSet> která byla zpracována ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="408c2-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="408c2-112">`RowUpdated`je aktivována po provedení jakékoli aktualizace řádku z, `DataSet` která byla zpracována ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="408c2-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="408c2-113">V důsledku toho můžete použít `RowUpdating` ke změně chování aktualizace před tím, než se stane, aby se zajistilo další zpracování, když dojde k aktualizaci, k uchování odkazu na aktualizovaný řádek, ke zrušení aktuální aktualizace a naplánování pro zpracování dávkového procesu později. a tak dále.</span><span class="sxs-lookup"><span data-stu-id="408c2-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="408c2-114">`RowUpdated`je vhodný pro reakci na chyby a výjimky, ke kterým dojde během aktualizace.</span><span class="sxs-lookup"><span data-stu-id="408c2-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="408c2-115">Do `DataSet`můžete přidat informace o chybě a také logiku opakování atd.</span><span class="sxs-lookup"><span data-stu-id="408c2-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="408c2-116">`RowUpdated` `Command` `Row` `Command` Argumenty <xref:System.Data.Common.RowUpdatingEventArgs> a<xref:System.Data.Common.RowUpdatedEventArgs> předané`RowUpdating` událostem a zahrnují následující: vlastnost, která odkazuje na objekt používaný k provedení aktualizace. vlastnost, která odkazuje `DataRow` na objekt obsahující aktualizované informace `StatementType` ; vlastnost pro typ aktualizace `TableMapping`, je-li k dispozici, a `Status` na operaci.</span><span class="sxs-lookup"><span data-stu-id="408c2-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="408c2-117">`Status` Vlastnost můžete použít k určení, zda během operace došlo k chybě, a v případě potřeby k řízení akcí proti aktuálnímu a výslednému řádku.</span><span class="sxs-lookup"><span data-stu-id="408c2-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="408c2-118">Pokud dojde k události, `Status` vlastnost se rovná buď `Continue` nebo `ErrorsOccurred`.</span><span class="sxs-lookup"><span data-stu-id="408c2-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="408c2-119">Následující tabulka uvádí hodnoty, na které můžete nastavit `Status` vlastnost, aby bylo možné řídit pozdější akce během aktualizace.</span><span class="sxs-lookup"><span data-stu-id="408c2-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="408c2-120">Stav</span><span class="sxs-lookup"><span data-stu-id="408c2-120">Status</span></span>|<span data-ttu-id="408c2-121">Popis</span><span class="sxs-lookup"><span data-stu-id="408c2-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="408c2-122">Pokračujte v operaci aktualizace.</span><span class="sxs-lookup"><span data-stu-id="408c2-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="408c2-123">Přerušte operaci aktualizace a vyvolejte výjimku.</span><span class="sxs-lookup"><span data-stu-id="408c2-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="408c2-124">Ignoruje aktuální řádek a pokračuje v operaci aktualizace.</span><span class="sxs-lookup"><span data-stu-id="408c2-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="408c2-125">Přerušte operaci aktualizace, ale Nevolejte výjimku.</span><span class="sxs-lookup"><span data-stu-id="408c2-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="408c2-126">Nastavení vlastnosti pro `ErrorsOccurred` způsobí vyvolání výjimky. `Status`</span><span class="sxs-lookup"><span data-stu-id="408c2-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="408c2-127">Můžete řídit, která výjimka je vyvolána, nastavením `Errors` vlastnosti na požadovanou výjimku.</span><span class="sxs-lookup"><span data-stu-id="408c2-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="408c2-128">Použití jedné z dalších hodnot pro `Status` brání vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="408c2-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="408c2-129">`ContinueUpdateOnError` Vlastnost můžete použít také ke zpracování chyb pro aktualizované řádky.</span><span class="sxs-lookup"><span data-stu-id="408c2-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="408c2-130">Pokud `DataAdapter.ContinueUpdateOnError` `RowError` je `true`v případě, že při aktualizaci řádku dojde k výjimce, je text výjimky umístěn do informací o konkrétním řádku a zpracování pokračuje bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="408c2-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="408c2-131">To vám umožní reagovat na chyby `Update` , až se dokončí, a to na rozdíl `RowUpdated` od události, což vám umožní reagovat na chyby, když dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="408c2-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="408c2-132">Následující ukázka kódu ukazuje, jak přidat a odebrat obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="408c2-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="408c2-133">Obslužná `RowUpdating` rutina události zapíše protokol všech odstraněných záznamů s časovým razítkem.</span><span class="sxs-lookup"><span data-stu-id="408c2-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="408c2-134"> =  `DataSet` `RowError` `true`Obslužná rutina `RowUpdated` události přidá informace o chybě do vlastnosti řádku v, potlačí výjimku `ContinueUpdateOnError`a pokračuje ve zpracování (zrcadlení chování).</span><span class="sxs-lookup"><span data-stu-id="408c2-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
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
  
## <a name="fillerror"></a><span data-ttu-id="408c2-135">FillError</span><span class="sxs-lookup"><span data-stu-id="408c2-135">FillError</span></span>  
 <span data-ttu-id="408c2-136">Vyvolá událost, `FillError` když dojde k chybě během `Fill` operace. `DataAdapter`</span><span class="sxs-lookup"><span data-stu-id="408c2-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="408c2-137">K tomuto typu chyby obvykle dochází, když nelze data v přidávaném řádku převést na typ .NET Framework bez ztráty přesnosti.</span><span class="sxs-lookup"><span data-stu-id="408c2-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="408c2-138">Pokud během `Fill` operace dojde k chybě, aktuální řádek není přidán `DataTable`do.</span><span class="sxs-lookup"><span data-stu-id="408c2-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="408c2-139">Událost umožňuje vyřešit chybu a přidat řádek nebo ignorovat vyloučený řádek a pokračovat v `Fill` operaci. `FillError`</span><span class="sxs-lookup"><span data-stu-id="408c2-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="408c2-140">Předaná`FillError` událost může obsahovat několik vlastností, které vám umožní reagovat na a vyřešit chyby. `FillErrorEventArgs`</span><span class="sxs-lookup"><span data-stu-id="408c2-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="408c2-141">V následující tabulce jsou uvedeny vlastnosti `FillErrorEventArgs` objektu.</span><span class="sxs-lookup"><span data-stu-id="408c2-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="408c2-142">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="408c2-142">Property</span></span>|<span data-ttu-id="408c2-143">Popis</span><span class="sxs-lookup"><span data-stu-id="408c2-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="408c2-144">K `Exception` nimž došlo.</span><span class="sxs-lookup"><span data-stu-id="408c2-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="408c2-145">Objekt `DataTable` , který je vyplněn, když došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="408c2-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="408c2-146">Pole objektů, které obsahují hodnoty řádku přidávaného při výskytu chyby.</span><span class="sxs-lookup"><span data-stu-id="408c2-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="408c2-147">Řadové odkazy `Values` v poli odpovídají řadovým odkazům na sloupce přidávaného řádku.</span><span class="sxs-lookup"><span data-stu-id="408c2-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="408c2-148">Například `Values[0]` je hodnota, která byla přidána jako první sloupec řádku.</span><span class="sxs-lookup"><span data-stu-id="408c2-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="408c2-149">Umožňuje zvolit, zda má být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="408c2-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="408c2-150">Nastavením vlastnosti na `false` zastavíte aktuální `Fill` operaci a vyvolá se výjimka. `Continue`</span><span class="sxs-lookup"><span data-stu-id="408c2-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="408c2-151">Nastavení `Continue` na `true` pokračování`Fill` operace bez ohledu na chybu.</span><span class="sxs-lookup"><span data-stu-id="408c2-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="408c2-152">Následující příklad kódu přidá obslužnou rutinu události pro `FillError` událost. `DataAdapter`</span><span class="sxs-lookup"><span data-stu-id="408c2-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="408c2-153">V kódu `FillError` události příklad určuje, zda existuje potenciál pro ztrátu přesnosti, a poskytuje příležitost reagovat na výjimku.</span><span class="sxs-lookup"><span data-stu-id="408c2-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="408c2-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="408c2-154">See also</span></span>

- [<span data-ttu-id="408c2-155">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="408c2-155">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="408c2-156">Zpracování událostí datové sady</span><span class="sxs-lookup"><span data-stu-id="408c2-156">Handling DataSet Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="408c2-157">Zpracování událostí datové tabulky</span><span class="sxs-lookup"><span data-stu-id="408c2-157">Handling DataTable Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="408c2-158">Události</span><span class="sxs-lookup"><span data-stu-id="408c2-158">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="408c2-159">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="408c2-159">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
