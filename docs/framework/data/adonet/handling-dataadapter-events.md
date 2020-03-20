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
# <a name="handling-dataadapter-events"></a><span data-ttu-id="5e944-102">Zpracování událostí adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="5e944-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="5e944-103">ADO.NET <xref:System.Data.Common.DataAdapter> zpřístupňuje tři události, které můžete použít k reakci na změny provedené v datech ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="5e944-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="5e944-104">V následující tabulce `DataAdapter` jsou uvedeny události.</span><span class="sxs-lookup"><span data-stu-id="5e944-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="5e944-105">Událost</span><span class="sxs-lookup"><span data-stu-id="5e944-105">Event</span></span>|<span data-ttu-id="5e944-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5e944-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="5e944-107">Operace UPDATE, INSERT nebo DELETE na řádku (voláním `Update` jedné z metod) se chystá zahájit.</span><span class="sxs-lookup"><span data-stu-id="5e944-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="5e944-108">Operace UPDATE, INSERT nebo DELETE na řádku (voláním `Update` jedné z metod) je dokončena.</span><span class="sxs-lookup"><span data-stu-id="5e944-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="5e944-109">Během operace došlo `Fill` k chybě.</span><span class="sxs-lookup"><span data-stu-id="5e944-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="5e944-110">RowUpdating a ŘádekAktualizováno</span><span class="sxs-lookup"><span data-stu-id="5e944-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="5e944-111">`RowUpdating`je aktivována před jakoukoli aktualizaci řádku z <xref:System.Data.DataSet> byl zpracován ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="5e944-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="5e944-112">`RowUpdated`je aktivována po jakékoli aktualizaci řádku z `DataSet` byl zpracován ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="5e944-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="5e944-113">V důsledku toho můžete `RowUpdating` použít k úpravě chování aktualizace dříve, než k ní dojde, poskytnout další zpracování při aktualizaci dojde, zachovat odkaz na aktualizovaný řádek, zrušit aktuální aktualizaci a naplánovat pro dávkový proces, který má být zpracován později a tak dále.</span><span class="sxs-lookup"><span data-stu-id="5e944-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="5e944-114">`RowUpdated`je užitečné pro odpovědi na chyby a výjimky, ke kterým dochází během aktualizace.</span><span class="sxs-lookup"><span data-stu-id="5e944-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="5e944-115">Můžete přidat informace o `DataSet`chybě , stejně jako logiku opakování a tak dále.</span><span class="sxs-lookup"><span data-stu-id="5e944-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="5e944-116"><xref:System.Data.Common.RowUpdatingEventArgs> Argumenty <xref:System.Data.Common.RowUpdatedEventArgs> a předané `RowUpdating` `RowUpdated` událostem a zahrnují `Command` následující: vlastnost, která odkazuje na `Command` objekt používaný k provedení aktualizace; `Row` vlastnost, která odkazuje `DataRow` na objekt obsahující aktualizované informace; `StatementType` vlastnost pro jaký typ aktualizace se provádí; `TableMapping`, případně; `Status` a operace.</span><span class="sxs-lookup"><span data-stu-id="5e944-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="5e944-117">`Status` Vlastnost můžete použít k určení, pokud došlo k chybě během operace a v případě potřeby k řízení akce proti aktuální a výsledné řádky.</span><span class="sxs-lookup"><span data-stu-id="5e944-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="5e944-118">Když dojde k události, `Status` vlastnost `Continue` se `ErrorsOccurred`rovná buď nebo .</span><span class="sxs-lookup"><span data-stu-id="5e944-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="5e944-119">V následující tabulce jsou uvedeny hodnoty, na které můžete nastavit `Status` vlastnost, abyste mohli řídit pozdější akce během aktualizace.</span><span class="sxs-lookup"><span data-stu-id="5e944-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="5e944-120">Status</span><span class="sxs-lookup"><span data-stu-id="5e944-120">Status</span></span>|<span data-ttu-id="5e944-121">Popis</span><span class="sxs-lookup"><span data-stu-id="5e944-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="5e944-122">Pokračujte v operaci aktualizace.</span><span class="sxs-lookup"><span data-stu-id="5e944-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="5e944-123">Přerušit operaci aktualizace a vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="5e944-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="5e944-124">Ignorujte aktuální řádek a pokračujte v operaci aktualizace.</span><span class="sxs-lookup"><span data-stu-id="5e944-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="5e944-125">Přerušit operaci aktualizace, ale nevyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="5e944-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="5e944-126">Nastavení `Status` vlastnosti `ErrorsOccurred` způsobí, že výjimku vyvolat.</span><span class="sxs-lookup"><span data-stu-id="5e944-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="5e944-127">Můžete určit, která výjimka je `Errors` vyvolána nastavením vlastnosti na požadovanou výjimku.</span><span class="sxs-lookup"><span data-stu-id="5e944-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="5e944-128">Použití jedné z dalších hodnot pro `Status` zabraňuje vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="5e944-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="5e944-129">`ContinueUpdateOnError` Vlastnost můžete také použít ke zpracování chyb pro aktualizované řádky.</span><span class="sxs-lookup"><span data-stu-id="5e944-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="5e944-130">Pokud `DataAdapter.ContinueUpdateOnError` `true`je , pokud aktualizace řádku má za následek vyvolání výjimky, text `RowError` výjimky je umístěn do informací o konkrétní řádek a zpracování pokračuje bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="5e944-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="5e944-131">To umožňuje reagovat na `Update` chyby po dokončení, `RowUpdated` na rozdíl od události, která umožňuje reagovat na chyby, když dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="5e944-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="5e944-132">Následující ukázka kódu ukazuje, jak přidat i odebrat obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="5e944-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="5e944-133">Obslužná rutina `RowUpdating` události zapíše protokol všech odstraněných záznamů s časovým razítkem.</span><span class="sxs-lookup"><span data-stu-id="5e944-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="5e944-134">Obslužná `RowUpdated` rutina `RowError` události přidá informace `DataSet`o chybě do vlastnosti řádku v oblasti `ContinueUpdateOnError`  =  `true`, potlačí výjimku a pokračuje ve zpracování (zrcadlení chování ).</span><span class="sxs-lookup"><span data-stu-id="5e944-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
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
  
