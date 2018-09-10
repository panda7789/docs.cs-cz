---
title: Aktualizace zdrojů dat pomocí adaptérů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: c334fb695f80bcac19167e9347d27d40f5139580
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038254"
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="8f36a-102">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="8f36a-102">Updating Data Sources with DataAdapters</span></span>
<span data-ttu-id="8f36a-103">`Update` Metodu <xref:System.Data.Common.DataAdapter> je volána k vyřešení změn z <xref:System.Data.DataSet> zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="8f36a-103">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="8f36a-104">`Update` Metoda, třeba `Fill` metoda, přebírá jako argumenty instance `DataSet`a volitelně <xref:System.Data.DataTable> objektu nebo `DataTable` název.</span><span class="sxs-lookup"><span data-stu-id="8f36a-104">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="8f36a-105">`DataSet` Instance je `DataSet` , která obsahuje změny, které byly provedeny, a `DataTable` identifikuje tabulky, ze kterých se mají obnovit změny.</span><span class="sxs-lookup"><span data-stu-id="8f36a-105">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="8f36a-106">Pokud ne `DataTable` je zadán první `DataTable` v `DataSet` se používá.</span><span class="sxs-lookup"><span data-stu-id="8f36a-106">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>  
  
 <span data-ttu-id="8f36a-107">Při volání `Update` metody `DataAdapter` analyzuje, které byly provedeny změny a spuštěn příslušný příkaz (vložení, aktualizace nebo odstranění).</span><span class="sxs-lookup"><span data-stu-id="8f36a-107">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="8f36a-108">Když `DataAdapter` dojde ke změně <xref:System.Data.DataRow>, použije <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, nebo <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> zpracovat změny.</span><span class="sxs-lookup"><span data-stu-id="8f36a-108">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="8f36a-109">Můžete tak maximalizovat výkon vaší aplikace ADO.NET zadáním syntaxe příkazu v době návrhu a kde je to možné, pomocí uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="8f36a-109">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="8f36a-110">Je nutné explicitně nastavit příkazy před voláním `Update`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-110">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="8f36a-111">Pokud `Update` nazývá a příslušný příkaz pro konkrétní aktualizace neexistuje (třeba ne `DeleteCommand` pro odstraněné řádky), je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8f36a-111">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f36a-112">Pokud chcete upravit nebo odstranit data s využitím používáte uložených procedur SQL serveru `DataAdapter`, ujistěte se, že SET NOCOUNT na nepoužívejte v definici uloženou proceduru.</span><span class="sxs-lookup"><span data-stu-id="8f36a-112">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="8f36a-113">To způsobí, že počet ovlivněných řádků vrácena rovno nule, který `DataAdapter` interpretuje jako ke konfliktu souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="8f36a-113">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="8f36a-114">V tomto případě <xref:System.Data.DBConcurrencyException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8f36a-114">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
 <span data-ttu-id="8f36a-115">Parametry příkazu je možné zadat vstupní a výstupní hodnoty pro příkaz SQL nebo uloženou proceduru pro každý řádek upravený `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-115">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="8f36a-116">Další informace najdete v tématu [parametry adaptéru dat](../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8f36a-116">For more information, see [DataAdapter Parameters](../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f36a-117">Je důležité pochopit rozdíl mezi odstranění řádku v <xref:System.Data.DataTable> a odebrání řádku.</span><span class="sxs-lookup"><span data-stu-id="8f36a-117">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="8f36a-118">Při volání `Remove` nebo `RemoveAt` metoda řádku je odebrán okamžitě.</span><span class="sxs-lookup"><span data-stu-id="8f36a-118">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="8f36a-119">Žádné odpovídající řádky v back-endového zdroje dat nebude mít vliv, pokud pak předáte `DataTable` nebo `DataSet` k `DataAdapter` a volat `Update`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-119">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="8f36a-120">Při použití `Delete` metody řádku zůstává ve `DataTable` a je označená k odstranění.</span><span class="sxs-lookup"><span data-stu-id="8f36a-120">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="8f36a-121">Pokud pak předáte `DataTable` nebo `DataSet` k `DataAdapter` a volat `Update`, odpovídající řádek v back-endového zdroje dat se odstraní.</span><span class="sxs-lookup"><span data-stu-id="8f36a-121">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>  
  
 <span data-ttu-id="8f36a-122">Pokud vaše `DataTable` mapuje nebo je generován z jedné tabulky databáze, které můžete využít <xref:System.Data.Common.DbCommandBuilder> objektu automaticky generuje `DeleteCommand`, `InsertCommand`, a `UpdateCommand` objekty pro `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-122">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="8f36a-123">Další informace najdete v tématu [generování příkazů s CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="8f36a-123">For more information, see [Generating Commands with CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).</span></span>  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="8f36a-124">Použití UpdatedRowSource k mapování hodnot do datové sady</span><span class="sxs-lookup"><span data-stu-id="8f36a-124">Using UpdatedRowSource to Map Values to a DataSet</span></span>  
 <span data-ttu-id="8f36a-125">Můžete řídit, jak jsou mapovány hodnot vrácených ze zdroje dat zpět do `DataTable` následující volání metody Update `DataAdapter`, s použitím <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> vlastnost <xref:System.Data.Common.DbCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="8f36a-125">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="8f36a-126">Tím, že nastavíte `UpdatedRowSource` vlastnost na jednu z <xref:System.Data.UpdateRowSource> hodnot výčtu, můžete řídit, zda výstupní parametry vrácené `DataAdapter` příkazy jsou ignorována nebo použitý pro změněné řádky v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-126">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="8f36a-127">Můžete také určit, zda vrátí první řádek (pokud existuje) je použitý pro změněné řádky v `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-127">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>  
  
 <span data-ttu-id="8f36a-128">Následující tabulka popisuje různé hodnoty `UpdateRowSource` výčet a způsob, jakým ovlivňují chování použít s příkaz `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-128">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>  
  
|<span data-ttu-id="8f36a-129">Výčet UpdatedRowSource</span><span class="sxs-lookup"><span data-stu-id="8f36a-129">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="8f36a-130">Popis</span><span class="sxs-lookup"><span data-stu-id="8f36a-130">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="8f36a-131">Výstupní parametry a první řádek je sada výsledků dotazu vrácená může mapovat na změněný řádek v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-131">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="8f36a-132">Změněný řádek v lze mapovat pouze data v prvním řádku je sada výsledků dotazu vrácená `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-132">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|  
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="8f36a-133">Žádné výstupní parametry nebo řádky vrácené výsledné sady jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="8f36a-133">Any output parameters or rows of a returned result set are ignored.</span></span>|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="8f36a-134">Pouze výstupní parametry lze mapovat na změněný řádek v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-134">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|  
  
 <span data-ttu-id="8f36a-135">`Update` Metoda vyřeší, vaše změny zpět do zdroje dat, ale ostatní klienty může mít upravená data ve zdroji dat od posledního jste vyplnili `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-135">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="8f36a-136">Aktualizujte vaše `DataSet` s aktuálními údaji, použijte `DataAdapter` a `Fill` metoda.</span><span class="sxs-lookup"><span data-stu-id="8f36a-136">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="8f36a-137">Nové řádky se přidají do tabulky a aktualizované informace budou zahrnuta do existující řádky.</span><span class="sxs-lookup"><span data-stu-id="8f36a-137">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="8f36a-138">`Fill` Metody Určuje, jestli se přidá nový řádek nebo aktualizuje existující řádek porovnáním hodnoty primárního klíče pro řádky v tabulce `DataSet` a řádků vrácených `SelectCommand`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-138">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="8f36a-139">Pokud `Fill` metoda zjistí hodnotu primárního klíče pro řádek v `DataSet` odpovídající hodnotu primárního klíče z řádků ve výsledcích vrácených `SelectCommand`, aktualizuje existující řádek s informacemi z řádků vrácených `SelectCommand`a nastaví <xref:System.Data.DataRow.RowState%2A> existující řádku `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-139">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="8f36a-140">Pokud řádek vrácený `SelectCommand` má hodnotu primárního klíče, který neodpovídá žádnému hodnoty primárního klíče řádků v `DataSet`, `Fill` metoda přidá nový řádek s `RowState` z `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-140">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f36a-141">Pokud `SelectCommand` vrátí výsledky z vnějšího spojení, `DataAdapter` nenastaví `PrimaryKey` hodnoty pro výsledné `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-141">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="8f36a-142">Je nutné definovat `PrimaryKey` sobě a ujistěte se, že jsou správně přeložit duplicitní řádky.</span><span class="sxs-lookup"><span data-stu-id="8f36a-142">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="8f36a-143">Další informace najdete v tématu [definování primárních klíčů](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="8f36a-143">For more information, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="8f36a-144">Zpracování výjimek, které mohou nastat při volání `Update` metodu, můžete použít `RowUpdated` události a reagovat na chyby aktualizace řádku, jak se objeví (naleznete v tématu [zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), nebo můžete nastavit `DataAdapter.ContinueUpdateOnError` k `true` před voláním `Update`a reagovat na chybové informace uložené v `RowError` vlastnosti konkrétního řádku po dokončení aktualizace (naleznete v tématu [informace o chybě řádek](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).</span><span class="sxs-lookup"><span data-stu-id="8f36a-144">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).</span></span>  
  
 <span data-ttu-id="8f36a-145">**Poznámka:** volání `AcceptChanges` na `DataSet`, `DataTable`, nebo `DataRow` způsobí, že všechny `Original` hodnoty `DataRow` chcete ji přepsat `Current` hodnoty `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-145">**Note** Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="8f36a-146">Pokud byly změněny hodnoty polí, které identifikují řádky jako jedinečné, po volání `AcceptChanges` `Original` hodnoty se už nebude odpovídat hodnotám ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="8f36a-146">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="8f36a-147">`AcceptChanges` je volána automaticky pro každý řádek při volání metody Update `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-147">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="8f36a-148">Při volání metody Update první zadaný v nastavení můžete zachovat původní hodnoty `AcceptChangesDuringUpdate` vlastnost `DataAdapter` na hodnotu false, případně můžete vytvořit obslužnou rutinu události pro `RowUpdated` událostí a nastavení <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> k <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span><span class="sxs-lookup"><span data-stu-id="8f36a-148">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="8f36a-149">Další informace najdete v tématu [slučování obsahu datové sady](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) a [zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="8f36a-149">For more information, see [Merging DataSet Contents](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f36a-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f36a-150">Example</span></span>  
 <span data-ttu-id="8f36a-151">Následující příklady ukazují, jak provádět aktualizace pro upravené řádky explicitním nastavením `UpdateCommand` z `DataAdapter` a volání jeho `Update` metoda.</span><span class="sxs-lookup"><span data-stu-id="8f36a-151">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="8f36a-152">Všimněte si, že tento parametr zadán v klauzuli WHERE aktualizace příkazu nastaveno pro použití `Original` hodnotu `SourceColumn`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-152">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="8f36a-153">To je důležité, protože `Current` hodnota může změnit a nemusí odpovídat hodnotě ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="8f36a-153">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="8f36a-154">`Original` Hodnota je hodnota, která byla použita k vyplnění `DataTable` z datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="8f36a-154">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a><span data-ttu-id="8f36a-155">Sloupců s automatickým navyšováním</span><span class="sxs-lookup"><span data-stu-id="8f36a-155">AutoIncrement Columns</span></span>  
 <span data-ttu-id="8f36a-156">Pokud tabulky ze zdroje dat. automatické zvyšování sloupců, můžete přejít k vyplnění sloupce, které vaše `DataSet` buď vrácením hodnoty automatické zvyšování čísla jako výstupní parametr uložené procedury a mapování, který sloupec v tabulce, Autor vrácení Automatické zvyšování čísla hodnotu na prvním řádku vrácený příkaz jazyka SQL nebo uloženou proceduru nebo s použitím sady výsledků `RowUpdated` událost `DataAdapter` provádět další příkaz SELECT.</span><span class="sxs-lookup"><span data-stu-id="8f36a-156">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="8f36a-157">Další informace a příklad najdete v tématu [načítání Identity nebo automatického číslování hodnoty](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).</span><span class="sxs-lookup"><span data-stu-id="8f36a-157">For more information and an example, see [Retrieving Identity or Autonumber Values](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).</span></span>  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="8f36a-158">Pořadí vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="8f36a-158">Ordering of Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="8f36a-159">V mnoha případech platí, pořadí, ve které změny provedené `DataSet` jsou odesílány zdroj dat je důležité.</span><span class="sxs-lookup"><span data-stu-id="8f36a-159">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="8f36a-160">Například pokud se aktualizuje existující řádek hodnoty primárního klíče a nový řádek se přidala se nová hodnota primárního klíče jako cizí klíč, je potřeba zpracovat aktualizace, než jsou insert.</span><span class="sxs-lookup"><span data-stu-id="8f36a-160">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>  
  
 <span data-ttu-id="8f36a-161">Můžete použít `Select` metodu `DataTable` se vraťte `DataRow` pole, které odkazuje pouze na řádky s konkrétní `RowState`.</span><span class="sxs-lookup"><span data-stu-id="8f36a-161">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="8f36a-162">Můžete předat vráceného `DataRow` pole na `Update` metodu `DataAdapter` zpracovat změněné řádky.</span><span class="sxs-lookup"><span data-stu-id="8f36a-162">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="8f36a-163">Zadáním podmnožinu řádků, které mají být aktualizovány, můžete řídit pořadí, ve kterém jsou zpracovány vložení, aktualizace a odstranění.</span><span class="sxs-lookup"><span data-stu-id="8f36a-163">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f36a-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f36a-164">Example</span></span>  
 <span data-ttu-id="8f36a-165">Například následující kód zajišťuje, že jsou odstraněné řádky v tabulce zpracovaných první, pak aktualizované řádky a řádky vložené.</span><span class="sxs-lookup"><span data-stu-id="8f36a-165">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>  
  
```vb  
Dim table As DataTable = dataSet.Tables("Customers")  
  
' First process deletes.  
dataSet.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.Deleted))  
  
' Next process updates.  
adapter.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.ModifiedCurrent))  
  
' Finally, process inserts.  
dataAdapater.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.Added))  
```  
  
```csharp  
DataTable table = dataSet.Tables["Customers"];  
  
// First process deletes.  
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));  
  
// Next process updates.  
adapter.Update(table.Select(null, null,   
  DataViewRowState.ModifiedCurrent));  
  
// Finally, process inserts.  
adapter.Update(table.Select(null, null, DataViewRowState.Added));  
```  
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="8f36a-166">Umožňuje načíst a aktualizovat Data adaptéru dat</span><span class="sxs-lookup"><span data-stu-id="8f36a-166">Use a DataAdapter to Retrieve and Update Data</span></span>  
 <span data-ttu-id="8f36a-167">Můžete použít adaptéru dat se načítají a aktualizují data.</span><span class="sxs-lookup"><span data-stu-id="8f36a-167">You can use a DataAdapter to retrieve and update the data.</span></span>  
  
-   <span data-ttu-id="8f36a-168">Ukázka používá DataAdapter.AcceptChangesDuringFill se klonovat data v databázi.</span><span class="sxs-lookup"><span data-stu-id="8f36a-168">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="8f36a-169">Pokud je vlastnost nastavená na hodnotu false, metoda AcceptChanges není volána při vyplňování tabulky a nově přidané řádky jsou považovány za vložené řádky.</span><span class="sxs-lookup"><span data-stu-id="8f36a-169">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="8f36a-170">Tedy Ukázka používá tyto řádky k vložení nových řádků do databáze.</span><span class="sxs-lookup"><span data-stu-id="8f36a-170">So, the sample uses these rows to insert the new rows into the database.</span></span>  
  
-   <span data-ttu-id="8f36a-171">Ukázky pomocí DataAdapter.TableMappings definuje mapování mezi zdrojovou tabulku a DataTable.</span><span class="sxs-lookup"><span data-stu-id="8f36a-171">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>  
  
-   <span data-ttu-id="8f36a-172">Ukázka používá DataAdapter.FillLoadOption určit, jakým způsobem adaptér naplňuje objekt DataTable z DbDataReader.</span><span class="sxs-lookup"><span data-stu-id="8f36a-172">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="8f36a-173">Při vytváření objektu DataTable můžete pouze zapisovat data z databáze na aktuální verzi nebo verzi původního nastavením vlastnosti jako LoadOption.Upsert nebo LoadOption.PreserveChanges.</span><span class="sxs-lookup"><span data-stu-id="8f36a-173">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>  
  
-   <span data-ttu-id="8f36a-174">Ukázka také aktualizovat tabulky pomocí DbDataAdapter.UpdateBatchSize k provádění operací služby batch.</span><span class="sxs-lookup"><span data-stu-id="8f36a-174">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>  
  
 <span data-ttu-id="8f36a-175">Před kompilace a spuštění ukázky, budete muset vytvoření ukázkové databáze:</span><span class="sxs-lookup"><span data-stu-id="8f36a-175">Before you compile and run the sample, you need to create the sample database:</span></span>  
  
```  
USE [master]  
GO  
  
CREATE DATABASE [MySchool]   
  
GO  
  
USE [MySchool]  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,  
[Year] [smallint] NOT NULL,  
[Title] [nvarchar](100) NOT NULL,  
[Credits] [int] NOT NULL,  
[DepartmentID] [int] NOT NULL,  
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED  
(  
[CourseID] ASC,  
[Year] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,  
[Name] [nvarchar](50) NOT NULL,  
[Budget] [money] NOT NULL,  
[StartDate] [datetime] NOT NULL,  
[Administrator] [int] NULL,  
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED  
(  
[DepartmentID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)  
  
SET IDENTITY_INSERT [dbo].[Department] ON   
  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)  
SET IDENTITY_INSERT [dbo].[Department] OFF  
  
ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])  
REFERENCES [dbo].[Department] ([DepartmentID])  
GO  
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]  
GO  
```  
  
 <span data-ttu-id="8f36a-176">Projekty C# a Visual Basic se tento vzorový kód můžete najít na [ukázky kódu vývojáře](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span><span class="sxs-lookup"><span data-stu-id="8f36a-176">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.Common;  
using System.Data.SqlClient;  
using System.Linq;  
using CSDataAdapterOperations.Properties;  
  
namespace CSDataAdapterOperations.Properties {  
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {  
  
      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));  
  
      public static Settings Default {  
         get {  
            return defaultInstance;  
         }  
      }  
  
      [global::System.Configuration.ApplicationScopedSettingAttribute()]  
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]  
      public string MySchoolConnectionString {  
         get {  
            return ((string)(this["MySchoolConnectionString"]));  
         }  
      }  
   }  
}  
  
