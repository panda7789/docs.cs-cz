---
title: Aktualizace zdrojů dat pomocí adaptérů dat
description: Přečtěte si, jak metoda Update funkce DataAdapter vyřeší změny z datové sady zpátky na zdroj dat v aplikacích ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: e2348a3a89aa1c28856bfc21aaa25f2c8327aac7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286181"
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="1cc5e-103">Aktualizace zdrojů dat pomocí adaptérů dat</span><span class="sxs-lookup"><span data-stu-id="1cc5e-103">Updating Data Sources with DataAdapters</span></span>

<span data-ttu-id="1cc5e-104">`Update`Metoda <xref:System.Data.Common.DataAdapter> je volána k vyřešení změn z <xref:System.Data.DataSet> zpátky na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-104">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="1cc5e-105">`Update`Metoda, jako je například `Fill` metoda, přijímá jako argumenty instanci a, což `DataSet` je nepovinný <xref:System.Data.DataTable> objekt nebo `DataTable` název.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-105">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="1cc5e-106">`DataSet`Instance je `DataSet` , která obsahuje změny, které byly provedeny, a `DataTable` identifikuje tabulku, ze které se mají změny načíst.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-106">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="1cc5e-107">Pokud `DataTable` není zadán, použije se první `DataTable` v `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-107">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>

<span data-ttu-id="1cc5e-108">Když zavoláte `Update` metodu, `DataAdapter` analyzuje provedené změny a provede příslušný příkaz (INSERT, Update nebo Delete).</span><span class="sxs-lookup"><span data-stu-id="1cc5e-108">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="1cc5e-109">Když `DataAdapter` dojde ke změně <xref:System.Data.DataRow> , používá, <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> nebo <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> ke zpracování změny.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-109">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="1cc5e-110">Díky tomu můžete maximalizovat výkon aplikace ADO.NET zadáním syntaxe příkazu v době návrhu a pokud je to možné, pomocí uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-110">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="1cc5e-111">Před voláním je nutné explicitně nastavit příkazy `Update` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-111">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="1cc5e-112">Pokud `Update` je volána a příslušný příkaz pro konkrétní aktualizaci neexistuje (například ne `DeleteCommand` pro odstraněné řádky), je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-112">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>

> [!NOTE]
> <span data-ttu-id="1cc5e-113">Pokud používáte SQL Server uložené procedury k úpravám nebo odstraňování dat pomocí, ujistěte se `DataAdapter` , že v definici uložené procedury nepoužijete nastavení počet.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-113">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="1cc5e-114">To způsobí, že počet ovlivněných řádků vrátil hodnotu nula, což `DataAdapter` interpretuje jako konflikt souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-114">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="1cc5e-115">V tomto případě <xref:System.Data.DBConcurrencyException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-115">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>

<span data-ttu-id="1cc5e-116">Parametry příkazu lze použít k určení vstupních a výstupních hodnot příkazu SQL nebo uložené procedury pro každý upravený řádek v `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-116">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="1cc5e-117">Další informace naleznete v tématu [parametry DataAdapter](dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1cc5e-117">For more information, see [DataAdapter Parameters](dataadapter-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1cc5e-118">Je důležité pochopit rozdíl mezi odstraněním řádku v <xref:System.Data.DataTable> a odebráním řádku.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-118">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="1cc5e-119">Při volání `Remove` metody nebo se `RemoveAt` řádek odebere okamžitě.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-119">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="1cc5e-120">Pokud pak předáte `DataTable` nebo `DataSet` k `DataAdapter` volání a, nebudou ovlivněny žádné odpovídající řádky ve zdroji dat back-end `Update` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-120">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="1cc5e-121">Když použijete `Delete` metodu, řádek zůstane v `DataTable` a je označený k odstranění.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-121">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="1cc5e-122">Pokud předáte `DataTable` `DataSet` `DataAdapter` volání metody a a a `Update` , je odstraněn odpovídající řádek ve zdroji dat back-endu.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-122">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>

<span data-ttu-id="1cc5e-123">Pokud vaše `DataTable` mapy nebo jsou vygenerovány z jedné tabulky databáze, můžete využít výhod <xref:System.Data.Common.DbCommandBuilder> objektu pro automatické generování `DeleteCommand` `InsertCommand` objektů, a `UpdateCommand` pro `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-123">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="1cc5e-124">Další informace najdete v tématu [generování příkazů pomocí CommandBuilders](generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="1cc5e-124">For more information, see [Generating Commands with CommandBuilders](generating-commands-with-commandbuilders.md).</span></span>

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="1cc5e-125">Mapování hodnot na datovou sadu pomocí UpdatedRowSource</span><span class="sxs-lookup"><span data-stu-id="1cc5e-125">Using UpdatedRowSource to Map Values to a DataSet</span></span>

