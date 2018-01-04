---
title: "Aktualizace zdrojů dat s DataAdapters"
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
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 44bd1672c6423277fa90eee98ce954e7c1c5334e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="51767-102">Aktualizace zdrojů dat s DataAdapters</span><span class="sxs-lookup"><span data-stu-id="51767-102">Updating Data Sources with DataAdapters</span></span>
<span data-ttu-id="51767-103">`Update` Metodu <xref:System.Data.Common.DataAdapter> je volána k vyřešení změny z <xref:System.Data.DataSet> zpět do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="51767-103">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="51767-104">`Update` Metoda, například `Fill` metoda, přijímá jako argumenty instanci `DataSet`a volitelné <xref:System.Data.DataTable> objekt nebo `DataTable` název.</span><span class="sxs-lookup"><span data-stu-id="51767-104">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="51767-105">`DataSet` Instance je `DataSet` obsahuje změny, které byly provedeny, a `DataTable` identifikuje tabulka, ze kterých se budou načítat změny.</span><span class="sxs-lookup"><span data-stu-id="51767-105">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="51767-106">Pokud žádné `DataTable` není zadaný, první `DataTable` v `DataSet` se používá.</span><span class="sxs-lookup"><span data-stu-id="51767-106">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>  
  
 <span data-ttu-id="51767-107">Při volání `Update` metody `DataAdapter` analyzuje změny, které jste provedli a provede příslušnou příkazu (INSERT, UPDATE nebo DELETE).</span><span class="sxs-lookup"><span data-stu-id="51767-107">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="51767-108">Když `DataAdapter` dojde ke změně <xref:System.Data.DataRow>, použije <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, nebo <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> zpracovat změny.</span><span class="sxs-lookup"><span data-stu-id="51767-108">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="51767-109">To umožňuje maximalizovat výkon vaší aplikace ADO.NET zadáním syntaxe příkazu v době návrhu a, kde je to možné, prostřednictvím uložených procedur.</span><span class="sxs-lookup"><span data-stu-id="51767-109">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="51767-110">Musíte jednoznačně nastavit příkazy před voláním `Update`.</span><span class="sxs-lookup"><span data-stu-id="51767-110">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="51767-111">Pokud `Update` nazývá a příslušný příkaz neexistuje pro konkrétní aktualizaci (například Ne `DeleteCommand` pro odstranit řádky), je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="51767-111">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51767-112">Pokud chcete upravit nebo odstranit data pomocí používáte uložené procedury SQL serveru `DataAdapter`, ujistěte se, nepoužívejte SET NOCOUNT ON v definici uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="51767-112">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="51767-113">To způsobí, že počet ovlivněných řádků vrácena rovno nule, který `DataAdapter` interpretuje jako konflikt souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="51767-113">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="51767-114">V takovém případě <xref:System.Data.DBConcurrencyException> bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="51767-114">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
 <span data-ttu-id="51767-115">Parametry příkazu lze zadat vstupní a výstupní hodnoty pro příkaz SQL nebo uloženou proceduru pro každý řádek upravený `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="51767-115">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="51767-116">Další informace najdete v tématu [DataAdapter parametry](../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="51767-116">For more information, see [DataAdapter Parameters](../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51767-117">Je důležité si uvědomit rozdíl mezi odstranění řádku <xref:System.Data.DataTable> a odebírání řádek.</span><span class="sxs-lookup"><span data-stu-id="51767-117">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="51767-118">Při volání `Remove` nebo `RemoveAt` metoda, řádek je odebrán okamžitě.</span><span class="sxs-lookup"><span data-stu-id="51767-118">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="51767-119">Žádné odpovídající řádky v back-end zdroj dat, nebude mít vliv, pokud pak předáte `DataTable` nebo `DataSet` k `DataAdapter` a volání `Update`.</span><span class="sxs-lookup"><span data-stu-id="51767-119">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="51767-120">Při použití `Delete` metody řádek zůstane v `DataTable` a je označena pro odstranění.</span><span class="sxs-lookup"><span data-stu-id="51767-120">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="51767-121">Pokud pak předáte `DataTable` nebo `DataSet` k `DataAdapter` a volání `Update`, odpovídající řádek v back-end zdroj dat je odstraněn.</span><span class="sxs-lookup"><span data-stu-id="51767-121">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>  
  
 <span data-ttu-id="51767-122">Pokud vaše `DataTable` mapuje nebo se vygeneruje z jedné tabulky databáze, můžete využít výhod <xref:System.Data.Common.DbCommandBuilder> objekt, který má automaticky generovat `DeleteCommand`, `InsertCommand`, a `UpdateCommand` objekty pro `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="51767-122">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="51767-123">Další informace najdete v tématu [generování příkazů s CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="51767-123">For more information, see [Generating Commands with CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).</span></span>  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="51767-124">Mapování hodnot na datovou sadu pomocí UpdatedRowSource</span><span class="sxs-lookup"><span data-stu-id="51767-124">Using UpdatedRowSource to Map Values to a DataSet</span></span>  
 <span data-ttu-id="51767-125">Můžete řídit, jak jsou mapována hodnot vrácených ze zdroje dat na `DataTable` následující volání metodě aktualizace `DataAdapter`, pomocí <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> vlastnost <xref:System.Data.Common.DbCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="51767-125">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="51767-126">Nastavením `UpdatedRowSource` vlastnost na jednu z <xref:System.Data.UpdateRowSource> hodnoty výčtu, můžete řídit zda výstupní parametry vrácený `DataAdapter` příkazy jsou ignorovány nebo použitá na změněných řádků v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="51767-126">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="51767-127">Můžete také určit, zda vrátí první řádek (pokud existuje) se použijí na změněných řádků v `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="51767-127">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>  
  
 <span data-ttu-id="51767-128">Následující tabulka popisuje různé hodnoty `UpdateRowSource` výčet a jejich vliv na chování příkazu použít s `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="51767-128">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>  
  
|<span data-ttu-id="51767-129">UpdatedRowSource – výčet</span><span class="sxs-lookup"><span data-stu-id="51767-129">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="51767-130">Popis</span><span class="sxs-lookup"><span data-stu-id="51767-130">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="51767-131">Výstupní parametry a první řádek je sada výsledků vrácená dotazu může být namapovaný na změněné řádek v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="51767-131">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="51767-132">Pouze data na prvním řádku je sada výsledků vrácená dotazu může být namapovaný na změněné řádek v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="51767-132">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|  
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="51767-133">Výstup parametry nebo řádky vrácené výsledné sady jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="51767-133">Any output parameters or rows of a returned result set are ignored.</span></span>|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="51767-134">Pouze výstupní parametry se dají namapovat na změněné řádek v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="51767-134">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|  
  
 <span data-ttu-id="51767-135">`Update` Metoda přeloží změny zpět do zdroje dat; ale jiných klientů může mít změnit dat ve zdroji dat od poslední jste vyplnili `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="51767-135">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="51767-136">Aktualizace vašeho `DataSet` s aktuální data, použijte `DataAdapter` a `Fill` metoda.</span><span class="sxs-lookup"><span data-stu-id="51767-136">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="51767-137">Přidá nové řádky do tabulky a aktualizované informace se začlení do existujících řádků.</span><span class="sxs-lookup"><span data-stu-id="51767-137">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="51767-138">`Fill` Metoda určuje, zda bude přidán nový řádek nebo zaktualizuje stávající řádek porovnáním hodnot primárního klíče řádků v `DataSet` a řádky vrácené `SelectCommand`.</span><span class="sxs-lookup"><span data-stu-id="51767-138">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="51767-139">Pokud `Fill` metoda zaznamená hodnotu primárního klíče pro řádek v `DataSet` odpovídající hodnotu primárního klíče v řádku v výsledků vrácených `SelectCommand`, aktualizuje existující řádek s informací z řádku vrácené `SelectCommand`a nastaví <xref:System.Data.DataRow.RowState%2A> z existující řádek, abyste `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="51767-139">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="51767-140">Pokud řádek vrácený `SelectCommand` má hodnotu primárního klíče, který neodpovídá žádnému z hodnot primárního klíče řádků v `DataSet`, `Fill` metoda přidá nový řádek s `RowState` z `Unchanged`.</span><span class="sxs-lookup"><span data-stu-id="51767-140">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51767-141">Pokud `SelectCommand` vrátí výsledky z vnějšího spojení, `DataAdapter` nenastaví `PrimaryKey` výsledná hodnota `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="51767-141">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="51767-142">Je nutné definovat `PrimaryKey` si, že jsou správně přeložit duplicitní řádky.</span><span class="sxs-lookup"><span data-stu-id="51767-142">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="51767-143">Další informace najdete v tématu [definování primárních klíčů](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="51767-143">For more information, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="51767-144">Zpracování výjimek, které mohou nastat při volání `Update` metodu, můžete použít `RowUpdated` událostí reagovat na řádek aktualizace chyby, kdy k nim dojde (najdete v části [zpracování události DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), nebo můžete nastavit `DataAdapter.ContinueUpdateOnError` k `true` před voláním `Update`a reagovat na informace o chybě, které jsou uložené v `RowError` vlastnost konkrétního řádku po dokončení aktualizace (najdete v části [informace o chybě řádek](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).</span><span class="sxs-lookup"><span data-stu-id="51767-144">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).</span></span>  
  
 <span data-ttu-id="51767-145">**Poznámka:** volání `AcceptChanges` na `DataSet`, `DataTable`, nebo `DataRow` způsobí, že všechny `Original` hodnoty pro `DataRow` přepsání s `Current` hodnoty `DataRow`.</span><span class="sxs-lookup"><span data-stu-id="51767-145">**Note** Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="51767-146">Pokud hodnoty polí, které identifikují řádku jako jedinečný změnilo po volání `AcceptChanges` `Original` hodnoty budou už shodují s hodnotami v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="51767-146">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="51767-147">`AcceptChanges`je automaticky volána pro každý řádek během volání metodě aktualizace `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="51767-147">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="51767-148">Můžete zachovat původní hodnoty při volání metody aktualizace první nastavením `AcceptChangesDuringUpdate` vlastnost `DataAdapter` na hodnotu false, případně můžete vytvořit obslužnou rutinu události pro `RowUpdated` událostí a nastavení <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> k <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span><span class="sxs-lookup"><span data-stu-id="51767-148">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="51767-149">Další informace najdete v tématu [slučování obsah datovou sadu](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) a [zpracování události DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="51767-149">For more information, see [Merging DataSet Contents](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51767-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="51767-150">Example</span></span>  
 <span data-ttu-id="51767-151">Následující příklady ukazují, jak provést aktualizace na upravené řádky explicitně nastavením `UpdateCommand` z `DataAdapter` a volání jeho `Update` metoda.</span><span class="sxs-lookup"><span data-stu-id="51767-151">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="51767-152">Všimněte si, že zadaný parametr v klauzuli WHERE aktualizace příkaz nastaven pro použití `Original` hodnotu `SourceColumn`.</span><span class="sxs-lookup"><span data-stu-id="51767-152">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="51767-153">To je důležité, protože `Current` hodnota může změnit a nemusí odpovídat hodnotě v datovém zdroji.</span><span class="sxs-lookup"><span data-stu-id="51767-153">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="51767-154">`Original` Hodnota je hodnota, která byla použita k vyplnění `DataTable` ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="51767-154">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a><span data-ttu-id="51767-155">Element AutoIncrement sloupců</span><span class="sxs-lookup"><span data-stu-id="51767-155">AutoIncrement Columns</span></span>  
 <span data-ttu-id="51767-156">Pokud automaticky rostoucí sloupců tabulky ze zdroje dat, můžete vyplnit sloupce vaší `DataSet` buď tak, že vrací hodnotu automatického přírůstku jako výstupní parametr uložené procedury a který mapování na sloupec v tabulce, pomocí vrácení hodnota automatického přírůstku na prvním řádku sada výsledků vrácená pomocí uložené procedury nebo příkazu SQL, nebo pomocí `RowUpdated` události `DataAdapter` k provedení příkazu vyberte další.</span><span class="sxs-lookup"><span data-stu-id="51767-156">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="51767-157">Další informace a příklady naleznete v tématu [načítání Identity nebo automatické číslování hodnoty](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).</span><span class="sxs-lookup"><span data-stu-id="51767-157">For more information and an example, see [Retrieving Identity or Autonumber Values](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).</span></span>  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="51767-158">Řazení vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="51767-158">Ordering of Inserts, Updates, and Deletes</span></span>  
 <span data-ttu-id="51767-159">V mnoha případech pořadí, ve které změny prostřednictvím `DataSet` odešlou zdroj dat je důležité.</span><span class="sxs-lookup"><span data-stu-id="51767-159">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="51767-160">Například pokud se aktualizuje stávající řádek hodnotu primárního klíče a nový řádek byla přidána s novou hodnotu primárního klíče jako cizí klíč, je potřeba zpracovat aktualizace, než insert.</span><span class="sxs-lookup"><span data-stu-id="51767-160">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>  
  
 <span data-ttu-id="51767-161">Můžete použít `Select` metodu `DataTable` vrátit `DataRow` pole, které odkazuje pouze řádky s konkrétní `RowState`.</span><span class="sxs-lookup"><span data-stu-id="51767-161">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="51767-162">Potom můžete předat vrácený `DataRow` pole na `Update` metodu `DataAdapter` zpracovat změněné řádky.</span><span class="sxs-lookup"><span data-stu-id="51767-162">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="51767-163">Zadáním podmnožinu řádků, který má být aktualizován, můžete řídit pořadí, ve kterém jsou zpracovány vložení, aktualizace a odstranění.</span><span class="sxs-lookup"><span data-stu-id="51767-163">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51767-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="51767-164">Example</span></span>  
 <span data-ttu-id="51767-165">Následující kód například zajišťuje, aby byly odstraněné řádky v tabulce zpracovaná první, potom aktualizované řádky a řádky vložené.</span><span class="sxs-lookup"><span data-stu-id="51767-165">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>  
  
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
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="51767-166">Použijte modul DataAdapter načíst a aktualizovat Data</span><span class="sxs-lookup"><span data-stu-id="51767-166">Use a DataAdapter to Retrieve and Update Data</span></span>  
 <span data-ttu-id="51767-167">Modul DataAdapter můžete načíst a aktualizovat data.</span><span class="sxs-lookup"><span data-stu-id="51767-167">You can use a DataAdapter to retrieve and update the data.</span></span>  
  
-   <span data-ttu-id="51767-168">Příklad používá DataAdapter.AcceptChangesDuringFill klonovat data v databázi.</span><span class="sxs-lookup"><span data-stu-id="51767-168">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="51767-169">Pokud je vlastnost nastavena jako hodnotu false, metoda AcceptChanges není volán při vyplňování tabulky a nově přidané řádky jsou považovány za vložených řádků.</span><span class="sxs-lookup"><span data-stu-id="51767-169">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="51767-170">Ano příklad používá tyto řádky do nové řádky vložit do databáze.</span><span class="sxs-lookup"><span data-stu-id="51767-170">So, the sample uses these rows to insert the new rows into the database.</span></span>  
  
-   <span data-ttu-id="51767-171">Ukázky DataAdapter.TableMappings používá k definování mapování mezi zdrojovou tabulku a DataTable.</span><span class="sxs-lookup"><span data-stu-id="51767-171">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>  
  
-   <span data-ttu-id="51767-172">Ukázka používá k určení, jak adaptér doplní DataTable z DbDataReader DataAdapter.FillLoadOption.</span><span class="sxs-lookup"><span data-stu-id="51767-172">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="51767-173">Při vytváření DataTable můžete pouze zapsat data z databáze do aktuální verze nebo na původní verzi nastavením vlastnosti jako LoadOption.Upsert nebo LoadOption.PreserveChanges.</span><span class="sxs-lookup"><span data-stu-id="51767-173">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>  
  
-   <span data-ttu-id="51767-174">Ukázka bude také aktualizovat tabulky pomocí DbDataAdapter.UpdateBatchSize provést dávkové operace.</span><span class="sxs-lookup"><span data-stu-id="51767-174">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>  
  
 <span data-ttu-id="51767-175">Před zkompilování a spuštění ukázky, je třeba k vytvoření ukázkové databáze:</span><span class="sxs-lookup"><span data-stu-id="51767-175">Before you compile and run the sample, you need to create the sample database:</span></span>  
  
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
  
 <span data-ttu-id="51767-176">C# a Visual Basic projekty s této ukázce kódu najdete na [ukázky kódu vývojáře](http://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span><span class="sxs-lookup"><span data-stu-id="51767-176">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](http://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51767-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="51767-177">See Also</span></span>  
 [<span data-ttu-id="51767-178">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="51767-178">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="51767-179">Stavy řádků a verze řádků</span><span class="sxs-lookup"><span data-stu-id="51767-179">Row States and Row Versions</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [<span data-ttu-id="51767-180">Metody AcceptChanges a RejectChanges</span><span class="sxs-lookup"><span data-stu-id="51767-180">AcceptChanges and RejectChanges</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [<span data-ttu-id="51767-181">Slučování obsahu datové sady</span><span class="sxs-lookup"><span data-stu-id="51767-181">Merging DataSet Contents</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [<span data-ttu-id="51767-182">Načítání hodnot identity nebo automatického číslování</span><span class="sxs-lookup"><span data-stu-id="51767-182">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [<span data-ttu-id="51767-183">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="51767-183">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