class Program {  
   static void Main(string[] args) {  
      Settings settings = new Settings();  
  
      // Copy the data from the database.  Get the table Department and Course from the database.  
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]  
                                     FROM [MySchool].[dbo].[Department];  
  
                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],  
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]  
                                   FROM [MySchool].[dbo].[Course]  
                                   Group by [CourseID]";  
  
      DataSet mySchool = new DataSet();  
  
      SqlCommand selectCommand = new SqlCommand(selectString);  
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);  
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);  
  
      // Use DataTableMapping to map the source tables and the destination tables.  
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};  
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);  
  
      Console.WriteLine("The following tables are from the database.");  
      foreach (DataTable table in mySchool.Tables) {  
         Console.WriteLine(table.TableName);  
         ShowDataTable(table);  
      }  
  
      // Roll back the changes  
      DataTable department = mySchool.Tables["Department"];  
      DataTable course = mySchool.Tables["Course"];  
  
      department.Rows[0]["Name"] = "New" + department.Rows[0][1];  
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];  
      course.Rows[0]["Credits"] = 10;  
  
      Console.WriteLine("After we changed the tables:");  
      foreach (DataTable table in mySchool.Tables) {  
         Console.WriteLine(table.TableName);  
         ShowDataTable(table);  
      }  
  
      department.RejectChanges();  
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");  
      ShowDataTable(department);  
  
      DataColumn[] primaryColumns = { course.Columns["CourseID"] };  
      DataColumn[] resetColumns = { course.Columns["Title"] };  
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);  
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");  
      ShowDataTable(course);  
  
      // Batch update the table.  
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],   
                                   [Credits],[DepartmentID])   
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";  
      SqlCommand insertCommand = new SqlCommand(insertString);  
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");  
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");  
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");  
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");  
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");  
  
      const Int32 batchSize = 10;  
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);  
   }  
  
   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         selectCommand.Connection = connection;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);  
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a   
            // DataRow after it is added to the DataTable during any of the Fill operations.  
            adapter.AcceptChangesDuringFill = false;  
  
            adapter.Fill(dataSet);  
         }  
      }  
   }  
  
   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.  
   private static void ResetCourse(DataTable table, String connectionString,  
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {  
      table.PrimaryKey = primaryColumns;  
  
      // Build the query string  
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));  
      String resetCols = String.Join(",", resetColumns.Select(col => "Max(" + col.ColumnName + ") as " + col.ColumnName));  
  
      String selectString = String.Format("Select {0},{1} from Course Group by {0}", primaryCols, resetCols);  
  
      SqlCommand selectCommand = new SqlCommand(selectString);  
  
      ResetDataTable(table, connectionString, selectCommand);  
   }  
  
   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges   
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges  
   // The ResetDataTable method rolls back one or more columns of data.  
   private static void ResetDataTable(DataTable table, String connectionString,  
       SqlCommand selectCommand) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         selectCommand.Connection = connection;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {  
            // The incoming values for this row will be written to the current version of each   
            // column. The original version of each column's data will not be changed.  
            adapter.FillLoadOption = LoadOption.Upsert;  
  
            adapter.Fill(table);  
         }  
      }  
   }  
  
   private static void BatchInsertUpdate(DataTable table, String connectionString,  
       SqlCommand insertCommand, Int32 batchSize) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         insertCommand.Connection = connection;  
         // When setting UpdateBatchSize to a value other than 1, all the commands   
         // associated with the SqlDataAdapter have to have their UpdatedRowSource   
         // property set to None or OutputParameters. An exception is thrown otherwise.  
         insertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter()) {  
            adapter.InsertCommand = insertCommand;  
            // Gets or sets the number of rows that are processed in each round-trip to the server.  
            // Setting it to 1 disables batch updates, as rows are sent one at a time.  
            adapter.UpdateBatchSize = batchSize;  
  
            adapter.Update(table);  
  
            Console.WriteLine("Successfully to update the table.");  
         }  
      }  
   }  
  
   private static void ShowDataTable(DataTable table) {  
      foreach (DataColumn col in table.Columns) {  
         Console.Write("{0,-14}", col.ColumnName);  
      }  
      Console.WriteLine("{0,-14}", "RowState");  
  
      foreach (DataRow row in table.Rows) {  
         foreach (DataColumn col in table.Columns) {  
            if (col.DataType.Equals(typeof(DateTime)))  
               Console.Write("{0,-14:d}", row[col]);  
            else if (col.DataType.Equals(typeof(Decimal)))  
               Console.Write("{0,-14:C}", row[col]);  
            else  
               Console.Write("{0,-14}", row[col]);  
         }  
         Console.WriteLine("{0,-14}", row.RowState);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f36a-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f36a-177">See Also</span></span>  
 [<span data-ttu-id="8f36a-178">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="8f36a-178">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="8f36a-179">Stavy řádků a verze řádků</span><span class="sxs-lookup"><span data-stu-id="8f36a-179">Row States and Row Versions</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [<span data-ttu-id="8f36a-180">Metody AcceptChanges a RejectChanges</span><span class="sxs-lookup"><span data-stu-id="8f36a-180">AcceptChanges and RejectChanges</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [<span data-ttu-id="8f36a-181">Slučování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="8f36a-181">Merging DataSet Contents</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [<span data-ttu-id="8f36a-182">Načítání hodnot identity nebo automatického číslování</span><span class="sxs-lookup"><span data-stu-id="8f36a-182">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [<span data-ttu-id="8f36a-183">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8f36a-183">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