<span data-ttu-id="1cc5e-126">Můžete určit, jak budou hodnoty vrácené ze zdroje dat mapovány zpět na `DataTable` následující volání metody aktualizace pro `DataAdapter` , pomocí <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> vlastnosti <xref:System.Data.Common.DbCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-126">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="1cc5e-127">Nastavením `UpdatedRowSource` vlastnosti na jednu z <xref:System.Data.UpdateRowSource> hodnot výčtu můžete určit, zda budou výstupní parametry vracené `DataAdapter` příkazy ignorovány nebo aplikovány na změněný řádek v `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-127">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="1cc5e-128">Můžete také určit, zda byl první vrácený řádek (pokud existuje) použit pro změněný řádek v `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-128">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>

<span data-ttu-id="1cc5e-129">V následující tabulce jsou popsány různé hodnoty `UpdateRowSource` výčtu a jejich vliv na chování příkazu používaného s `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-129">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>

|<span data-ttu-id="1cc5e-130">Výčet UpdatedRowSource</span><span class="sxs-lookup"><span data-stu-id="1cc5e-130">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="1cc5e-131">Popis</span><span class="sxs-lookup"><span data-stu-id="1cc5e-131">Description</span></span>|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="1cc5e-132">Výstupní parametry a první řádek vrácené sady výsledků můžou být namapovány na změněný řádek v `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-132">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="1cc5e-133">Pouze data v prvním řádku vrácené sady výsledků dotazu mohou být mapována na změněný řádek v `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-133">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="1cc5e-134">Všechny výstupní parametry nebo řádky vracené sady výsledků jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-134">Any output parameters or rows of a returned result set are ignored.</span></span>|
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="1cc5e-135">Pouze výstupní parametry mohou být mapovány na změněný řádek v `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-135">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|

<span data-ttu-id="1cc5e-136">`Update`Metoda vyřeší vaše změny zpátky na zdroj dat. ostatní klienti však mohou data ze zdroje dat od posledního vyplňování upravovat `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-136">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="1cc5e-137">Chcete-li aktualizovat `DataSet` aktuální data, použijte `DataAdapter` metodu a `Fill` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-137">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="1cc5e-138">Do tabulky budou přidány nové řádky a aktualizované informace budou zahrnuty do stávajících řádků.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-138">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="1cc5e-139">`Fill`Metoda určuje, zda bude přidán nový řádek, nebo bude aktualizován existující řádek tím, že prozkoumá hodnoty primárního klíče řádků v řádcích `DataSet` a řádky vrácené `SelectCommand` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-139">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="1cc5e-140">Pokud `Fill` Metoda narazí na hodnotu primárního klíče pro řádek v `DataSet` , který se shoduje s hodnotou primárního klíče z řádku v výsledkůch vrácených `SelectCommand` , aktualizuje stávající řádek informacemi z řádku vráceného `SelectCommand` a nastaví <xref:System.Data.DataRow.RowState%2A> existující řádek na `Unchanged` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-140">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="1cc5e-141">Pokud řádek vrácený `SelectCommand` hodnotou má primární klíč, který se neshoduje s žádnou z hodnot primárního klíče v řádcích v `DataSet` , `Fill` Metoda přidá nový řádek s hodnotou `RowState` `Unchanged` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-141">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>