## <a name="fillerror"></a><span data-ttu-id="5e944-135">Chyba fill</span><span class="sxs-lookup"><span data-stu-id="5e944-135">FillError</span></span>  
 <span data-ttu-id="5e944-136">Problémy `DataAdapter` `FillError` události, když dojde k `Fill` chybě během operace.</span><span class="sxs-lookup"><span data-stu-id="5e944-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="5e944-137">K tomuto typu chyby obvykle dochází, když data v řádku, který je přidáván nelze převést na typ rozhraní .NET Framework bez ztráty přesnosti.</span><span class="sxs-lookup"><span data-stu-id="5e944-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="5e944-138">Pokud během `Fill` operace dojde k chybě, aktuální řádek `DataTable`není přidán do .</span><span class="sxs-lookup"><span data-stu-id="5e944-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="5e944-139">Událost `FillError` umožňuje vyřešit chybu a přidat řádek nebo ignorovat vyloučený řádek `Fill` a pokračovat v operaci.</span><span class="sxs-lookup"><span data-stu-id="5e944-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="5e944-140">Předáno `FillErrorEventArgs` `FillError` události může obsahovat několik vlastností, které umožňují reagovat a řešit chyby.</span><span class="sxs-lookup"><span data-stu-id="5e944-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="5e944-141">V následující tabulce jsou `FillErrorEventArgs` uvedeny vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="5e944-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="5e944-142">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="5e944-142">Property</span></span>|<span data-ttu-id="5e944-143">Popis</span><span class="sxs-lookup"><span data-stu-id="5e944-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="5e944-144">To, `Exception` co se stalo.</span><span class="sxs-lookup"><span data-stu-id="5e944-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="5e944-145">Objekt, `DataTable` který se vyplňuje, když došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="5e944-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="5e944-146">Pole objektů, které obsahuje hodnoty řádku, který je přidáván, když došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="5e944-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="5e944-147">Ordinální odkazy `Values` pole odpovídají řadové odkazy na sloupce řádku, které jsou přidávány.</span><span class="sxs-lookup"><span data-stu-id="5e944-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="5e944-148">Například `Values[0]` je hodnota, která byla přidána jako první sloupec řádku.</span><span class="sxs-lookup"><span data-stu-id="5e944-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="5e944-149">Umožňuje zvolit, zda chcete vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="5e944-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="5e944-150">Nastavení `Continue` vlastnosti `false` zastaví aktuální `Fill` operaci a bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="5e944-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="5e944-151">Nastavení `Continue` `true` pokračovat `Fill` v operaci i přes chybu.</span><span class="sxs-lookup"><span data-stu-id="5e944-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="5e944-152">Následující příklad kódu přidá obslužnou rutinu `FillError` události pro událost `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="5e944-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="5e944-153">V `FillError` kódu události příklad určuje, zda existuje potenciál pro ztrátu přesnosti, poskytuje možnost reagovat na výjimku.</span><span class="sxs-lookup"><span data-stu-id="5e944-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5e944-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e944-154">See also</span></span>

- [<span data-ttu-id="5e944-155">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="5e944-155">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="5e944-156">Zpracování událostí datové sady</span><span class="sxs-lookup"><span data-stu-id="5e944-156">Handling DataSet Events</span></span>](./dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="5e944-157">Zpracování událostí datové tabulky</span><span class="sxs-lookup"><span data-stu-id="5e944-157">Handling DataTable Events</span></span>](./dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="5e944-158">Akce</span><span class="sxs-lookup"><span data-stu-id="5e944-158">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="5e944-159">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5e944-159">ADO.NET Overview</span></span>](ado-net-overview.md)
