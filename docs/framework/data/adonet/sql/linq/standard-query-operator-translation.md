---
title: Převod standardních operátorů dotazů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: 4df1653b7bd6865ad9f5d7d3fb9be6815dcfe018
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781012"
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="7a7b7-102">Převod standardních operátorů dotazů</span><span class="sxs-lookup"><span data-stu-id="7a7b7-102">Standard Query Operator Translation</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7a7b7-103">přeloží standardní operátory dotazu na příkazy SQL.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-103">translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="7a7b7-104">Procesor dotazů databáze určuje sémantiku provádění překladu SQL.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-104">The query processor of the database determines the execution semantics of SQL translation.</span></span>

<span data-ttu-id="7a7b7-105">Standardní operátory dotazu jsou definovány pro *sekvence*.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-105">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="7a7b7-106">Sekvence je *seřazena* a spoléhá na referenční identitu pro každý prvek sekvence.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-106">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="7a7b7-107">Další informace najdete v tématu Přehled [standardních operátorů dotazůC#()](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) nebo [standardní operátory dotazu (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7a7b7-107">For more information, see [Standard Query Operators Overview (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

<span data-ttu-id="7a7b7-108">SQL slouží hlavně pro *neuspořádané sady hodnot*.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-108">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="7a7b7-109">Řazení je obvykle výslovně uvedeno, operace následného zpracování, která je použita na konečný výsledek dotazu, nikoli na mezilehlé výsledky.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-109">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="7a7b7-110">Identita je definována hodnotami.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-110">Identity is defined by values.</span></span> <span data-ttu-id="7a7b7-111">Z tohoto důvodu jsou dotazy SQL srozumitelné pro práci s více sadami (*penalt*) místo *sad*.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-111">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>

<span data-ttu-id="7a7b7-112">Následující odstavce popisují rozdíly mezi standardními operátory dotazů a jejich překladem SQL pro poskytovatele SQL Server pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a7b7-112">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

## <a name="operator-support"></a><span data-ttu-id="7a7b7-113">Podpora operátorů</span><span class="sxs-lookup"><span data-stu-id="7a7b7-113">Operator Support</span></span>

### <a name="concat"></a><span data-ttu-id="7a7b7-114">Spojuje</span><span class="sxs-lookup"><span data-stu-id="7a7b7-114">Concat</span></span>

<span data-ttu-id="7a7b7-115"><xref:System.Linq.Enumerable.Concat%2A> Metoda je definována pro seřazené množiny, kde pořadí přijímače a pořadí argumentu jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-115">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="7a7b7-116"><xref:System.Linq.Enumerable.Concat%2A>funguje stejně `UNION ALL` jako více sad následovaných běžným pořadím.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-116"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>

<span data-ttu-id="7a7b7-117">Poslední krok je seřazen v SQL před vytvořením výsledků.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-117">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="7a7b7-118"><xref:System.Linq.Enumerable.Concat%2A>nezachovává pořadí argumentů.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-118"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="7a7b7-119">Aby bylo zajištěno vhodné řazení, je nutné explicitně seřadit výsledky <xref:System.Linq.Enumerable.Concat%2A>.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-119">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>

### <a name="intersect-except-union"></a><span data-ttu-id="7a7b7-120">Průsečík, s výjimkou sjednocení</span><span class="sxs-lookup"><span data-stu-id="7a7b7-120">Intersect, Except, Union</span></span>

<span data-ttu-id="7a7b7-121">Metody <xref:System.Linq.Enumerable.Intersect%2A> a<xref:System.Linq.Enumerable.Except%2A> jsou dobře definovány pouze pro sady.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-121">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="7a7b7-122">Sémantika pro více sad není definována.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-122">The semantics for multisets is undefined.</span></span>

<span data-ttu-id="7a7b7-123"><xref:System.Linq.Enumerable.Union%2A> Metoda je definována pro množiny jako neuspořádané zřetězení množin (efektivně výsledek klauzule UNION ALL v SQL).</span><span class="sxs-lookup"><span data-stu-id="7a7b7-123">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>

### <a name="take-skip"></a><span data-ttu-id="7a7b7-124">Vzít, přeskočit</span><span class="sxs-lookup"><span data-stu-id="7a7b7-124">Take, Skip</span></span>

<span data-ttu-id="7a7b7-125"><xref:System.Linq.Enumerable.Take%2A>metody <xref:System.Linq.Enumerable.Skip%2A> a jsou dobře definovány pouze proti *seřazeným sadám*.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-125"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="7a7b7-126">Sémantika pro neuspořádané sady nebo více sad není definována.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-126">The semantics for unordered sets or multisets are undefined.</span></span>

> [!NOTE]
> <span data-ttu-id="7a7b7-127"><xref:System.Linq.Enumerable.Take%2A>a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, pokud se používají v dotazech proti SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-127"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="7a7b7-128">Další informace najdete v části "přeskočení a přijetí výjimek v SQL Server 2000" v tématu [řešení potíží](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="7a7b7-128">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

<span data-ttu-id="7a7b7-129">Z důvodu omezení pro řazení v SQL se [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokusí přesunout řazení argumentu těchto metod do výsledku metody.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-129">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="7a7b7-130">Zvažte například následující [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotaz:</span><span class="sxs-lookup"><span data-stu-id="7a7b7-130">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

<span data-ttu-id="7a7b7-131">Vygenerovaný SQL pro tento kód přesune řazení na konec následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7a7b7-131">The generated SQL for this code moves the ordering to the end, as follows:</span></span>

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

<span data-ttu-id="7a7b7-132">Je zřejmé, že všechna zadaná řazení musí být konzistentní, když <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> zřetězené dohromady.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-132">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="7a7b7-133">V opačném případě nejsou výsledky definovány.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-133">Otherwise, the results are undefined.</span></span>

<span data-ttu-id="7a7b7-134"><xref:System.Linq.Enumerable.Take%2A> A<xref:System.Linq.Enumerable.Skip%2A> jsou dobře definovány pro nezáporné, konstantní celočíselné argumenty založené na standardní specifikaci operátoru dotazu.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-134">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>

### <a name="operators-with-no-translation"></a><span data-ttu-id="7a7b7-135">Operátory bez překladu</span><span class="sxs-lookup"><span data-stu-id="7a7b7-135">Operators with No Translation</span></span>

<span data-ttu-id="7a7b7-136">Následující metody nejsou přeloženy pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a7b7-136">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="7a7b7-137">Nejběžnějším důvodem je rozdíl mezi neseřazenými množinami a sekvencemi.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-137">The most common reason is the difference between unordered multisets and sequences.</span></span>

|<span data-ttu-id="7a7b7-138">Operátory</span><span class="sxs-lookup"><span data-stu-id="7a7b7-138">Operators</span></span>|<span data-ttu-id="7a7b7-139">Dobře chápete důvody</span><span class="sxs-lookup"><span data-stu-id="7a7b7-139">Rationale</span></span>|
|---------------|---------------|
|<span data-ttu-id="7a7b7-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="7a7b7-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="7a7b7-141">Dotazy SQL pracují s více sadami, nikoli v sekvencích.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-141">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="7a7b7-142">`ORDER BY`musí se jednat o poslední klauzuli použitou pro výsledky.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-142">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="7a7b7-143">Z tohoto důvodu neexistuje žádný překlad pro obecné účely těchto dvou metod.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-143">For this reason, there is no general-purpose translation for these two methods.</span></span>|
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="7a7b7-144">Překlad této metody je možný pro seřazenou sadu, ale není aktuálně přeložen pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a7b7-144">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="7a7b7-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="7a7b7-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="7a7b7-146">Překlad těchto metod je možný pro seřazenou sadu, ale není aktuálně přeložen pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a7b7-146">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="7a7b7-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="7a7b7-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="7a7b7-148">Dotazy SQL pracují s více sadami, nikoli s indexovanými sekvencemi.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-148">SQL queries operate on multisets, not on indexable sequences.</span></span>|
|<span data-ttu-id="7a7b7-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A>(Overload s výchozím ARG)</span><span class="sxs-lookup"><span data-stu-id="7a7b7-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="7a7b7-150">Obecně platí, že u libovolné řazené kolekce členů nejde zadat výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-150">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="7a7b7-151">Hodnoty null pro řazené kolekce členů jsou možné v některých případech prostřednictvím vnějších spojení.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-151">Null values for tuples are possible in some cases through outer joins.</span></span>|

## <a name="expression-translation"></a><span data-ttu-id="7a7b7-152">Překlad výrazu</span><span class="sxs-lookup"><span data-stu-id="7a7b7-152">Expression Translation</span></span>

### <a name="null-semantics"></a><span data-ttu-id="7a7b7-153">Sémantika null</span><span class="sxs-lookup"><span data-stu-id="7a7b7-153">Null semantics</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7a7b7-154">neukládá sémantiku porovnání s hodnotou null na SQL.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-154">does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="7a7b7-155">Operátory porovnání jsou syntakticky přeloženy na jejich ekvivalenty SQL.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-155">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="7a7b7-156">Z tohoto důvodu sémantika odráží sémantiku SQL, která je definovaná nastavením serveru nebo připojení.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-156">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="7a7b7-157">Například dvě hodnoty null se považují za neshodné s výchozím SQL Server nastavením, ale můžete změnit nastavení pro změnu sémantiky.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-157">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7a7b7-158">nebere v úvahu nastavení serveru při překládání dotazů.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-158">does not consider server settings when it translates queries.</span></span>

<span data-ttu-id="7a7b7-159">Porovnání s literálem null je přeloženo na odpovídající verzi SQL (`is null` nebo `is not null`).</span><span class="sxs-lookup"><span data-stu-id="7a7b7-159">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="7a7b7-160">Hodnota `null` v kolaci je definována SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-160">The value of `null` in collation is defined by SQL Server.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7a7b7-161">nemění kolaci.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-161">does not change the collation.</span></span>

### <a name="aggregates"></a><span data-ttu-id="7a7b7-162">Agregace</span><span class="sxs-lookup"><span data-stu-id="7a7b7-162">Aggregates</span></span>

<span data-ttu-id="7a7b7-163">Agregační metoda <xref:System.Linq.Enumerable.Sum%2A> standardního operátoru dotazu vyhodnocuje nulu pro prázdnou sekvenci nebo pro sekvenci, která obsahuje pouze hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-163">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="7a7b7-164">V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]systému jsou sémantika jazyka SQL ponechána beze změny a <xref:System.Linq.Enumerable.Sum%2A> vyhodnocena `null` jako místo nuly pro prázdnou sekvenci nebo pro sekvenci, která obsahuje pouze hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-164">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>

<span data-ttu-id="7a7b7-165">Omezení SQL pro mezilehlé výsledky se vztahují na agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a7b7-165">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="7a7b7-166">Počet <xref:System.Linq.Enumerable.Sum%2A> celočíselných hodnot v čísle 32 není počítán pomocí 64 bitových výsledků.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-166">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="7a7b7-167">Přetečení může nastat pro [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Enumerable.Sum%2A>překlad, i když standardní implementace operátoru dotazu nezpůsobí přetečení odpovídající posloupnosti v paměti.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-167">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>

<span data-ttu-id="7a7b7-168">`integer` `double`Podobně je [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Enumerable.Average%2A> převod celočíselných hodnot vypočítán jako, nikoli jako.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-168">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>

### <a name="entity-arguments"></a><span data-ttu-id="7a7b7-169">Argumenty entity</span><span class="sxs-lookup"><span data-stu-id="7a7b7-169">Entity Arguments</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7a7b7-170">umožňuje použít typy entit v <xref:System.Linq.Enumerable.GroupBy%2A> metodách a. <xref:System.Linq.Enumerable.OrderBy%2A></span><span class="sxs-lookup"><span data-stu-id="7a7b7-170">enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="7a7b7-171">V překladu těchto operátorů je použití argumentu typu považováno za ekvivalent pro určení všech členů tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-171">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="7a7b7-172">Například následující kód je ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="7a7b7-172">For example, the following code is equivalent:</span></span>

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a><span data-ttu-id="7a7b7-173">Nejrovnější/porovnatelné argumenty</span><span class="sxs-lookup"><span data-stu-id="7a7b7-173">Equatable / Comparable Arguments</span></span>

<span data-ttu-id="7a7b7-174">V implementaci následujících metod je vyžadována rovnost argumentů:</span><span class="sxs-lookup"><span data-stu-id="7a7b7-174">Equality of arguments is required in the implementation of the following methods:</span></span>

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7a7b7-175">podporuje rovnost a porovnávání pro *rovné* argumenty, ale ne pro argumenty, které jsou nebo obsahují sekvence.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-175">supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="7a7b7-176">Plochý argument je typ, který lze namapovat na řádek SQL.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-176">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="7a7b7-177">Projekce jednoho nebo více typů entit, které lze staticky určit, aby neobsahovala sekvenci, je považována za plochý argument.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-177">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>

<span data-ttu-id="7a7b7-178">Následují příklady plochých argumentů:</span><span class="sxs-lookup"><span data-stu-id="7a7b7-178">Following are examples of flat arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

<span data-ttu-id="7a7b7-179">Následují příklady neplochých (hierarchických) argumentů.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-179">The following are examples of non-flat (hierarchical) arguments.</span></span>

[!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a><span data-ttu-id="7a7b7-180">Visual Basic překlad funkce</span><span class="sxs-lookup"><span data-stu-id="7a7b7-180">Visual Basic Function Translation</span></span>

<span data-ttu-id="7a7b7-181">Následující pomocné funkce, které jsou používány kompilátorem Visual Basic, jsou přeloženy do odpovídajících funkcí a operátorů SQL:</span><span class="sxs-lookup"><span data-stu-id="7a7b7-181">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

<span data-ttu-id="7a7b7-182">Metody převodu:</span><span class="sxs-lookup"><span data-stu-id="7a7b7-182">Conversion methods:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="7a7b7-183">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="7a7b7-183">ToBoolean</span></span>|<span data-ttu-id="7a7b7-184">ToSByte –</span><span class="sxs-lookup"><span data-stu-id="7a7b7-184">ToSByte</span></span>|<span data-ttu-id="7a7b7-185">ToByte –</span><span class="sxs-lookup"><span data-stu-id="7a7b7-185">ToByte</span></span>|<span data-ttu-id="7a7b7-186">ToChar –</span><span class="sxs-lookup"><span data-stu-id="7a7b7-186">ToChar</span></span>|
|<span data-ttu-id="7a7b7-187">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="7a7b7-187">ToCharArrayRankOne</span></span>|<span data-ttu-id="7a7b7-188">V tomto</span><span class="sxs-lookup"><span data-stu-id="7a7b7-188">ToDate</span></span>|<span data-ttu-id="7a7b7-189">ToDecimal –</span><span class="sxs-lookup"><span data-stu-id="7a7b7-189">ToDecimal</span></span>|<span data-ttu-id="7a7b7-190">ToDouble –</span><span class="sxs-lookup"><span data-stu-id="7a7b7-190">ToDouble</span></span>|
|<span data-ttu-id="7a7b7-191">ToInteger</span><span class="sxs-lookup"><span data-stu-id="7a7b7-191">ToInteger</span></span>|<span data-ttu-id="7a7b7-192">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="7a7b7-192">ToUInteger</span></span>|<span data-ttu-id="7a7b7-193">ToLong</span><span class="sxs-lookup"><span data-stu-id="7a7b7-193">ToLong</span></span>|<span data-ttu-id="7a7b7-194">ToULong</span><span class="sxs-lookup"><span data-stu-id="7a7b7-194">ToULong</span></span>|
|<span data-ttu-id="7a7b7-195">ToShort</span><span class="sxs-lookup"><span data-stu-id="7a7b7-195">ToShort</span></span>|<span data-ttu-id="7a7b7-196">ToUShort</span><span class="sxs-lookup"><span data-stu-id="7a7b7-196">ToUShort</span></span>|<span data-ttu-id="7a7b7-197">ToSingle –</span><span class="sxs-lookup"><span data-stu-id="7a7b7-197">ToSingle</span></span>|<span data-ttu-id="7a7b7-198">Metodu</span><span class="sxs-lookup"><span data-stu-id="7a7b7-198">ToString</span></span>|

## <a name="inheritance-support"></a><span data-ttu-id="7a7b7-199">Podpora dědičnosti</span><span class="sxs-lookup"><span data-stu-id="7a7b7-199">Inheritance Support</span></span>

### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="7a7b7-200">Omezení mapování dědičnosti</span><span class="sxs-lookup"><span data-stu-id="7a7b7-200">Inheritance Mapping Restrictions</span></span>

<span data-ttu-id="7a7b7-201">Další informace najdete v tématu [jak: Mapování hierarchií](how-to-map-inheritance-hierarchies.md)dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-201">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>

### <a name="inheritance-in-queries"></a><span data-ttu-id="7a7b7-202">Dědičnost v dotazech</span><span class="sxs-lookup"><span data-stu-id="7a7b7-202">Inheritance in Queries</span></span>

<span data-ttu-id="7a7b7-203">C#přetypování jsou podporovaná jenom v projekci.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-203">C# casts are supported only in projection.</span></span> <span data-ttu-id="7a7b7-204">Přetypování, která jsou používána jinde, nejsou přeložena a jsou ignorována.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-204">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="7a7b7-205">Z nezávisle na názvech funkcí SQL provádí SQL skutečně pouze ekvivalent modulu CLR (Common Language Runtime <xref:System.Convert>).</span><span class="sxs-lookup"><span data-stu-id="7a7b7-205">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="7a7b7-206">To znamená, že SQL může změnit hodnotu jednoho typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-206">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="7a7b7-207">Neexistuje žádný ekvivalent přetypování CLR, protože neexistuje koncept přeinterpretace stejných bitů jako u jiného typu.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-207">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="7a7b7-208">To je důvod, C# proč přetypování funguje pouze místně.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-208">That is why a C# cast works only locally.</span></span> <span data-ttu-id="7a7b7-209">Nejedná se o vzdálenou.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-209">It is not remoted.</span></span>

<span data-ttu-id="7a7b7-210">Operátory, `is` `Select` a `as` a`GetType` metody nejsou omezeny na operátor.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-210">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="7a7b7-211">Je možné je použít také v jiných operátorech dotazu.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-211">They can be used in other query operators also.</span></span>

## <a name="sql-server-2008-support"></a><span data-ttu-id="7a7b7-212">SQL Server 2008 Support</span><span class="sxs-lookup"><span data-stu-id="7a7b7-212">SQL Server 2008 Support</span></span>

<span data-ttu-id="7a7b7-213">Počínaje verzí .NET Framework 3,5 SP1 LINQ to SQL podporuje mapování na nové typy data a času zavedené pomocí SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-213">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="7a7b7-214">Existují však určitá omezení pro operátory LINQ to SQL dotazů, které lze použít při práci s hodnotami mapovanými na tyto nové typy.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-214">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>

### <a name="unsupported-query-operators"></a><span data-ttu-id="7a7b7-215">Nepodporované operátory dotazů</span><span class="sxs-lookup"><span data-stu-id="7a7b7-215">Unsupported Query Operators</span></span>

<span data-ttu-id="7a7b7-216">Následující operátory dotazu nejsou podporovány v hodnotách mapovaných na `DATETIME2`nové SQL Server typy data a času:, `DATE`, `TIME` `DATETIMEOFFSET`a.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-216">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

<span data-ttu-id="7a7b7-217">Další informace o mapování na tyto SQL Server typy data a času naleznete v tématu [mapování typu SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="7a7b7-217">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

## <a name="sql-server-2005-support"></a><span data-ttu-id="7a7b7-218">SQL Server 2005 Support</span><span class="sxs-lookup"><span data-stu-id="7a7b7-218">SQL Server 2005 Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7a7b7-219">nepodporuje následující funkce SQL Server 2005:</span><span class="sxs-lookup"><span data-stu-id="7a7b7-219">does not support the following SQL Server 2005 features:</span></span>

- <span data-ttu-id="7a7b7-220">Uložené procedury napsané pro SQL CLR.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-220">Stored procedures written for SQL CLR.</span></span>

- <span data-ttu-id="7a7b7-221">Uživatelem definovaný typ.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-221">User-defined type.</span></span>

- <span data-ttu-id="7a7b7-222">Funkce dotazů XML.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-222">XML query features.</span></span>

## <a name="sql-server-2000-support"></a><span data-ttu-id="7a7b7-223">SQL Server 2000 Support</span><span class="sxs-lookup"><span data-stu-id="7a7b7-223">SQL Server 2000 Support</span></span>

<span data-ttu-id="7a7b7-224">Následující omezení SQL Server 2000 (v porovnání s Microsoft SQL Server 2005) mají [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vliv na podporu.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-224">The following SQL Server 2000 limitations (compared to Microsoft SQL Server 2005) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>

### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="7a7b7-225">Operátory vzájemného použití a vnějšího použití</span><span class="sxs-lookup"><span data-stu-id="7a7b7-225">Cross Apply and Outer Apply Operators</span></span>

<span data-ttu-id="7a7b7-226">Tyto operátory nejsou k dispozici v SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-226">These operators are not available in SQL Server 2000.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7a7b7-227">pokusí se o řadu přepsání, která je nahradí příslušnými spojeními.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-227">tries a series of rewrites to replace them with appropriate joins.</span></span>

<span data-ttu-id="7a7b7-228">`Cross Apply`a `Outer Apply` jsou generovány pro navigaci relací.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-228">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="7a7b7-229">Sada dotazů, pro které jsou takové přepisy možné, není dobře definována.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-229">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="7a7b7-230">Z tohoto důvodu je minimální sada dotazů, které jsou podporovány pro SQL Server 2000, sadou, která nezahrnuje navigaci relací.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-230">For this reason, the minimal set of queries that is supported for SQL Server 2000 is the set that does not involve relationship navigation.</span></span>

### <a name="text--ntext"></a><span data-ttu-id="7a7b7-231">text/ntext</span><span class="sxs-lookup"><span data-stu-id="7a7b7-231">text / ntext</span></span>

<span data-ttu-id="7a7b7-232">Datové typy `text`  /  `varchar(max)`  / nelze použít v určitých operacích dotazu proti`nvarchar(max)`, které jsou podporovány Microsoft SQL Server 2005. `ntext`</span><span class="sxs-lookup"><span data-stu-id="7a7b7-232">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by Microsoft SQL Server 2005.</span></span>

<span data-ttu-id="7a7b7-233">Pro toto omezení není k dispozici žádné řešení.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-233">No resolution is available for this limitation.</span></span> <span data-ttu-id="7a7b7-234">Konkrétně nemůžete použít `Distinct()` na žádný výsledek, který obsahuje členy mapované na `text` nebo `ntext` sloupce.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-234">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>

### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="7a7b7-235">Chování aktivované vnořenými dotazy</span><span class="sxs-lookup"><span data-stu-id="7a7b7-235">Behavior Triggered by Nested Queries</span></span>

<span data-ttu-id="7a7b7-236">Pořadač SQL Server 2000 (přes SP4) obsahuje některé idiosyncrasies, které se spouštějí ve vnořených dotazech.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-236">SQL Server 2000 (through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="7a7b7-237">Sada dotazů SQL, které aktivují tyto idiosyncrasies, není správně definovaná.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-237">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="7a7b7-238">Z tohoto důvodu nemůžete definovat sadu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazů, které by mohly způsobit SQL Server výjimky.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-238">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>

### <a name="skip-and-take-operators"></a><span data-ttu-id="7a7b7-239">Přeskočit a převzít operátory</span><span class="sxs-lookup"><span data-stu-id="7a7b7-239">Skip and Take Operators</span></span>

<span data-ttu-id="7a7b7-240"><xref:System.Linq.Enumerable.Take%2A>a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, pokud se používají v dotazech proti SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-240"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="7a7b7-241">Další informace najdete v části "přeskočení a přijetí výjimek v SQL Server 2000" v tématu [řešení potíží](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="7a7b7-241">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="object-materialization"></a><span data-ttu-id="7a7b7-242">Materializace objektů</span><span class="sxs-lookup"><span data-stu-id="7a7b7-242">Object Materialization</span></span>

<span data-ttu-id="7a7b7-243">Materializace vytvoří objekty CLR z řádků, které jsou vráceny jedním nebo více dotazy jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-243">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>

- <span data-ttu-id="7a7b7-244">Následující volání se *spouštějí místně* jako součást materializace:</span><span class="sxs-lookup"><span data-stu-id="7a7b7-244">The following calls are *executed locally* as a part of materialization:</span></span>

  - <span data-ttu-id="7a7b7-245">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="7a7b7-245">Constructors</span></span>

  - <span data-ttu-id="7a7b7-246">`ToString`metody v projekce</span><span class="sxs-lookup"><span data-stu-id="7a7b7-246">`ToString` methods in projections</span></span>

  - <span data-ttu-id="7a7b7-247">Typy přetypování v projekce</span><span class="sxs-lookup"><span data-stu-id="7a7b7-247">Type casts in projections</span></span>

- <span data-ttu-id="7a7b7-248">Metody, které následují <xref:System.Linq.Enumerable.AsEnumerable%2A> metodu jsou *spouštěny místně*.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-248">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="7a7b7-249">Tato metoda nezpůsobí okamžité provedení.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-249">This method does not cause immediate execution.</span></span>

- <span data-ttu-id="7a7b7-250">Můžete použít `struct` jako návratový typ výsledku dotazu nebo jako člen typu výsledku.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-250">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="7a7b7-251">Entity jsou nutné pro třídy.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-251">Entities are required to be classes.</span></span> <span data-ttu-id="7a7b7-252">Anonymní typy jsou materializované jako instance třídy, ale pojmenované struktury (jiné než entity) se dají použít v projekci.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-252">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>

- <span data-ttu-id="7a7b7-253">Člen návratového typu výsledku dotazu může být typu <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-253">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="7a7b7-254">Je vyhodnocena jako místní kolekce.</span><span class="sxs-lookup"><span data-stu-id="7a7b7-254">It is materialized as a local collection.</span></span>

- <span data-ttu-id="7a7b7-255">Následující metody způsobují *okamžitou materializaci* sekvence, na kterou jsou metody aplikovány:</span><span class="sxs-lookup"><span data-stu-id="7a7b7-255">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a><span data-ttu-id="7a7b7-256">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a7b7-256">See also</span></span>

- [<span data-ttu-id="7a7b7-257">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="7a7b7-257">Reference</span></span>](reference.md)
- [<span data-ttu-id="7a7b7-258">Vrácení nebo přeskočení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="7a7b7-258">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)
- [<span data-ttu-id="7a7b7-259">Zřetězení dvou sekvencí</span><span class="sxs-lookup"><span data-stu-id="7a7b7-259">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)
- [<span data-ttu-id="7a7b7-260">Vrácení rozdílů množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="7a7b7-260">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)
- [<span data-ttu-id="7a7b7-261">Vrácení průniku množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="7a7b7-261">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)
- [<span data-ttu-id="7a7b7-262">Vrácení sjednocení množin mezi dvěma sekvencemi</span><span class="sxs-lookup"><span data-stu-id="7a7b7-262">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)