> [!NOTE]
> <span data-ttu-id="1cc5e-142">Vrátí-li `SelectCommand` funkce výsledky vnějšího spojení, nebude `DataAdapter` `PrimaryKey` hodnota pro výsledný výsledek nastavena `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-142">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="1cc5e-143">Aby `PrimaryKey` bylo zajištěno, že duplicitní řádky budou správně vyřešeny, je nutné definovat sami sebe.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-143">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="1cc5e-144">Další informace najdete v tématu [Definování primárních klíčů](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="1cc5e-144">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>

<span data-ttu-id="1cc5e-145">Chcete-li zpracovat výjimky, které mohou nastat při volání `Update` metody, můžete použít `RowUpdated` událost k reakci na chyby aktualizace řádků při jejich výskytu ( [Viz zpracování událostí DataAdapter](handling-dataadapter-events.md)), nebo můžete nastavit `DataAdapter.ContinueUpdateOnError` na hodnotu `true` před voláním `Update` a reagovat na informace o chybě uložené v `RowError` vlastnosti určitého řádku po dokončení aktualizace (viz [informace o chybě řádku](./dataset-datatable-dataview/row-error-information.md)).</span><span class="sxs-lookup"><span data-stu-id="1cc5e-145">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](./dataset-datatable-dataview/row-error-information.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="1cc5e-146">Volání `AcceptChanges` na `DataSet` , `DataTable` , nebo způsobí, že `DataRow` všechny `Original` hodnoty pro a budou `DataRow` přepsány `Current` hodnotami pro `DataRow` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-146">Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="1cc5e-147">Pokud byly změněny hodnoty polí, které identifikují řádek jako jedinečné, potom po volání `AcceptChanges` `Original` hodnoty již nebudou hodnoty ve zdroji dat odpovídat.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-147">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="1cc5e-148">`AcceptChanges`je volána automaticky pro každý řádek při volání metody aktualizace pro `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-148">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="1cc5e-149">Původní hodnoty můžete zachovat během volání metody aktualizace – nejprve nastavte `AcceptChangesDuringUpdate` vlastnost na `DataAdapter` hodnotu false nebo vytvořením obslužné rutiny události pro `RowUpdated` událost a nastavením na <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> <xref:System.Data.UpdateStatus.SkipCurrentRow> .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-149">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="1cc5e-150">Další informace najdete v tématech [sloučení obsahu datových sad](./dataset-datatable-dataview/merging-dataset-contents.md) a [zpracování událostí DataAdapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="1cc5e-150">For more information, see [Merging DataSet Contents](./dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="1cc5e-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cc5e-151">Example</span></span>

<span data-ttu-id="1cc5e-152">Následující příklady ukazují, jak provést aktualizace upravených řádků explicitně nastavením typu `UpdateCommand` `DataAdapter` a a voláním `Update` metody.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-152">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="1cc5e-153">Všimněte si, že parametr zadaný v klauzuli WHERE příkazu UPDATE je nastaven na použití `Original` hodnoty `SourceColumn` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-153">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="1cc5e-154">To je důležité, protože `Current` hodnota je možná upravená a nemusí odpovídat hodnotě ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-154">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="1cc5e-155">`Original`Hodnota je hodnota, která byla použita k naplnění `DataTable` zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-155">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a><span data-ttu-id="1cc5e-156">Sloupce AutoIncrement</span><span class="sxs-lookup"><span data-stu-id="1cc5e-156">AutoIncrement Columns</span></span>

<span data-ttu-id="1cc5e-157">Pokud tabulky ze zdroje dat mají automatické přírůstkové sloupce, sloupce můžete vyplnit `DataSet` buď tak, že vrátíte hodnotu automatického zvýšení jako výstupní parametr uložené procedury a mapování na sloupec v tabulce, vrácením hodnoty AutoIncrement v prvním řádku výsledné sady vrácené uloženou procedurou nebo příkazem jazyka SQL nebo pomocí `RowUpdated` události `DataAdapter` ke spuštění dalšího příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-157">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="1cc5e-158">Další informace a příklad najdete v tématu [načtení hodnot identity nebo Autonumber Values](retrieving-identity-or-autonumber-values.md).</span><span class="sxs-lookup"><span data-stu-id="1cc5e-158">For more information and an example, see [Retrieving Identity or Autonumber Values](retrieving-identity-or-autonumber-values.md).</span></span>

## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="1cc5e-159">Řazení vložení, aktualizací a odstranění</span><span class="sxs-lookup"><span data-stu-id="1cc5e-159">Ordering of Inserts, Updates, and Deletes</span></span>

<span data-ttu-id="1cc5e-160">V mnoha případech je důležité pořadí, ve kterém se změny provedou při `DataSet` odeslání do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-160">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="1cc5e-161">Například pokud je hodnota primárního klíče pro existující řádek aktualizována a nový řádek byl přidán s novou hodnotou primárního klíče jako cizí klíč, je důležité zpracovat aktualizaci před vložením.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-161">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>

<span data-ttu-id="1cc5e-162">Můžete použít `Select` metodu `DataTable` pro vrácení `DataRow` pole, které odkazuje pouze na řádky s určitým objektem `RowState` .</span><span class="sxs-lookup"><span data-stu-id="1cc5e-162">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="1cc5e-163">Pak můžete předat vrácené `DataRow` pole `Update` metodě `DataAdapter` pro zpracování změněných řádků.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-163">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="1cc5e-164">Zadáním podmnožiny řádků, které se mají aktualizovat, můžete řídit pořadí, ve kterém se zpracují vložení, aktualizace a odstranění.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-164">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>

## <a name="example"></a><span data-ttu-id="1cc5e-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cc5e-165">Example</span></span>

<span data-ttu-id="1cc5e-166">Následující kód například zajistí, že se odstraněné řádky tabulky zpracovávají jako první, pak aktualizované řádky a vložené řádky.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-166">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>

```vb
Dim table As DataTable = dataSet.Tables("Customers")

' First process deletes.
dataSet.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Deleted))

' Next process updates.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.ModifiedCurrent))

' Finally, process inserts.
adapter.Update(table.Select(Nothing, Nothing, _
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

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="1cc5e-167">Použití DataAdapter k načtení a aktualizaci dat</span><span class="sxs-lookup"><span data-stu-id="1cc5e-167">Use a DataAdapter to Retrieve and Update Data</span></span>

<span data-ttu-id="1cc5e-168">K načtení a aktualizaci dat lze použít modul DataAdapter.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-168">You can use a DataAdapter to retrieve and update the data.</span></span>

- <span data-ttu-id="1cc5e-169">Ukázka používá DataAdapter. AcceptChangesDuringFill ke klonování dat v databázi.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-169">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="1cc5e-170">Pokud je vlastnost nastavena na hodnotu false, při vyplňování tabulky není volána metoda AcceptChanges a nově přidané řádky jsou zpracovány jako vložené řádky.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-170">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="1cc5e-171">Ukázka proto používá tyto řádky k vložení nových řádků do databáze.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-171">So, the sample uses these rows to insert the new rows into the database.</span></span>

- <span data-ttu-id="1cc5e-172">Ukázky používají DataAdapter. vlastnosti TableMappings k definování mapování mezi zdrojovou tabulkou a DataTable.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-172">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>

- <span data-ttu-id="1cc5e-173">Ukázka používá DataAdapter. FillLoadOption k určení toho, jak adaptér vyplní objekt DataTable z DbDataReader.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-173">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="1cc5e-174">Při vytváření objektu DataTable můžete zapsat data pouze z databáze do aktuální verze nebo původní verze nastavením vlastnosti jako LoadOption. Upsert nebo LoadOption. PreserveChanges.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-174">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>

- <span data-ttu-id="1cc5e-175">Ukázka také aktualizuje tabulku pomocí objekt DbDataAdapter. UpdateBatchSize a provede operace dávkového zpracování.</span><span class="sxs-lookup"><span data-stu-id="1cc5e-175">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>

<span data-ttu-id="1cc5e-176">Před kompilací a spuštěním ukázky je třeba vytvořit ukázkovou databázi:</span><span class="sxs-lookup"><span data-stu-id="1cc5e-176">Before you compile and run the sample, you need to create the sample database:</span></span>

```sql
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

<span data-ttu-id="1cc5e-177">Projekty C# a Visual Basic s touto ukázkou kódu najdete v [ukázkách kódu pro vývojáře](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span><span class="sxs-lookup"><span data-stu-id="1cc5e-177">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>

```csharp
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
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));

      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");

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

## <a name="see-also"></a><span data-ttu-id="1cc5e-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cc5e-178">See also</span></span>

- [<span data-ttu-id="1cc5e-179">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="1cc5e-179">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="1cc5e-180">Stavy řádků a verze řádků</span><span class="sxs-lookup"><span data-stu-id="1cc5e-180">Row States and Row Versions</span></span>](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [<span data-ttu-id="1cc5e-181">Metody AcceptChanges a RejectChanges</span><span class="sxs-lookup"><span data-stu-id="1cc5e-181">AcceptChanges and RejectChanges</span></span>](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [<span data-ttu-id="1cc5e-182">Slučování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="1cc5e-182">Merging DataSet Contents</span></span>](./dataset-datatable-dataview/merging-dataset-contents.md)
- [<span data-ttu-id="1cc5e-183">Načítání hodnot identity nebo automatického číslování</span><span class="sxs-lookup"><span data-stu-id="1cc5e-183">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)
- [<span data-ttu-id="1cc5e-184">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1cc5e-184">ADO.NET Overview</span></span>](ado-net-overview.md)
