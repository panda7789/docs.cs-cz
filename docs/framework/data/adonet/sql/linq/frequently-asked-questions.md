---
title: Nejčastější dotazy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: ed9149eb5b88d648c02863e0fb0101e5503e1c73
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782140"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="f83a8-102">Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="f83a8-102">Frequently Asked Questions</span></span>

<span data-ttu-id="f83a8-103">V následujících částech najdete odpovědi na některé běžné problémy, se kterými se můžete [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]setkat při implementaci nástroje.</span><span class="sxs-lookup"><span data-stu-id="f83a8-103">The following sections answer some common issues that you might encounter when you implement [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>

<span data-ttu-id="f83a8-104">Další problémy jsou řešeny při [řešení potíží](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="f83a8-104">Additional issues are addressed in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="cannot-connect"></a><span data-ttu-id="f83a8-105">Nejde se připojit</span><span class="sxs-lookup"><span data-stu-id="f83a8-105">Cannot Connect</span></span>

<span data-ttu-id="f83a8-106">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-106">Q.</span></span> <span data-ttu-id="f83a8-107">Nemůžu se připojit k databázi.</span><span class="sxs-lookup"><span data-stu-id="f83a8-107">I cannot connect to my database.</span></span>

<span data-ttu-id="f83a8-108">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-108">A.</span></span> <span data-ttu-id="f83a8-109">Ujistěte se, že je připojovací řetězec správný a že je spuštěná instance SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f83a8-109">Make sure your connection string is correct and that your SQL Server instance is running.</span></span> <span data-ttu-id="f83a8-110">Upozorňujeme také, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] že je nutné povolit protokol pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="f83a8-110">Note also that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requires the Named Pipes protocol to be enabled.</span></span> <span data-ttu-id="f83a8-111">Další informace najdete v tématu [výukové postupy](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="f83a8-111">For more information, see [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

## <a name="changes-to-database-lost"></a><span data-ttu-id="f83a8-112">Změny databáze ztraceny</span><span class="sxs-lookup"><span data-stu-id="f83a8-112">Changes to Database Lost</span></span>

<span data-ttu-id="f83a8-113">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-113">Q.</span></span> <span data-ttu-id="f83a8-114">Změnil (a) jsem data v databázi, ale při Reran své aplikace už tato změna neexistovala.</span><span class="sxs-lookup"><span data-stu-id="f83a8-114">I made a change to data in the database, but when I reran my application, the change was no longer there.</span></span>

<span data-ttu-id="f83a8-115">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-115">A.</span></span> <span data-ttu-id="f83a8-116">Ujistěte se, že zavoláte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> k uložení výsledků do databáze.</span><span class="sxs-lookup"><span data-stu-id="f83a8-116">Make sure that you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> to save results to the database.</span></span>

## <a name="database-connection-open-how-long"></a><span data-ttu-id="f83a8-117">Připojení k databázi: Otevřít jak dlouho?</span><span class="sxs-lookup"><span data-stu-id="f83a8-117">Database Connection: Open How Long?</span></span>

<span data-ttu-id="f83a8-118">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-118">Q.</span></span> <span data-ttu-id="f83a8-119">Jak dlouho zůstane moje připojení k databázi otevřené?</span><span class="sxs-lookup"><span data-stu-id="f83a8-119">How long does my database connection remain open?</span></span>

<span data-ttu-id="f83a8-120">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-120">A.</span></span> <span data-ttu-id="f83a8-121">Připojení obvykle zůstává otevřené, dokud nespotřebujete výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="f83a8-121">A connection typically remains open until you consume the query results.</span></span> <span data-ttu-id="f83a8-122">Pokud očekáváte, že bude zpracování všech výsledků trvat déle a nemusíte proti nim ukládat výsledky do mezipaměti, <xref:System.Linq.Enumerable.ToList%2A> použijte dotaz.</span><span class="sxs-lookup"><span data-stu-id="f83a8-122">If you expect to take time to process all the results and are not opposed to caching the results, apply <xref:System.Linq.Enumerable.ToList%2A> to the query.</span></span> <span data-ttu-id="f83a8-123">V běžných scénářích, kdy se každý objekt zpracovává jenom jednou, je model streamování nadřazený v `DataReader` obou [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]i.</span><span class="sxs-lookup"><span data-stu-id="f83a8-123">In common scenarios where each object is processed only one time, the streaming model is superior in both `DataReader` and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

<span data-ttu-id="f83a8-124">Přesné podrobnosti o využití připojení závisí na následujících informacích:</span><span class="sxs-lookup"><span data-stu-id="f83a8-124">The exact details of connection usage depend on the following:</span></span>

- <span data-ttu-id="f83a8-125">Stav připojení, <xref:System.Data.Linq.DataContext> je-li objekt vytvořen pomocí objektu připojení.</span><span class="sxs-lookup"><span data-stu-id="f83a8-125">Connection status if the <xref:System.Data.Linq.DataContext> is constructed with a connection object.</span></span>

- <span data-ttu-id="f83a8-126">Nastavení připojovacího řetězce (například povolení více aktivních sad výsledků (MARS).</span><span class="sxs-lookup"><span data-stu-id="f83a8-126">Connection string settings (for example, enabling Multiple Active Result Sets (MARS).</span></span> <span data-ttu-id="f83a8-127">Další informace najdete v tématu [několik aktivních sad výsledků dotazu (MARS)](../multiple-active-result-sets-mars.md).</span><span class="sxs-lookup"><span data-stu-id="f83a8-127">For more information, see [Multiple Active Result Sets (MARS)](../multiple-active-result-sets-mars.md).</span></span>

## <a name="updating-without-querying"></a><span data-ttu-id="f83a8-128">Aktualizace bez dotazování</span><span class="sxs-lookup"><span data-stu-id="f83a8-128">Updating Without Querying</span></span>

<span data-ttu-id="f83a8-129">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-129">Q.</span></span> <span data-ttu-id="f83a8-130">Můžu aktualizovat data tabulky bez prvotního dotazování databáze?</span><span class="sxs-lookup"><span data-stu-id="f83a8-130">Can I update table data without first querying the database?</span></span>

<span data-ttu-id="f83a8-131">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-131">A.</span></span> <span data-ttu-id="f83a8-132">I [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] když nemá příkazy aktualizace založené na nastavení, můžete použít některý z následujících postupů k aktualizaci bez předchozího dotazování:</span><span class="sxs-lookup"><span data-stu-id="f83a8-132">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not have set-based update commands, you can use either of the following techniques to update without first querying:</span></span>

- <span data-ttu-id="f83a8-133">Použijte <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> k odeslání kódu SQL.</span><span class="sxs-lookup"><span data-stu-id="f83a8-133">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to send SQL code.</span></span>

- <span data-ttu-id="f83a8-134">Vytvořte novou instanci objektu a inicializujte všechny aktuální hodnoty (pole), které mají vliv na aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="f83a8-134">Create a new instance of the object and initialize all the current values (fields) that affect the update.</span></span> <span data-ttu-id="f83a8-135">Pak objekt připojte k <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.Table%601.Attach%2A> objektu pomocí a upravte pole, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="f83a8-135">Then attach the object to the <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.Table%601.Attach%2A> and modify the field you want to change.</span></span>

## <a name="unexpected-query-results"></a><span data-ttu-id="f83a8-136">Neočekávané výsledky dotazu</span><span class="sxs-lookup"><span data-stu-id="f83a8-136">Unexpected Query Results</span></span>

<span data-ttu-id="f83a8-137">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-137">Q.</span></span> <span data-ttu-id="f83a8-138">Dotaz vrací neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="f83a8-138">My query is returning unexpected results.</span></span> <span data-ttu-id="f83a8-139">Jak se dá zkontrolovat, co se děje?</span><span class="sxs-lookup"><span data-stu-id="f83a8-139">How can I inspect what is occurring?</span></span>

<span data-ttu-id="f83a8-140">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-140">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f83a8-141">poskytuje několik nástrojů pro kontrolu kódu SQL, který generuje.</span><span class="sxs-lookup"><span data-stu-id="f83a8-141">provides several tools for inspecting the SQL code it generates.</span></span> <span data-ttu-id="f83a8-142">Jedním z nejdůležitějších je <xref:System.Data.Linq.DataContext.Log%2A>.</span><span class="sxs-lookup"><span data-stu-id="f83a8-142">One of the most important is <xref:System.Data.Linq.DataContext.Log%2A>.</span></span> <span data-ttu-id="f83a8-143">Další informace najdete v tématu [Podpora ladění](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="f83a8-143">For more information, see [Debugging Support](debugging-support.md).</span></span>

## <a name="unexpected-stored-procedure-results"></a><span data-ttu-id="f83a8-144">Neočekávané výsledky uložených procedur</span><span class="sxs-lookup"><span data-stu-id="f83a8-144">Unexpected Stored Procedure Results</span></span>

<span data-ttu-id="f83a8-145">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-145">Q.</span></span> <span data-ttu-id="f83a8-146">Mám uloženou proceduru, jejíž návratová hodnota se `MAX()`počítá pomocí.</span><span class="sxs-lookup"><span data-stu-id="f83a8-146">I have a stored procedure whose return value is calculated by `MAX()`.</span></span> <span data-ttu-id="f83a8-147">Když přetáhnem uloženou proceduru na plochu návrháře O/R, návratová hodnota není správná.</span><span class="sxs-lookup"><span data-stu-id="f83a8-147">When I drag the stored procedure to the O/R Designer surface, the return value is not correct.</span></span>

<span data-ttu-id="f83a8-148">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-148">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f83a8-149">nabízí dva způsoby vrácení hodnot generovaných databází pomocí uložených procedur:</span><span class="sxs-lookup"><span data-stu-id="f83a8-149">provides two ways to return database-generated values by way of stored procedures:</span></span>

- <span data-ttu-id="f83a8-150">Pojmenováním výsledku výstupu.</span><span class="sxs-lookup"><span data-stu-id="f83a8-150">By naming the output result.</span></span>

- <span data-ttu-id="f83a8-151">Explicitním zadáním výstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="f83a8-151">By explicitly specifying an output parameter.</span></span>

<span data-ttu-id="f83a8-152">Následuje příklad nesprávného výstupu.</span><span class="sxs-lookup"><span data-stu-id="f83a8-152">The following is an example of incorrect output.</span></span> <span data-ttu-id="f83a8-153">Vzhledem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] k tomu, že nelze namapovat výsledky, vždy vrátí hodnotu 0:</span><span class="sxs-lookup"><span data-stu-id="f83a8-153">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot map the results, it always returns 0:</span></span>

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

<span data-ttu-id="f83a8-154">Následuje příklad správného výstupu pomocí parametru output:</span><span class="sxs-lookup"><span data-stu-id="f83a8-154">The following is an example of correct output by using an output parameter:</span></span>

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

<span data-ttu-id="f83a8-155">Následuje příklad správného výstupu pomocí pojmenování výsledku výstupu:</span><span class="sxs-lookup"><span data-stu-id="f83a8-155">The following is an example of correct output by naming the output result:</span></span>

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

<span data-ttu-id="f83a8-156">Další informace najdete v tématu [přizpůsobení operací pomocí uložených procedur](customizing-operations-by-using-stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f83a8-156">For more information, see [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md).</span></span>

## <a name="serialization-errors"></a><span data-ttu-id="f83a8-157">Chyby serializace</span><span class="sxs-lookup"><span data-stu-id="f83a8-157">Serialization Errors</span></span>

<span data-ttu-id="f83a8-158">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-158">Q.</span></span> <span data-ttu-id="f83a8-159">Při pokusu o serializaci se zobrazí následující chyba: Zadejte System. data. Linq. ChangeTracker + StandardChangeTracker... není označen jako serializovatelný. "</span><span class="sxs-lookup"><span data-stu-id="f83a8-159">When I try to serialize, I get the following error: "Type 'System.Data.Linq.ChangeTracker+StandardChangeTracker' ... is not marked as serializable."</span></span>

<span data-ttu-id="f83a8-160">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-160">A.</span></span> <span data-ttu-id="f83a8-161">Generování kódu v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nástroji <xref:System.Runtime.Serialization.DataContractSerializer> podporuje serializaci.</span><span class="sxs-lookup"><span data-stu-id="f83a8-161">Code generation in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports <xref:System.Runtime.Serialization.DataContractSerializer> serialization.</span></span> <span data-ttu-id="f83a8-162"><xref:System.Xml.Serialization.XmlSerializer> Nepodporuje nebo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="f83a8-162">It does not support <xref:System.Xml.Serialization.XmlSerializer> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="f83a8-163">Další informace naleznete v tématu [serializace](serialization.md).</span><span class="sxs-lookup"><span data-stu-id="f83a8-163">For more information, see [Serialization](serialization.md).</span></span>

## <a name="multiple-dbml-files"></a><span data-ttu-id="f83a8-164">Více souborů DBML</span><span class="sxs-lookup"><span data-stu-id="f83a8-164">Multiple DBML Files</span></span>

<span data-ttu-id="f83a8-165">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-165">Q.</span></span> <span data-ttu-id="f83a8-166">Když mám více souborů DBML, které sdílejí některé tabulky běžně, zobrazí se chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f83a8-166">When I have multiple DBML files that share some tables in common, I get a compiler error.</span></span>

<span data-ttu-id="f83a8-167">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-167">A.</span></span> <span data-ttu-id="f83a8-168">Nastavte **obor názvů kontextu** a vlastnosti **oboru názvů entit** z Návrhář relací objektů na jedinečnou hodnotu pro každý soubor DBML.</span><span class="sxs-lookup"><span data-stu-id="f83a8-168">Set the **Context Namespace** and **Entity Namespace** properties from the Object Relational Designer to a distinct value for each DBML file.</span></span> <span data-ttu-id="f83a8-169">Tento přístup eliminuje kolizi názvu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f83a8-169">This approach eliminates the name/namespace collision.</span></span>

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a><span data-ttu-id="f83a8-170">Zamezení explicitního nastavení hodnot generovaných databází při vkládání nebo aktualizaci</span><span class="sxs-lookup"><span data-stu-id="f83a8-170">Avoiding Explicit Setting of Database-Generated Values on Insert or Update</span></span>

<span data-ttu-id="f83a8-171">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-171">Q.</span></span> <span data-ttu-id="f83a8-172">Mám databázovou tabulku se `DateCreated` sloupcem, který je ve výchozím nastavení SQL. `Getdate()`</span><span class="sxs-lookup"><span data-stu-id="f83a8-172">I have a database table with a `DateCreated` column that defaults to SQL `Getdate()`.</span></span> <span data-ttu-id="f83a8-173">Když se pokusím vložit nový záznam pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], hodnota se nastaví na. `NULL`</span><span class="sxs-lookup"><span data-stu-id="f83a8-173">When I try to insert a new record by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the value gets set to `NULL`.</span></span> <span data-ttu-id="f83a8-174">Očekávalo se, že se má nastavit jako výchozí databáze.</span><span class="sxs-lookup"><span data-stu-id="f83a8-174">I would expect it to be set to the database default.</span></span>

<span data-ttu-id="f83a8-175">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-175">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f83a8-176">zpracovává tuto situaci automaticky pro identitu (Automatický přírůstek) a ROWGUIDCOL (GUID vygenerované databáze) a sloupce časového razítka.</span><span class="sxs-lookup"><span data-stu-id="f83a8-176">handles this situation automatically for identity (auto-increment) and rowguidcol (database-generated GUID) and timestamp columns.</span></span> <span data-ttu-id="f83a8-177">V <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> jiných případech byste měli nastavit a = = `true` <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> zadatvlastnosti/ ručně. <xref:System.Data.Linq.Mapping.AutoSync.Always> <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate></span><span class="sxs-lookup"><span data-stu-id="f83a8-177">In other cases, you should manually set <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` and <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> properties.</span></span>

## <a name="multiple-dataloadoptions"></a><span data-ttu-id="f83a8-178">Několik DataLoadOptions</span><span class="sxs-lookup"><span data-stu-id="f83a8-178">Multiple DataLoadOptions</span></span>

<span data-ttu-id="f83a8-179">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-179">Q.</span></span> <span data-ttu-id="f83a8-180">Můžu zadat další možnosti načítání bez přepsání prvního?</span><span class="sxs-lookup"><span data-stu-id="f83a8-180">Can I specify additional load options without overwriting the first?</span></span>

<span data-ttu-id="f83a8-181">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-181">A.</span></span> <span data-ttu-id="f83a8-182">Ano.</span><span class="sxs-lookup"><span data-stu-id="f83a8-182">Yes.</span></span> <span data-ttu-id="f83a8-183">První není přepsána, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f83a8-183">The first is not overwritten, as in the following example:</span></span>

```vb
Dim dlo As New DataLoadOptions()
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)
```

```csharp
DataLoadOptions dlo = new DataLoadOptions();
dlo.LoadWith<Order>(o => o.Customer);
dlo.LoadWith<Order>(o => o.OrderDetails);
```

## <a name="errors-using-sql-compact-35"></a><span data-ttu-id="f83a8-184">Chyby pomocí SQL Compact 3,5</span><span class="sxs-lookup"><span data-stu-id="f83a8-184">Errors Using SQL Compact 3.5</span></span>

<span data-ttu-id="f83a8-185">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-185">Q.</span></span> <span data-ttu-id="f83a8-186">Při přetahování tabulek z databáze SQL Server Compact 3,5 se zobrazí chyba.</span><span class="sxs-lookup"><span data-stu-id="f83a8-186">I get an error when I drag tables out of a SQL Server Compact 3.5 database.</span></span>

<span data-ttu-id="f83a8-187">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-187">A.</span></span> <span data-ttu-id="f83a8-188">Návrhář relací objektů nepodporuje SQL Server Compact 3,5, i když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modul runtime provádí.</span><span class="sxs-lookup"><span data-stu-id="f83a8-188">The Object Relational Designer does not support SQL Server Compact 3.5, although the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime does.</span></span> <span data-ttu-id="f83a8-189">V takovém případě je nutné vytvořit vlastní třídy entit a přidat příslušné atributy.</span><span class="sxs-lookup"><span data-stu-id="f83a8-189">In this situation, you must create your own entity classes and add the appropriate attributes.</span></span>

## <a name="errors-in-inheritance-relationships"></a><span data-ttu-id="f83a8-190">Chyby v relacích dědičnosti</span><span class="sxs-lookup"><span data-stu-id="f83a8-190">Errors in Inheritance Relationships</span></span>

<span data-ttu-id="f83a8-191">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-191">Q.</span></span> <span data-ttu-id="f83a8-192">Použil (a) jsem obrazec dědičnosti panelu nástrojů v Návrhář relací objektů k propojení dvou entit, ale zobrazí se chyby.</span><span class="sxs-lookup"><span data-stu-id="f83a8-192">I used the toolbox inheritance shape in the Object Relational Designer to connect two entities, but I get errors.</span></span>

<span data-ttu-id="f83a8-193">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-193">A.</span></span> <span data-ttu-id="f83a8-194">Vytvoření relace není dostatečné.</span><span class="sxs-lookup"><span data-stu-id="f83a8-194">Creating the relationship is not enough.</span></span> <span data-ttu-id="f83a8-195">Musíte zadat informace, jako je sloupec diskriminátor, hodnota diskriminátoru základní třídy a hodnota diskriminátoru odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="f83a8-195">You must provide information such as the discriminator column, base class discriminator value, and derived class discriminator value.</span></span>

## <a name="provider-model"></a><span data-ttu-id="f83a8-196">Model poskytovatele</span><span class="sxs-lookup"><span data-stu-id="f83a8-196">Provider Model</span></span>

<span data-ttu-id="f83a8-197">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-197">Q.</span></span> <span data-ttu-id="f83a8-198">Je k dispozici model veřejného poskytovatele?</span><span class="sxs-lookup"><span data-stu-id="f83a8-198">Is a public provider model available?</span></span>

<span data-ttu-id="f83a8-199">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-199">A.</span></span> <span data-ttu-id="f83a8-200">Není k dispozici žádný model veřejného poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="f83a8-200">No public provider model is available.</span></span> <span data-ttu-id="f83a8-201">V současné době [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje pouze SQL Server a SQL Server Compact 3,5.</span><span class="sxs-lookup"><span data-stu-id="f83a8-201">At this time, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports SQL Server and SQL Server Compact 3.5 only.</span></span>

## <a name="sql-injection-attacks"></a><span data-ttu-id="f83a8-202">Útoky prostřednictvím injektáže SQL</span><span class="sxs-lookup"><span data-stu-id="f83a8-202">SQL-Injection Attacks</span></span>

<span data-ttu-id="f83a8-203">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-203">Q.</span></span> <span data-ttu-id="f83a8-204">Jak je [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] chráněná proti útokům prostřednictvím injektáže SQL?</span><span class="sxs-lookup"><span data-stu-id="f83a8-204">How is [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protected from SQL-injection attacks?</span></span>

<span data-ttu-id="f83a8-205">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-205">A.</span></span> <span data-ttu-id="f83a8-206">Injektáže SQL bylo významně rizikové pro tradiční dotazy SQL vytvořené zřetězením uživatelského vstupu.</span><span class="sxs-lookup"><span data-stu-id="f83a8-206">SQL injection has been a significant risk for traditional SQL queries formed by concatenating user input.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f83a8-207">Nepoužívejte takové vložení pomocí <xref:System.Data.SqlClient.SqlParameter> v dotazech.</span><span class="sxs-lookup"><span data-stu-id="f83a8-207">avoids such injection by using <xref:System.Data.SqlClient.SqlParameter> in queries.</span></span> <span data-ttu-id="f83a8-208">Vstup uživatele je převeden do hodnot parametrů.</span><span class="sxs-lookup"><span data-stu-id="f83a8-208">User input is turned into parameter values.</span></span> <span data-ttu-id="f83a8-209">Tento přístup zabraňuje použití škodlivých příkazů ze vstupu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="f83a8-209">This approach prevents malicious commands from being used from customer input.</span></span>

## <a name="changing-read-only-flag-in-dbml-files"></a><span data-ttu-id="f83a8-210">Změna příznaku jen pro čtení v souborech DBML</span><span class="sxs-lookup"><span data-stu-id="f83a8-210">Changing Read-only Flag in DBML Files</span></span>

<span data-ttu-id="f83a8-211">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-211">Q.</span></span> <span data-ttu-id="f83a8-212">Při vytváření objektového modelu ze souboru DBML Návody eliminovat metody setter z některých vlastností?</span><span class="sxs-lookup"><span data-stu-id="f83a8-212">How do I eliminate setters from some properties when I create an object model from a DBML file?</span></span>

<span data-ttu-id="f83a8-213">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-213">A.</span></span> <span data-ttu-id="f83a8-214">V tomto pokročilém scénáři proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="f83a8-214">Take the following steps for this advanced scenario:</span></span>

1. <span data-ttu-id="f83a8-215">V souboru. dbml upravte vlastnost změnou <xref:System.Data.Linq.ITable.IsReadOnly%2A> příznaku na. `True`</span><span class="sxs-lookup"><span data-stu-id="f83a8-215">In the .dbml file, modify the property by changing the <xref:System.Data.Linq.ITable.IsReadOnly%2A> flag to `True`.</span></span>

2. <span data-ttu-id="f83a8-216">Přidejte částečnou třídu.</span><span class="sxs-lookup"><span data-stu-id="f83a8-216">Add a partial class.</span></span> <span data-ttu-id="f83a8-217">Vytvořte konstruktor s parametry pro členy jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f83a8-217">Create a constructor with parameters for the read-only members.</span></span>

3. <span data-ttu-id="f83a8-218">Zkontrolujte výchozí <xref:System.Data.Linq.Mapping.UpdateCheck> hodnotu (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) a určete, zda se jedná o správnou hodnotu pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f83a8-218">Review the default <xref:System.Data.Linq.Mapping.UpdateCheck> value (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) to determine whether that is the correct value for your application.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="f83a8-219">Pokud používáte Návrhář relací objektů v aplikaci Visual Studio, mohou být změny přepsány.</span><span class="sxs-lookup"><span data-stu-id="f83a8-219">If you are using the Object Relational Designer in Visual Studio, your changes might be overwritten.</span></span>

## <a name="aptca"></a><span data-ttu-id="f83a8-220">APTCA</span><span class="sxs-lookup"><span data-stu-id="f83a8-220">APTCA</span></span>

<span data-ttu-id="f83a8-221">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-221">Q.</span></span> <span data-ttu-id="f83a8-222">Je System. data. Linq označen pro použití částečně důvěryhodným kódem?</span><span class="sxs-lookup"><span data-stu-id="f83a8-222">Is System.Data.Linq marked for use by partially trusted code?</span></span>

<span data-ttu-id="f83a8-223">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-223">A.</span></span> <span data-ttu-id="f83a8-224">Ano, sestavení System. data. Linq. dll je mezi nimi .NET Framework sestavení označená <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="f83a8-224">Yes, the System.Data.Linq.dll assembly is among those .NET Framework assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="f83a8-225">Bez tohoto označení jsou sestavení v .NET Framework určena pouze pro použití plně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="f83a8-225">Without this marking, assemblies in the .NET Framework are intended for use only by fully trusted code.</span></span>

<span data-ttu-id="f83a8-226">Hlavní scénář v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nástroji pro povolení částečně důvěryhodným volajícím je [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] povolit přístup k sestavení z webových aplikací, kde je konfigurace *vztahu důvěryhodnosti* střední.</span><span class="sxs-lookup"><span data-stu-id="f83a8-226">The principal scenario in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] for allowing partially trusted callers is to enable the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly to be accessed from Web applications, where the *trust* configuration is Medium.</span></span>

## <a name="mapping-data-from-multiple-tables"></a><span data-ttu-id="f83a8-227">Mapování dat z více tabulek</span><span class="sxs-lookup"><span data-stu-id="f83a8-227">Mapping Data from Multiple Tables</span></span>

<span data-ttu-id="f83a8-228">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-228">Q.</span></span> <span data-ttu-id="f83a8-229">Data v mé entitě pocházejí z více tabulek.</span><span class="sxs-lookup"><span data-stu-id="f83a8-229">The data in my entity comes from multiple tables.</span></span> <span data-ttu-id="f83a8-230">Návody namapovat?</span><span class="sxs-lookup"><span data-stu-id="f83a8-230">How do I map it?</span></span>

<span data-ttu-id="f83a8-231">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-231">A.</span></span> <span data-ttu-id="f83a8-232">V databázi můžete vytvořit zobrazení a mapovat entitu na zobrazení.</span><span class="sxs-lookup"><span data-stu-id="f83a8-232">You can create a view in a database and map the entity to the view.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f83a8-233">generuje stejný SQL pro zobrazení v tabulkách.</span><span class="sxs-lookup"><span data-stu-id="f83a8-233">generates the same SQL for views as it does for tables.</span></span>

> [!NOTE]
> <span data-ttu-id="f83a8-234">Použití zobrazení v tomto scénáři má omezení.</span><span class="sxs-lookup"><span data-stu-id="f83a8-234">The use of views in this scenario has limitations.</span></span> <span data-ttu-id="f83a8-235">Tento přístup funguje nejvíce bezpečně, pokud jsou operace prováděné na základě <xref:System.Data.Linq.Table%601> základní zobrazení podporovány.</span><span class="sxs-lookup"><span data-stu-id="f83a8-235">This approach works most safely when the operations performed on <xref:System.Data.Linq.Table%601> are supported by the underlying view.</span></span> <span data-ttu-id="f83a8-236">Pouze víte, které operace jsou určeny.</span><span class="sxs-lookup"><span data-stu-id="f83a8-236">Only you know which operations are intended.</span></span> <span data-ttu-id="f83a8-237">Například většina aplikací je jen pro čtení a další výraznou `Create` číslo provádí / `Update` / `Delete` operace jenom pomocí uložených procedur pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="f83a8-237">For example, most applications are read-only, and another sizeable number perform `Create`/`Update`/`Delete` operations only by using stored procedures against views.</span></span>

## <a name="connection-pooling"></a><span data-ttu-id="f83a8-238">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="f83a8-238">Connection Pooling</span></span>

<span data-ttu-id="f83a8-239">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-239">Q.</span></span> <span data-ttu-id="f83a8-240">Je k dispozici konstrukce, která může <xref:System.Data.Linq.DataContext> pomáhat s sdružováním?</span><span class="sxs-lookup"><span data-stu-id="f83a8-240">Is there a construct that can help with <xref:System.Data.Linq.DataContext> pooling?</span></span>

<span data-ttu-id="f83a8-241">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-241">A.</span></span> <span data-ttu-id="f83a8-242">Nepokoušejte se znovu použít instance <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="f83a8-242">Do not try to reuse instances of <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="f83a8-243">Každá <xref:System.Data.Linq.DataContext> z nich udržuje stav (včetně mezipaměti identit) pro jednu konkrétní relaci úprav/dotazů.</span><span class="sxs-lookup"><span data-stu-id="f83a8-243">Each <xref:System.Data.Linq.DataContext> maintains state (including an identity cache) for one particular edit/query session.</span></span> <span data-ttu-id="f83a8-244">Chcete-li získat nové instance založené na aktuálním stavu databáze, použijte novou <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="f83a8-244">To obtain new instances based on the current state of the database, use a new <xref:System.Data.Linq.DataContext>.</span></span>

<span data-ttu-id="f83a8-245">Můžete dál používat základní sdružování připojení ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f83a8-245">You can still use underlying ADO.NET connection pooling.</span></span> <span data-ttu-id="f83a8-246">Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../../sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="f83a8-246">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../sql-server-connection-pooling.md).</span></span>

## <a name="second-datacontext-is-not-updated"></a><span data-ttu-id="f83a8-247">Druhý kontext kontextu není aktualizován.</span><span class="sxs-lookup"><span data-stu-id="f83a8-247">Second DataContext Is Not Updated</span></span>

<span data-ttu-id="f83a8-248">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-248">Q.</span></span> <span data-ttu-id="f83a8-249">Použil ( <xref:System.Data.Linq.DataContext> a) jsem jednu instanci pro ukládání hodnot do databáze.</span><span class="sxs-lookup"><span data-stu-id="f83a8-249">I used one instance of <xref:System.Data.Linq.DataContext> to store values in the database.</span></span> <span data-ttu-id="f83a8-250">Druhý <xref:System.Data.Linq.DataContext> ve stejné databázi ale neodráží aktualizované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f83a8-250">However, a second <xref:System.Data.Linq.DataContext> on the same database does not reflect the updated values.</span></span> <span data-ttu-id="f83a8-251">Druhá <xref:System.Data.Linq.DataContext> instance se jeví pro vrácení hodnot uložených v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f83a8-251">The second <xref:System.Data.Linq.DataContext> instance seems to return cached values.</span></span>

<span data-ttu-id="f83a8-252">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-252">A.</span></span> <span data-ttu-id="f83a8-253">Toto chování je záměrné.</span><span class="sxs-lookup"><span data-stu-id="f83a8-253">This behavior is by design.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f83a8-254">nadále vrací stejné instance nebo hodnoty, které jste viděli v první instanci.</span><span class="sxs-lookup"><span data-stu-id="f83a8-254">continues to return the same instances/values that you saw in the first instance.</span></span> <span data-ttu-id="f83a8-255">Při provádění aktualizací se používá Optimistická souběžnost.</span><span class="sxs-lookup"><span data-stu-id="f83a8-255">When you make updates, you use optimistic concurrency.</span></span> <span data-ttu-id="f83a8-256">Původní data se používají ke kontrole stavu aktuální databáze a k vyhodnocení, že se ve skutečnosti stále nezměnila.</span><span class="sxs-lookup"><span data-stu-id="f83a8-256">The original data is used to check against the current database state to assert that it is in fact still unchanged.</span></span> <span data-ttu-id="f83a8-257">Pokud došlo ke změně, dojde ke konfliktu a aplikace ji musí vyřešit.</span><span class="sxs-lookup"><span data-stu-id="f83a8-257">If it has changed, a conflict occurs and your application must resolve it.</span></span> <span data-ttu-id="f83a8-258">Jednou z možností aplikace je obnovit původní stav do stavu aktuální databáze a pokusit se o aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="f83a8-258">One option of your application is to reset the original state to the current database state and to try the update again.</span></span> <span data-ttu-id="f83a8-259">Další informace najdete v tématu [jak: Spravujte konflikty](how-to-manage-change-conflicts.md)změn.</span><span class="sxs-lookup"><span data-stu-id="f83a8-259">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>

<span data-ttu-id="f83a8-260">Můžete také nastavit <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> hodnotu false, která vypne ukládání do mezipaměti a sledování změn.</span><span class="sxs-lookup"><span data-stu-id="f83a8-260">You can also set <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to false, which turns off caching and change tracking.</span></span> <span data-ttu-id="f83a8-261">Pak můžete načíst nejnovější hodnoty pokaždé, když budete dotazováni.</span><span class="sxs-lookup"><span data-stu-id="f83a8-261">You can then retrieve the latest values every time that you query.</span></span>

## <a name="cannot-call-submitchanges-in-read-only-mode"></a><span data-ttu-id="f83a8-262">Nelze volat SubmitChanges v režimu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f83a8-262">Cannot Call SubmitChanges in Read-only Mode</span></span>

<span data-ttu-id="f83a8-263">Otázka:</span><span class="sxs-lookup"><span data-stu-id="f83a8-263">Q.</span></span> <span data-ttu-id="f83a8-264">Při pokusu o volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> v režimu jen pro čtení se zobrazí chyba.</span><span class="sxs-lookup"><span data-stu-id="f83a8-264">When I try to call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> in read-only mode, I get an error.</span></span>

<span data-ttu-id="f83a8-265">A.</span><span class="sxs-lookup"><span data-stu-id="f83a8-265">A.</span></span> <span data-ttu-id="f83a8-266">Režim jen pro čtení vypne schopnost kontextu sledovat změny.</span><span class="sxs-lookup"><span data-stu-id="f83a8-266">Read-only mode turns off the ability of the context to track changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="f83a8-267">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f83a8-267">See also</span></span>

- [<span data-ttu-id="f83a8-268">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="f83a8-268">Reference</span></span>](reference.md)
- [<span data-ttu-id="f83a8-269">Odstraňování potíží</span><span class="sxs-lookup"><span data-stu-id="f83a8-269">Troubleshooting</span></span>](troubleshooting.md)
- [<span data-ttu-id="f83a8-270">Zabezpečení v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="f83a8-270">Security in LINQ to SQL</span></span>](security-in-linq-to-sql.md)
