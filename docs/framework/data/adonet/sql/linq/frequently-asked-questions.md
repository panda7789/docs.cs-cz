---
title: Nejčastější dotazy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 3cc879e97438138554f1d39cf588e01bfbba28a6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634697"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="af468-102">Nejčastější dotazy</span><span class="sxs-lookup"><span data-stu-id="af468-102">Frequently Asked Questions</span></span>

<span data-ttu-id="af468-103">V následujících částech najdete odpovědi na některé běžné problémy, se kterými se můžete setkat při implementaci LINQ.</span><span class="sxs-lookup"><span data-stu-id="af468-103">The following sections answer some common issues that you might encounter when you implement LINQ.</span></span>

<span data-ttu-id="af468-104">Další problémy jsou řešeny při [řešení potíží](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="af468-104">Additional issues are addressed in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="cannot-connect"></a><span data-ttu-id="af468-105">Nejde se připojit</span><span class="sxs-lookup"><span data-stu-id="af468-105">Cannot Connect</span></span>

<span data-ttu-id="af468-106">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-106">Q.</span></span> <span data-ttu-id="af468-107">Nemůžu se připojit k databázi.</span><span class="sxs-lookup"><span data-stu-id="af468-107">I cannot connect to my database.</span></span>

<span data-ttu-id="af468-108">A.</span><span class="sxs-lookup"><span data-stu-id="af468-108">A.</span></span> <span data-ttu-id="af468-109">Ujistěte se, že je připojovací řetězec správný a že je spuštěná instance SQL Server.</span><span class="sxs-lookup"><span data-stu-id="af468-109">Make sure your connection string is correct and that your SQL Server instance is running.</span></span> <span data-ttu-id="af468-110">Všimněte si také, že [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vyžaduje, aby byl povolen protokol pojmenovaných kanálů.</span><span class="sxs-lookup"><span data-stu-id="af468-110">Note also that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requires the Named Pipes protocol to be enabled.</span></span> <span data-ttu-id="af468-111">Další informace najdete v tématu [výukové postupy](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="af468-111">For more information, see [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

## <a name="changes-to-database-lost"></a><span data-ttu-id="af468-112">Změny databáze ztraceny</span><span class="sxs-lookup"><span data-stu-id="af468-112">Changes to Database Lost</span></span>

<span data-ttu-id="af468-113">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-113">Q.</span></span> <span data-ttu-id="af468-114">Změnil (a) jsem data v databázi, ale při Reran své aplikace už tato změna neexistovala.</span><span class="sxs-lookup"><span data-stu-id="af468-114">I made a change to data in the database, but when I reran my application, the change was no longer there.</span></span>

<span data-ttu-id="af468-115">A.</span><span class="sxs-lookup"><span data-stu-id="af468-115">A.</span></span> <span data-ttu-id="af468-116">Ujistěte se, že zavoláte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> k uložení výsledků do databáze.</span><span class="sxs-lookup"><span data-stu-id="af468-116">Make sure that you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> to save results to the database.</span></span>

## <a name="database-connection-open-how-long"></a><span data-ttu-id="af468-117">Připojení k databázi: jak dlouho chcete otevřít?</span><span class="sxs-lookup"><span data-stu-id="af468-117">Database Connection: Open How Long?</span></span>

<span data-ttu-id="af468-118">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-118">Q.</span></span> <span data-ttu-id="af468-119">Jak dlouho zůstane moje připojení k databázi otevřené?</span><span class="sxs-lookup"><span data-stu-id="af468-119">How long does my database connection remain open?</span></span>

<span data-ttu-id="af468-120">A.</span><span class="sxs-lookup"><span data-stu-id="af468-120">A.</span></span> <span data-ttu-id="af468-121">Připojení obvykle zůstává otevřené, dokud nespotřebujete výsledky dotazu.</span><span class="sxs-lookup"><span data-stu-id="af468-121">A connection typically remains open until you consume the query results.</span></span> <span data-ttu-id="af468-122">Pokud očekáváte, že bude zpracování všech výsledků trvat déle a nejste proti výsledkům ukládání do mezipaměti, použijte pro dotaz <xref:System.Linq.Enumerable.ToList%2A>.</span><span class="sxs-lookup"><span data-stu-id="af468-122">If you expect to take time to process all the results and are not opposed to caching the results, apply <xref:System.Linq.Enumerable.ToList%2A> to the query.</span></span> <span data-ttu-id="af468-123">V běžných scénářích, kdy se každý objekt zpracovává jenom jednou, je model streamování nadřazený v `DataReader` i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af468-123">In common scenarios where each object is processed only one time, the streaming model is superior in both `DataReader` and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

<span data-ttu-id="af468-124">Přesné podrobnosti o využití připojení závisí na následujících informacích:</span><span class="sxs-lookup"><span data-stu-id="af468-124">The exact details of connection usage depend on the following:</span></span>

- <span data-ttu-id="af468-125">Stav připojení, je-li <xref:System.Data.Linq.DataContext> vytvořen pomocí objektu připojení.</span><span class="sxs-lookup"><span data-stu-id="af468-125">Connection status if the <xref:System.Data.Linq.DataContext> is constructed with a connection object.</span></span>

- <span data-ttu-id="af468-126">Nastavení připojovacího řetězce (například povolení více aktivních sad výsledků (MARS).</span><span class="sxs-lookup"><span data-stu-id="af468-126">Connection string settings (for example, enabling Multiple Active Result Sets (MARS).</span></span> <span data-ttu-id="af468-127">Další informace najdete v tématu [několik aktivních sad výsledků dotazu (MARS)](../multiple-active-result-sets-mars.md).</span><span class="sxs-lookup"><span data-stu-id="af468-127">For more information, see [Multiple Active Result Sets (MARS)](../multiple-active-result-sets-mars.md).</span></span>

## <a name="updating-without-querying"></a><span data-ttu-id="af468-128">Aktualizace bez dotazování</span><span class="sxs-lookup"><span data-stu-id="af468-128">Updating Without Querying</span></span>

<span data-ttu-id="af468-129">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-129">Q.</span></span> <span data-ttu-id="af468-130">Můžu aktualizovat data tabulky bez prvotního dotazování databáze?</span><span class="sxs-lookup"><span data-stu-id="af468-130">Can I update table data without first querying the database?</span></span>

<span data-ttu-id="af468-131">A.</span><span class="sxs-lookup"><span data-stu-id="af468-131">A.</span></span> <span data-ttu-id="af468-132">I když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemá příkazy aktualizace založené na nastavení, můžete použít některý z následujících postupů k aktualizaci bez předchozího dotazování:</span><span class="sxs-lookup"><span data-stu-id="af468-132">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not have set-based update commands, you can use either of the following techniques to update without first querying:</span></span>

- <span data-ttu-id="af468-133">K odeslání kódu SQL použijte <xref:System.Data.Linq.DataContext.ExecuteCommand%2A>.</span><span class="sxs-lookup"><span data-stu-id="af468-133">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to send SQL code.</span></span>

- <span data-ttu-id="af468-134">Vytvořte novou instanci objektu a inicializujte všechny aktuální hodnoty (pole), které mají vliv na aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="af468-134">Create a new instance of the object and initialize all the current values (fields) that affect the update.</span></span> <span data-ttu-id="af468-135">Pak objekt připojte k <xref:System.Data.Linq.DataContext> pomocí <xref:System.Data.Linq.Table%601.Attach%2A> a upravte pole, které chcete změnit.</span><span class="sxs-lookup"><span data-stu-id="af468-135">Then attach the object to the <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.Table%601.Attach%2A> and modify the field you want to change.</span></span>

## <a name="unexpected-query-results"></a><span data-ttu-id="af468-136">Neočekávané výsledky dotazu</span><span class="sxs-lookup"><span data-stu-id="af468-136">Unexpected Query Results</span></span>

<span data-ttu-id="af468-137">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-137">Q.</span></span> <span data-ttu-id="af468-138">Dotaz vrací neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="af468-138">My query is returning unexpected results.</span></span> <span data-ttu-id="af468-139">Jak se dá zkontrolovat, co se děje?</span><span class="sxs-lookup"><span data-stu-id="af468-139">How can I inspect what is occurring?</span></span>

<span data-ttu-id="af468-140">A.</span><span class="sxs-lookup"><span data-stu-id="af468-140">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="af468-141">poskytuje několik nástrojů pro kontrolu kódu SQL, který generuje.</span><span class="sxs-lookup"><span data-stu-id="af468-141">provides several tools for inspecting the SQL code it generates.</span></span> <span data-ttu-id="af468-142">Jedním z nejdůležitějších je <xref:System.Data.Linq.DataContext.Log%2A>.</span><span class="sxs-lookup"><span data-stu-id="af468-142">One of the most important is <xref:System.Data.Linq.DataContext.Log%2A>.</span></span> <span data-ttu-id="af468-143">Další informace najdete v tématu [Podpora ladění](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="af468-143">For more information, see [Debugging Support](debugging-support.md).</span></span>

## <a name="unexpected-stored-procedure-results"></a><span data-ttu-id="af468-144">Neočekávané výsledky uložených procedur</span><span class="sxs-lookup"><span data-stu-id="af468-144">Unexpected Stored Procedure Results</span></span>

<span data-ttu-id="af468-145">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-145">Q.</span></span> <span data-ttu-id="af468-146">Mám uloženou proceduru, jejíž návratová hodnota se počítá pomocí `MAX()`.</span><span class="sxs-lookup"><span data-stu-id="af468-146">I have a stored procedure whose return value is calculated by `MAX()`.</span></span> <span data-ttu-id="af468-147">Když přetáhnem uloženou proceduru na plochu návrháře O/R, návratová hodnota není správná.</span><span class="sxs-lookup"><span data-stu-id="af468-147">When I drag the stored procedure to the O/R Designer surface, the return value is not correct.</span></span>

<span data-ttu-id="af468-148">A.</span><span class="sxs-lookup"><span data-stu-id="af468-148">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="af468-149">poskytuje dva způsoby, jak vrátit hodnoty generované databází pomocí uložených procedur:</span><span class="sxs-lookup"><span data-stu-id="af468-149">provides two ways to return database-generated values by way of stored procedures:</span></span>

- <span data-ttu-id="af468-150">Pojmenováním výsledku výstupu.</span><span class="sxs-lookup"><span data-stu-id="af468-150">By naming the output result.</span></span>

- <span data-ttu-id="af468-151">Explicitním zadáním výstupního parametru.</span><span class="sxs-lookup"><span data-stu-id="af468-151">By explicitly specifying an output parameter.</span></span>

<span data-ttu-id="af468-152">Následuje příklad nesprávného výstupu.</span><span class="sxs-lookup"><span data-stu-id="af468-152">The following is an example of incorrect output.</span></span> <span data-ttu-id="af468-153">Vzhledem k tomu, že [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemůže namapovat výsledky, vždy vrátí hodnotu 0:</span><span class="sxs-lookup"><span data-stu-id="af468-153">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot map the results, it always returns 0:</span></span>

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

<span data-ttu-id="af468-154">Následuje příklad správného výstupu pomocí parametru output:</span><span class="sxs-lookup"><span data-stu-id="af468-154">The following is an example of correct output by using an output parameter:</span></span>

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

<span data-ttu-id="af468-155">Následuje příklad správného výstupu pomocí pojmenování výsledku výstupu:</span><span class="sxs-lookup"><span data-stu-id="af468-155">The following is an example of correct output by naming the output result:</span></span>

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

<span data-ttu-id="af468-156">Další informace najdete v tématu [přizpůsobení operací pomocí uložených procedur](customizing-operations-by-using-stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="af468-156">For more information, see [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md).</span></span>

## <a name="serialization-errors"></a><span data-ttu-id="af468-157">Chyby serializace</span><span class="sxs-lookup"><span data-stu-id="af468-157">Serialization Errors</span></span>

<span data-ttu-id="af468-158">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-158">Q.</span></span> <span data-ttu-id="af468-159">Při pokusu o serializaci se zobrazí následující chyba: "Type ' System. data. Linq. ChangeTracker + StandardChangeTracker '... není označen jako serializovatelný. "</span><span class="sxs-lookup"><span data-stu-id="af468-159">When I try to serialize, I get the following error: "Type 'System.Data.Linq.ChangeTracker+StandardChangeTracker' ... is not marked as serializable."</span></span>

<span data-ttu-id="af468-160">A.</span><span class="sxs-lookup"><span data-stu-id="af468-160">A.</span></span> <span data-ttu-id="af468-161">Generování kódu v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje serializaci <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="af468-161">Code generation in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports <xref:System.Runtime.Serialization.DataContractSerializer> serialization.</span></span> <span data-ttu-id="af468-162">Nepodporuje <xref:System.Xml.Serialization.XmlSerializer> ani <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="af468-162">It does not support <xref:System.Xml.Serialization.XmlSerializer> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="af468-163">Další informace naleznete v tématu [serializace](serialization.md).</span><span class="sxs-lookup"><span data-stu-id="af468-163">For more information, see [Serialization](serialization.md).</span></span>

## <a name="multiple-dbml-files"></a><span data-ttu-id="af468-164">Více souborů DBML</span><span class="sxs-lookup"><span data-stu-id="af468-164">Multiple DBML Files</span></span>

<span data-ttu-id="af468-165">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-165">Q.</span></span> <span data-ttu-id="af468-166">Když mám více souborů DBML, které sdílejí některé tabulky běžně, zobrazí se chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="af468-166">When I have multiple DBML files that share some tables in common, I get a compiler error.</span></span>

<span data-ttu-id="af468-167">A.</span><span class="sxs-lookup"><span data-stu-id="af468-167">A.</span></span> <span data-ttu-id="af468-168">Nastavte **obor názvů kontextu** a vlastnosti **oboru názvů entit** z Návrhář relací objektů na jedinečnou hodnotu pro každý soubor DBML.</span><span class="sxs-lookup"><span data-stu-id="af468-168">Set the **Context Namespace** and **Entity Namespace** properties from the Object Relational Designer to a distinct value for each DBML file.</span></span> <span data-ttu-id="af468-169">Tento přístup eliminuje kolizi názvu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="af468-169">This approach eliminates the name/namespace collision.</span></span>

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a><span data-ttu-id="af468-170">Zamezení explicitního nastavení hodnot generovaných databází při vkládání nebo aktualizaci</span><span class="sxs-lookup"><span data-stu-id="af468-170">Avoiding Explicit Setting of Database-Generated Values on Insert or Update</span></span>

<span data-ttu-id="af468-171">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-171">Q.</span></span> <span data-ttu-id="af468-172">Mám databázovou tabulku s `DateCreated`ovým sloupcem, ve kterém je výchozí nastavení SQL `Getdate()`.</span><span class="sxs-lookup"><span data-stu-id="af468-172">I have a database table with a `DateCreated` column that defaults to SQL `Getdate()`.</span></span> <span data-ttu-id="af468-173">Při pokusu o vložení nového záznamu pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]je hodnota nastavena na `NULL`.</span><span class="sxs-lookup"><span data-stu-id="af468-173">When I try to insert a new record by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the value gets set to `NULL`.</span></span> <span data-ttu-id="af468-174">Očekávalo se, že se má nastavit jako výchozí databáze.</span><span class="sxs-lookup"><span data-stu-id="af468-174">I would expect it to be set to the database default.</span></span>

<span data-ttu-id="af468-175">A.</span><span class="sxs-lookup"><span data-stu-id="af468-175">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="af468-176">zpracovává tuto situaci automaticky pro identitu (Automatický přírůstek) a ROWGUIDCOL (GUID vygenerované databáze) a sloupce časového razítka.</span><span class="sxs-lookup"><span data-stu-id="af468-176">handles this situation automatically for identity (auto-increment) and rowguidcol (database-generated GUID) and timestamp columns.</span></span> <span data-ttu-id="af468-177">V jiných případech byste měli ručně nastavit <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` a <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="af468-177">In other cases, you should manually set <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` and <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> properties.</span></span>

## <a name="multiple-dataloadoptions"></a><span data-ttu-id="af468-178">Několik DataLoadOptions</span><span class="sxs-lookup"><span data-stu-id="af468-178">Multiple DataLoadOptions</span></span>

<span data-ttu-id="af468-179">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-179">Q.</span></span> <span data-ttu-id="af468-180">Můžu zadat další možnosti načítání bez přepsání prvního?</span><span class="sxs-lookup"><span data-stu-id="af468-180">Can I specify additional load options without overwriting the first?</span></span>

<span data-ttu-id="af468-181">A.</span><span class="sxs-lookup"><span data-stu-id="af468-181">A.</span></span> <span data-ttu-id="af468-182">Ano.</span><span class="sxs-lookup"><span data-stu-id="af468-182">Yes.</span></span> <span data-ttu-id="af468-183">První není přepsána, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="af468-183">The first is not overwritten, as in the following example:</span></span>

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

## <a name="errors-using-sql-compact-35"></a><span data-ttu-id="af468-184">Chyby pomocí SQL Compact 3,5</span><span class="sxs-lookup"><span data-stu-id="af468-184">Errors Using SQL Compact 3.5</span></span>

<span data-ttu-id="af468-185">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-185">Q.</span></span> <span data-ttu-id="af468-186">Při přetahování tabulek z databáze SQL Server Compact 3,5 se zobrazí chyba.</span><span class="sxs-lookup"><span data-stu-id="af468-186">I get an error when I drag tables out of a SQL Server Compact 3.5 database.</span></span>

<span data-ttu-id="af468-187">A.</span><span class="sxs-lookup"><span data-stu-id="af468-187">A.</span></span> <span data-ttu-id="af468-188">Návrhář relací objektů nepodporuje SQL Server Compact 3,5, i když modul runtime [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af468-188">The Object Relational Designer does not support SQL Server Compact 3.5, although the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime does.</span></span> <span data-ttu-id="af468-189">V takovém případě je nutné vytvořit vlastní třídy entit a přidat příslušné atributy.</span><span class="sxs-lookup"><span data-stu-id="af468-189">In this situation, you must create your own entity classes and add the appropriate attributes.</span></span>

## <a name="errors-in-inheritance-relationships"></a><span data-ttu-id="af468-190">Chyby v relacích dědičnosti</span><span class="sxs-lookup"><span data-stu-id="af468-190">Errors in Inheritance Relationships</span></span>

<span data-ttu-id="af468-191">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-191">Q.</span></span> <span data-ttu-id="af468-192">Použil (a) jsem obrazec dědičnosti panelu nástrojů v Návrhář relací objektů k propojení dvou entit, ale zobrazí se chyby.</span><span class="sxs-lookup"><span data-stu-id="af468-192">I used the toolbox inheritance shape in the Object Relational Designer to connect two entities, but I get errors.</span></span>

<span data-ttu-id="af468-193">A.</span><span class="sxs-lookup"><span data-stu-id="af468-193">A.</span></span> <span data-ttu-id="af468-194">Vytvoření relace není dostatečné.</span><span class="sxs-lookup"><span data-stu-id="af468-194">Creating the relationship is not enough.</span></span> <span data-ttu-id="af468-195">Musíte zadat informace, jako je sloupec diskriminátor, hodnota diskriminátoru základní třídy a hodnota diskriminátoru odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="af468-195">You must provide information such as the discriminator column, base class discriminator value, and derived class discriminator value.</span></span>

## <a name="provider-model"></a><span data-ttu-id="af468-196">Model poskytovatele</span><span class="sxs-lookup"><span data-stu-id="af468-196">Provider Model</span></span>

<span data-ttu-id="af468-197">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-197">Q.</span></span> <span data-ttu-id="af468-198">Je k dispozici model veřejného poskytovatele?</span><span class="sxs-lookup"><span data-stu-id="af468-198">Is a public provider model available?</span></span>

<span data-ttu-id="af468-199">A.</span><span class="sxs-lookup"><span data-stu-id="af468-199">A.</span></span> <span data-ttu-id="af468-200">Není k dispozici žádný model veřejného poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="af468-200">No public provider model is available.</span></span> <span data-ttu-id="af468-201">V tuto chvíli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje jenom SQL Server a SQL Server Compact 3,5.</span><span class="sxs-lookup"><span data-stu-id="af468-201">At this time, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports SQL Server and SQL Server Compact 3.5 only.</span></span>

## <a name="sql-injection-attacks"></a><span data-ttu-id="af468-202">Útoky prostřednictvím injektáže SQL</span><span class="sxs-lookup"><span data-stu-id="af468-202">SQL-Injection Attacks</span></span>

<span data-ttu-id="af468-203">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-203">Q.</span></span> <span data-ttu-id="af468-204">Jak se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] chránit před útoky prostřednictvím injektáže SQL?</span><span class="sxs-lookup"><span data-stu-id="af468-204">How is [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protected from SQL-injection attacks?</span></span>

<span data-ttu-id="af468-205">A.</span><span class="sxs-lookup"><span data-stu-id="af468-205">A.</span></span> <span data-ttu-id="af468-206">Injektáže SQL bylo významně rizikové pro tradiční dotazy SQL vytvořené zřetězením uživatelského vstupu.</span><span class="sxs-lookup"><span data-stu-id="af468-206">SQL injection has been a significant risk for traditional SQL queries formed by concatenating user input.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="af468-207">se vyhnout takovému vložení pomocí <xref:System.Data.SqlClient.SqlParameter> v dotazech.</span><span class="sxs-lookup"><span data-stu-id="af468-207">avoids such injection by using <xref:System.Data.SqlClient.SqlParameter> in queries.</span></span> <span data-ttu-id="af468-208">Vstup uživatele je převeden do hodnot parametrů.</span><span class="sxs-lookup"><span data-stu-id="af468-208">User input is turned into parameter values.</span></span> <span data-ttu-id="af468-209">Tento přístup zabraňuje použití škodlivých příkazů ze vstupu zákazníka.</span><span class="sxs-lookup"><span data-stu-id="af468-209">This approach prevents malicious commands from being used from customer input.</span></span>

## <a name="changing-read-only-flag-in-dbml-files"></a><span data-ttu-id="af468-210">Změna příznaku jen pro čtení v souborech DBML</span><span class="sxs-lookup"><span data-stu-id="af468-210">Changing Read-only Flag in DBML Files</span></span>

<span data-ttu-id="af468-211">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-211">Q.</span></span> <span data-ttu-id="af468-212">Při vytváření objektového modelu ze souboru DBML Návody eliminovat metody setter z některých vlastností?</span><span class="sxs-lookup"><span data-stu-id="af468-212">How do I eliminate setters from some properties when I create an object model from a DBML file?</span></span>

<span data-ttu-id="af468-213">A.</span><span class="sxs-lookup"><span data-stu-id="af468-213">A.</span></span> <span data-ttu-id="af468-214">V tomto pokročilém scénáři proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="af468-214">Take the following steps for this advanced scenario:</span></span>

1. <span data-ttu-id="af468-215">V souboru. dbml upravte vlastnost změnou příznaku <xref:System.Data.Linq.ITable.IsReadOnly%2A> na `True`.</span><span class="sxs-lookup"><span data-stu-id="af468-215">In the .dbml file, modify the property by changing the <xref:System.Data.Linq.ITable.IsReadOnly%2A> flag to `True`.</span></span>

2. <span data-ttu-id="af468-216">Přidejte částečnou třídu.</span><span class="sxs-lookup"><span data-stu-id="af468-216">Add a partial class.</span></span> <span data-ttu-id="af468-217">Vytvořte konstruktor s parametry pro členy jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="af468-217">Create a constructor with parameters for the read-only members.</span></span>

3. <span data-ttu-id="af468-218">Zkontrolujte výchozí hodnotu <xref:System.Data.Linq.Mapping.UpdateCheck> (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>), abyste zjistili, jestli je to správná hodnota pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="af468-218">Review the default <xref:System.Data.Linq.Mapping.UpdateCheck> value (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) to determine whether that is the correct value for your application.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="af468-219">Pokud používáte Návrhář relací objektů v aplikaci Visual Studio, mohou být změny přepsány.</span><span class="sxs-lookup"><span data-stu-id="af468-219">If you are using the Object Relational Designer in Visual Studio, your changes might be overwritten.</span></span>

## <a name="aptca"></a><span data-ttu-id="af468-220">APTCA</span><span class="sxs-lookup"><span data-stu-id="af468-220">APTCA</span></span>

<span data-ttu-id="af468-221">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-221">Q.</span></span> <span data-ttu-id="af468-222">Je System. data. Linq označen pro použití částečně důvěryhodným kódem?</span><span class="sxs-lookup"><span data-stu-id="af468-222">Is System.Data.Linq marked for use by partially trusted code?</span></span>

<span data-ttu-id="af468-223">A.</span><span class="sxs-lookup"><span data-stu-id="af468-223">A.</span></span> <span data-ttu-id="af468-224">Ano, sestavení System. data. Linq. dll je mezi nimi .NET Framework sestavení označená atributem <xref:System.Security.AllowPartiallyTrustedCallersAttribute>.</span><span class="sxs-lookup"><span data-stu-id="af468-224">Yes, the System.Data.Linq.dll assembly is among those .NET Framework assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="af468-225">Bez tohoto označení jsou sestavení v .NET Framework určena pouze pro použití plně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="af468-225">Without this marking, assemblies in the .NET Framework are intended for use only by fully trusted code.</span></span>

<span data-ttu-id="af468-226">Hlavní scénář v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pro povolení částečně důvěryhodným volajícím je povolit přístup k [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sestavení z webových aplikací, kde je konfigurace *vztahu důvěryhodnosti* střední.</span><span class="sxs-lookup"><span data-stu-id="af468-226">The principal scenario in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] for allowing partially trusted callers is to enable the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly to be accessed from Web applications, where the *trust* configuration is Medium.</span></span>

## <a name="mapping-data-from-multiple-tables"></a><span data-ttu-id="af468-227">Mapování dat z více tabulek</span><span class="sxs-lookup"><span data-stu-id="af468-227">Mapping Data from Multiple Tables</span></span>

<span data-ttu-id="af468-228">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-228">Q.</span></span> <span data-ttu-id="af468-229">Data v mé entitě pocházejí z více tabulek.</span><span class="sxs-lookup"><span data-stu-id="af468-229">The data in my entity comes from multiple tables.</span></span> <span data-ttu-id="af468-230">Návody namapovat?</span><span class="sxs-lookup"><span data-stu-id="af468-230">How do I map it?</span></span>

<span data-ttu-id="af468-231">A.</span><span class="sxs-lookup"><span data-stu-id="af468-231">A.</span></span> <span data-ttu-id="af468-232">V databázi můžete vytvořit zobrazení a mapovat entitu na zobrazení.</span><span class="sxs-lookup"><span data-stu-id="af468-232">You can create a view in a database and map the entity to the view.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="af468-233">generuje stejný SQL pro zobrazení v tabulkách.</span><span class="sxs-lookup"><span data-stu-id="af468-233">generates the same SQL for views as it does for tables.</span></span>

> [!NOTE]
> <span data-ttu-id="af468-234">Použití zobrazení v tomto scénáři má omezení.</span><span class="sxs-lookup"><span data-stu-id="af468-234">The use of views in this scenario has limitations.</span></span> <span data-ttu-id="af468-235">Tento přístup funguje nejvíce bezpečně, pokud jsou operace prováděné na <xref:System.Data.Linq.Table%601> podporovány podkladovým zobrazením.</span><span class="sxs-lookup"><span data-stu-id="af468-235">This approach works most safely when the operations performed on <xref:System.Data.Linq.Table%601> are supported by the underlying view.</span></span> <span data-ttu-id="af468-236">Pouze víte, které operace jsou určeny.</span><span class="sxs-lookup"><span data-stu-id="af468-236">Only you know which operations are intended.</span></span> <span data-ttu-id="af468-237">Například většina aplikací je jen pro čtení a další výraznou číslo provádí `Create`/`Update`/`Delete`ch operací jenom pomocí uložených procedur pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="af468-237">For example, most applications are read-only, and another sizeable number perform `Create`/`Update`/`Delete` operations only by using stored procedures against views.</span></span>

## <a name="connection-pooling"></a><span data-ttu-id="af468-238">Sdružování připojení</span><span class="sxs-lookup"><span data-stu-id="af468-238">Connection Pooling</span></span>

<span data-ttu-id="af468-239">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-239">Q.</span></span> <span data-ttu-id="af468-240">Je k dispozici konstrukce, která může pomáhat s <xref:System.Data.Linq.DataContext> sdružováním?</span><span class="sxs-lookup"><span data-stu-id="af468-240">Is there a construct that can help with <xref:System.Data.Linq.DataContext> pooling?</span></span>

<span data-ttu-id="af468-241">A.</span><span class="sxs-lookup"><span data-stu-id="af468-241">A.</span></span> <span data-ttu-id="af468-242">Nepokoušejte se znovu použít instance <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="af468-242">Do not try to reuse instances of <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="af468-243">Každý <xref:System.Data.Linq.DataContext> udržuje stav (včetně mezipaměti identit) pro jednu konkrétní relaci úprav/dotazů.</span><span class="sxs-lookup"><span data-stu-id="af468-243">Each <xref:System.Data.Linq.DataContext> maintains state (including an identity cache) for one particular edit/query session.</span></span> <span data-ttu-id="af468-244">Chcete-li získat nové instance založené na aktuálním stavu databáze, použijte novou <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="af468-244">To obtain new instances based on the current state of the database, use a new <xref:System.Data.Linq.DataContext>.</span></span>

<span data-ttu-id="af468-245">Můžete dál používat základní sdružování připojení ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="af468-245">You can still use underlying ADO.NET connection pooling.</span></span> <span data-ttu-id="af468-246">Další informace najdete v tématu věnovaném [sdružování připojení SQL Server (ADO.NET)](../../sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="af468-246">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../sql-server-connection-pooling.md).</span></span>

## <a name="second-datacontext-is-not-updated"></a><span data-ttu-id="af468-247">Druhý kontext kontextu není aktualizován.</span><span class="sxs-lookup"><span data-stu-id="af468-247">Second DataContext Is Not Updated</span></span>

<span data-ttu-id="af468-248">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-248">Q.</span></span> <span data-ttu-id="af468-249">Použil (a) jsem jednu instanci <xref:System.Data.Linq.DataContext> k uložení hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="af468-249">I used one instance of <xref:System.Data.Linq.DataContext> to store values in the database.</span></span> <span data-ttu-id="af468-250">Druhý <xref:System.Data.Linq.DataContext> ve stejné databázi ale neodráží aktualizované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="af468-250">However, a second <xref:System.Data.Linq.DataContext> on the same database does not reflect the updated values.</span></span> <span data-ttu-id="af468-251">Druhá instance <xref:System.Data.Linq.DataContext> pravděpodobně vrátila hodnoty uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="af468-251">The second <xref:System.Data.Linq.DataContext> instance seems to return cached values.</span></span>

<span data-ttu-id="af468-252">A.</span><span class="sxs-lookup"><span data-stu-id="af468-252">A.</span></span> <span data-ttu-id="af468-253">Toto chování je záměrné.</span><span class="sxs-lookup"><span data-stu-id="af468-253">This behavior is by design.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="af468-254">nadále vrací stejné instance nebo hodnoty, které jste viděli v první instanci.</span><span class="sxs-lookup"><span data-stu-id="af468-254">continues to return the same instances/values that you saw in the first instance.</span></span> <span data-ttu-id="af468-255">Při provádění aktualizací se používá Optimistická souběžnost.</span><span class="sxs-lookup"><span data-stu-id="af468-255">When you make updates, you use optimistic concurrency.</span></span> <span data-ttu-id="af468-256">Původní data se používají ke kontrole stavu aktuální databáze a k vyhodnocení, že se ve skutečnosti stále nezměnila.</span><span class="sxs-lookup"><span data-stu-id="af468-256">The original data is used to check against the current database state to assert that it is in fact still unchanged.</span></span> <span data-ttu-id="af468-257">Pokud došlo ke změně, dojde ke konfliktu a aplikace ji musí vyřešit.</span><span class="sxs-lookup"><span data-stu-id="af468-257">If it has changed, a conflict occurs and your application must resolve it.</span></span> <span data-ttu-id="af468-258">Jednou z možností aplikace je obnovit původní stav do stavu aktuální databáze a pokusit se o aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="af468-258">One option of your application is to reset the original state to the current database state and to try the update again.</span></span> <span data-ttu-id="af468-259">Další informace najdete v tématu [How to: Manage Change konflikty](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="af468-259">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>

<span data-ttu-id="af468-260">Můžete také nastavit <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> na false, což vypne ukládání do mezipaměti a sledování změn.</span><span class="sxs-lookup"><span data-stu-id="af468-260">You can also set <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to false, which turns off caching and change tracking.</span></span> <span data-ttu-id="af468-261">Pak můžete načíst nejnovější hodnoty pokaždé, když budete dotazováni.</span><span class="sxs-lookup"><span data-stu-id="af468-261">You can then retrieve the latest values every time that you query.</span></span>

## <a name="cannot-call-submitchanges-in-read-only-mode"></a><span data-ttu-id="af468-262">Nelze volat SubmitChanges v režimu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="af468-262">Cannot Call SubmitChanges in Read-only Mode</span></span>

<span data-ttu-id="af468-263">Otázka:</span><span class="sxs-lookup"><span data-stu-id="af468-263">Q.</span></span> <span data-ttu-id="af468-264">Při pokusu o volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> v režimu jen pro čtení se zobrazí chyba.</span><span class="sxs-lookup"><span data-stu-id="af468-264">When I try to call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> in read-only mode, I get an error.</span></span>

<span data-ttu-id="af468-265">A.</span><span class="sxs-lookup"><span data-stu-id="af468-265">A.</span></span> <span data-ttu-id="af468-266">Režim jen pro čtení vypne schopnost kontextu sledovat změny.</span><span class="sxs-lookup"><span data-stu-id="af468-266">Read-only mode turns off the ability of the context to track changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="af468-267">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af468-267">See also</span></span>

- [<span data-ttu-id="af468-268">Odkazy</span><span class="sxs-lookup"><span data-stu-id="af468-268">Reference</span></span>](reference.md)
- [<span data-ttu-id="af468-269">Odstraňování potíží</span><span class="sxs-lookup"><span data-stu-id="af468-269">Troubleshooting</span></span>](troubleshooting.md)
- [<span data-ttu-id="af468-270">Zabezpečení v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="af468-270">Security in LINQ to SQL</span></span>](security-in-linq-to-sql.md)
