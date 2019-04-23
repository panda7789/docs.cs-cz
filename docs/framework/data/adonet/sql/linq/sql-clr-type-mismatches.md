---
title: Neshody typů SQL a CLR
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 13d8d68140b68652b5e059ae9fb106f32142f698
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974854"
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="0aacd-102">Neshody typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="0aacd-102">SQL-CLR Type Mismatches</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0aacd-103">automatizuje většinu překlad mezi objektový model a systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0aacd-103">automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="0aacd-104">Nicméně některé situace zabránit přesné překladu.</span><span class="sxs-lookup"><span data-stu-id="0aacd-104">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="0aacd-105">Tyto klíče neshody mezi běžné typy language runtime (CLR) a typy databáze systému SQL Server jsou shrnuté v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="0aacd-105">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="0aacd-106">Můžete najít další podrobnosti o mapování určitého typu a funkce překladu na [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) a [datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span><span class="sxs-lookup"><span data-stu-id="0aacd-106">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) and [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span></span>

## <a name="data-types"></a><span data-ttu-id="0aacd-107">Datové typy</span><span class="sxs-lookup"><span data-stu-id="0aacd-107">Data Types</span></span>

<span data-ttu-id="0aacd-108">Při odesílání dotazu do databáze a kdy se výsledky odesílají zpět k objektovému modelu dochází k převodu mezi CLR a systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0aacd-108">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="0aacd-109">Například následující dotaz jazyka Transact-SQL vyžaduje dva převody hodnot:</span><span class="sxs-lookup"><span data-stu-id="0aacd-109">For example, the following Transact-SQL query requires two value conversions:</span></span>

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

<span data-ttu-id="0aacd-110">Předtím, než je možné provést dotaz v systému SQL Server, musíte zadat hodnotu pro parametr příkazů jazyka Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="0aacd-110">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="0aacd-111">V tomto příkladu `id` hodnota parametru musí být nejdříve přeložena z modul CLR. <xref:System.Int32?displayProperty=nameWithType> typu k serveru SQL Server `INT` tak, aby databáze můžete pochopit, co je hodnota.</span><span class="sxs-lookup"><span data-stu-id="0aacd-111">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="0aacd-112">Potom k načtení výsledků, SQL Server `DateOfBirth` sloupec musí být převedeny z SQL serveru `DATETIME` typ, který má modul CLR <xref:System.DateTime?displayProperty=nameWithType> typ pro použití v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="0aacd-112">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="0aacd-113">V tomto příkladu typy CLR objektový model a databáze systému SQL Server mají přirozené mapování.</span><span class="sxs-lookup"><span data-stu-id="0aacd-113">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="0aacd-114">Ale není to vždy.</span><span class="sxs-lookup"><span data-stu-id="0aacd-114">But, this is not always the case.</span></span>

### <a name="missing-counterparts"></a><span data-ttu-id="0aacd-115">Chybějící protějšky</span><span class="sxs-lookup"><span data-stu-id="0aacd-115">Missing Counterparts</span></span>

<span data-ttu-id="0aacd-116">Následující typy nemají přiměřené protějšky.</span><span class="sxs-lookup"><span data-stu-id="0aacd-116">The following types do not have reasonable counterparts.</span></span>

- <span data-ttu-id="0aacd-117">V modulu CLR se neshoduje s <xref:System> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="0aacd-117">Mismatches in the CLR <xref:System> namespace:</span></span>

  - <span data-ttu-id="0aacd-118">**Čísla typu unsigned integer**.</span><span class="sxs-lookup"><span data-stu-id="0aacd-118">**Unsigned integers**.</span></span> <span data-ttu-id="0aacd-119">Tyto typy se obvykle mapují na své ekvivalenty podepsaný o větší velikosti chcete zabránit přetečení.</span><span class="sxs-lookup"><span data-stu-id="0aacd-119">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="0aacd-120">Literály lze převést na číselnou znaménkem stejné nebo menší velikosti na základě hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0aacd-120">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>

  - <span data-ttu-id="0aacd-121">**Logická**.</span><span class="sxs-lookup"><span data-stu-id="0aacd-121">**Boolean**.</span></span> <span data-ttu-id="0aacd-122">Tyto typy lze mapovat na bit nebo větší numerická nebo řetězec.</span><span class="sxs-lookup"><span data-stu-id="0aacd-122">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="0aacd-123">Literál je možné mapovat na výraz, který se vyhodnotí jako stejná hodnota (například `1=1` v SQL pro `True` ve specifikaci CLS).</span><span class="sxs-lookup"><span data-stu-id="0aacd-123">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>

  - <span data-ttu-id="0aacd-124">**Časový interval**.</span><span class="sxs-lookup"><span data-stu-id="0aacd-124">**TimeSpan**.</span></span> <span data-ttu-id="0aacd-125">Tento typ reprezentuje rozdíl mezi dvěma `DateTime` hodnoty a nemusí odpovídat `timestamp` systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0aacd-125">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="0aacd-126">Modul CLR <xref:System.TimeSpan?displayProperty=nameWithType> může také namapovat na SQL Server `TIME` typ v některých případech.</span><span class="sxs-lookup"><span data-stu-id="0aacd-126">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="0aacd-127">SQL Server `TIME` typu byla určena pouze k reprezentaci kladné hodnoty kratší než 24 hodin.</span><span class="sxs-lookup"><span data-stu-id="0aacd-127">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="0aacd-128">Modul CLR <xref:System.TimeSpan> má mnohem větší rozsah.</span><span class="sxs-lookup"><span data-stu-id="0aacd-128">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>

  > [!NOTE]
  > <span data-ttu-id="0aacd-129">SQL Server – konkrétní [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] napíše <xref:System.Data.SqlTypes> nejsou součástí tohoto porovnání.</span><span class="sxs-lookup"><span data-stu-id="0aacd-129">SQL Server-specific [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>

- <span data-ttu-id="0aacd-130">Neshody v systému SQL Server:</span><span class="sxs-lookup"><span data-stu-id="0aacd-130">Mismatches in SQL Server:</span></span>

  - <span data-ttu-id="0aacd-131">**Typy znaků pevné délky**.</span><span class="sxs-lookup"><span data-stu-id="0aacd-131">**Fixed length character types**.</span></span> <span data-ttu-id="0aacd-132">Příkaz Transact-SQL rozlišuje mezi kategorie sady Unicode a kódování Unicode a má tři různé typy v každé kategorii: pevnou délku `nchar` / `char`, s proměnnou délkou `nvarchar` / `varchar`, a větší velikost `ntext` / `text`.</span><span class="sxs-lookup"><span data-stu-id="0aacd-132">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="0aacd-133">Typy znaků pevné délky mapovat CLR <xref:System.Char?displayProperty=nameWithType> znaky typu pro načtení, ale ve skutečnosti neodpovídají na stejný typ. převody a chování.</span><span class="sxs-lookup"><span data-stu-id="0aacd-133">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>

  - <span data-ttu-id="0aacd-134">**Bit**.</span><span class="sxs-lookup"><span data-stu-id="0aacd-134">**Bit**.</span></span> <span data-ttu-id="0aacd-135">I když `bit` doména má stejný počet hodnot jako `Nullable<Boolean>`, jsou dva různé typy.</span><span class="sxs-lookup"><span data-stu-id="0aacd-135">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="0aacd-136">`Bit` přijímá hodnoty `1` a `0` místo `true` / `false`a nelze jej použít jako rovnocenné logických výrazů.</span><span class="sxs-lookup"><span data-stu-id="0aacd-136">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>

  - <span data-ttu-id="0aacd-137">**Časové razítko**.</span><span class="sxs-lookup"><span data-stu-id="0aacd-137">**Timestamp**.</span></span> <span data-ttu-id="0aacd-138">Na rozdíl od CLR <xref:System.TimeSpan?displayProperty=nameWithType> zadejte SQL Server `TIMESTAMP` typ představuje číslo 8bajtový generován databází, které je jedinečné pro jednotlivé aktualizace a není založena na rozdíl mezi <xref:System.DateTime> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0aacd-138">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>

  - <span data-ttu-id="0aacd-139">**Peníze** a **SmallMoney**.</span><span class="sxs-lookup"><span data-stu-id="0aacd-139">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="0aacd-140">Tyto typy lze mapovat na <xref:System.Decimal> , ale jsou v podstatě různé typy a jako takový nakládá serverových funkcí a převody.</span><span class="sxs-lookup"><span data-stu-id="0aacd-140">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>

### <a name="multiple-mappings"></a><span data-ttu-id="0aacd-141">Mapování více</span><span class="sxs-lookup"><span data-stu-id="0aacd-141">Multiple Mappings</span></span>

<span data-ttu-id="0aacd-142">Existuje mnoho typů dat serveru SQL Server, namapované na jeden nebo více datové typy CLR.</span><span class="sxs-lookup"><span data-stu-id="0aacd-142">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="0aacd-143">Existují také mnoho typů CLR, které můžete namapovat na jeden nebo více typů systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0aacd-143">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="0aacd-144">I když mapování může být podporována technologií LINQ to SQL, neznamená to, že tyto dva typy mapovány mezi CLR a systému SQL Server se skvěle hodí v přesnost, rozsahu a sémantika.</span><span class="sxs-lookup"><span data-stu-id="0aacd-144">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="0aacd-145">Některé mapování může obsahovat rozdíly v některých nebo všech těchto dimenzí.</span><span class="sxs-lookup"><span data-stu-id="0aacd-145">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="0aacd-146">Můžete najít podrobnosti o těchto rozdílech potenciální pro různé možnosti mapování na [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="0aacd-146">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>

### <a name="user-defined-types"></a><span data-ttu-id="0aacd-147">Uživatelem definované typy</span><span class="sxs-lookup"><span data-stu-id="0aacd-147">User-defined Types</span></span>

<span data-ttu-id="0aacd-148">Uživatelem definované typy CLR jsou navržené tak, abychom překleňte propast systému typu.</span><span class="sxs-lookup"><span data-stu-id="0aacd-148">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="0aacd-149">Nicméně poskytování zajímavých problémů o správě verzí typu.</span><span class="sxs-lookup"><span data-stu-id="0aacd-149">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="0aacd-150">Změnou v typ uložený na databázovém serveru nemusí odpovídat změnu ve verzi na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="0aacd-150">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="0aacd-151">Tato změna způsobí, že jiný Neshoda typu, kde nemusí odpovídat Sémantika typu a mezera verze je pravděpodobné, že budou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="0aacd-151">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="0aacd-152">Hierarchie dědičnosti implementovány v následných verzích docházet k další komplikace.</span><span class="sxs-lookup"><span data-stu-id="0aacd-152">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>

## <a name="expression-semantics"></a><span data-ttu-id="0aacd-153">Sémantika výrazů</span><span class="sxs-lookup"><span data-stu-id="0aacd-153">Expression Semantics</span></span>

<span data-ttu-id="0aacd-154">Výrazy kromě pairwise Neshoda mezi typy CLR a databáze přidat složitost neshoda.</span><span class="sxs-lookup"><span data-stu-id="0aacd-154">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="0aacd-155">Musí přestat považovat neshody v operátor sémantiku, sémantiku funkce, implicitní převod typu a pravidel.</span><span class="sxs-lookup"><span data-stu-id="0aacd-155">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>

<span data-ttu-id="0aacd-156">Následující témata ukazují neshody mezi zjevně podobné výrazy.</span><span class="sxs-lookup"><span data-stu-id="0aacd-156">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="0aacd-157">Je možné generovat SQL výrazy, které jsou sémanticky ekvivalentní daného výrazu CLR.</span><span class="sxs-lookup"><span data-stu-id="0aacd-157">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="0aacd-158">Ale není jasné, jestli jsou menší významové rozdíly mezi zjevně podobné výrazy CLR uživateli zřejmé, a proto určuje, zda jsou určeny změny, které jsou požadovány pro sémantické ekvivalence nebo ne.</span><span class="sxs-lookup"><span data-stu-id="0aacd-158">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="0aacd-159">To je zvlášť zásadní potíže při vyhodnocování výrazu pro sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="0aacd-159">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="0aacd-160">Viditelnost rozdíl může záviset na data – a být obtížné určit během psaní kódu a ladění.</span><span class="sxs-lookup"><span data-stu-id="0aacd-160">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>

### <a name="null-semantics"></a><span data-ttu-id="0aacd-161">Sémantika s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="0aacd-161">Null Semantics</span></span>

<span data-ttu-id="0aacd-162">Výrazy SQL poskytují tři vracející logiku pro logické výrazy.</span><span class="sxs-lookup"><span data-stu-id="0aacd-162">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="0aacd-163">Výsledkem může být true, false nebo null.</span><span class="sxs-lookup"><span data-stu-id="0aacd-163">The result can be true, false, or null.</span></span> <span data-ttu-id="0aacd-164">Naopak CLR určuje dvěma hodnotami výsledek logickou hodnotu pro porovnání s hodnotami null.</span><span class="sxs-lookup"><span data-stu-id="0aacd-164">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="0aacd-165">Vezměte v úvahu následující kód:</span><span class="sxs-lookup"><span data-stu-id="0aacd-165">Consider the following code:</span></span>

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

<span data-ttu-id="0aacd-166">Podobný problém se vyskytuje za předpokladu o výsledcích dvěma hodnotami.</span><span class="sxs-lookup"><span data-stu-id="0aacd-166">A similar problem occurs with the assumption about two-valued results.</span></span>

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

<span data-ttu-id="0aacd-167">V předchozím případě získáte ekvivalentního chování při generování SQL, ale překladu nemusí přesně odrážet váš záměr.</span><span class="sxs-lookup"><span data-stu-id="0aacd-167">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0aacd-168">nepředstavuje C# `null` nebo Visual Basic `nothing` porovnání sémantiky pro SQL.</span><span class="sxs-lookup"><span data-stu-id="0aacd-168">does not impose C# `null` or Visual Basic `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="0aacd-169">Operátory porovnání jsou syntakticky převedeny na jejich ekvivalenty SQL.</span><span class="sxs-lookup"><span data-stu-id="0aacd-169">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="0aacd-170">Sémantika odrážet SQL sémantiku dle nastavení serveru nebo připojení.</span><span class="sxs-lookup"><span data-stu-id="0aacd-170">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="0aacd-171">Dvě hodnoty null se považují za nestejné podle výchozího nastavení systému SQL Server (i když můžete změnit nastavení můžete změnit sémantiku).</span><span class="sxs-lookup"><span data-stu-id="0aacd-171">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="0aacd-172">Bez ohledu na to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nebere v úvahu nastavení serveru v překladu dotazu.</span><span class="sxs-lookup"><span data-stu-id="0aacd-172">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>

<span data-ttu-id="0aacd-173">Porovnání s literál `null` (`nothing`) se přeloží na odpovídající verzi SQL (`is null` nebo `is not null`).</span><span class="sxs-lookup"><span data-stu-id="0aacd-173">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="0aacd-174">Hodnota `null` (`nothing`) v kolaci je definován pomocí SQL serveru. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nedojde ke změně kolace.</span><span class="sxs-lookup"><span data-stu-id="0aacd-174">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>

### <a name="type-conversion-and-promotion"></a><span data-ttu-id="0aacd-175">Převod typu a podpora</span><span class="sxs-lookup"><span data-stu-id="0aacd-175">Type Conversion and Promotion</span></span>

<span data-ttu-id="0aacd-176">SQL podporuje širokou škálu implicitních převodů ve výrazech.</span><span class="sxs-lookup"><span data-stu-id="0aacd-176">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="0aacd-177">Podobně jako výrazy v C# by vyžaduje explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="0aacd-177">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="0aacd-178">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0aacd-178">For example:</span></span>

- <span data-ttu-id="0aacd-179">`Nvarchar` a `DateTime` typy lze porovnat v SQL bez žádné explicitní přetypování; C# vyžaduje explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="0aacd-179">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>

- <span data-ttu-id="0aacd-180">`Decimal` je implicitně převeden na `DateTime` v SQL.</span><span class="sxs-lookup"><span data-stu-id="0aacd-180">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="0aacd-181">C#neumožňuje implicitní převod.</span><span class="sxs-lookup"><span data-stu-id="0aacd-181">C# does not allow for an implicit conversion.</span></span>

<span data-ttu-id="0aacd-182">Priorita typ příkazů jazyka Transact-SQL se liší od typu priority v C# protože základní sadu typů se liší.</span><span class="sxs-lookup"><span data-stu-id="0aacd-182">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="0aacd-183">Mezi seznamy prioritu ve skutečnosti není žádný vztah vymazat dílčí/nadmnožinou.</span><span class="sxs-lookup"><span data-stu-id="0aacd-183">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="0aacd-184">Například porovnávání `nvarchar` s `varchar` způsobí, že implicitní převod `varchar` výraz, který se `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="0aacd-184">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="0aacd-185">CLR poskytuje žádná ekvivalentní povýšení.</span><span class="sxs-lookup"><span data-stu-id="0aacd-185">The CLR provides no equivalent promotion.</span></span>

<span data-ttu-id="0aacd-186">Tyto rozdíly v jednoduché případech způsobit výrazy CLR pomocí přetypování redundantní pro odpovídající výraz SQL.</span><span class="sxs-lookup"><span data-stu-id="0aacd-186">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="0aacd-187">Důležitější je, mezivýsledků SQL výraz může být implicitně povýšen na typ, který nemá přesné protějšek v C#a naopak.</span><span class="sxs-lookup"><span data-stu-id="0aacd-187">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="0aacd-188">Celkově testování, ladění a ověřování těchto výrazů přidá významné zatížení na uživatele.</span><span class="sxs-lookup"><span data-stu-id="0aacd-188">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>

### <a name="collation"></a><span data-ttu-id="0aacd-189">Kolace</span><span class="sxs-lookup"><span data-stu-id="0aacd-189">Collation</span></span>

<span data-ttu-id="0aacd-190">Příkaz Transact-SQL podporuje explicitní řazení jako poznámky a typy řetězce znaků.</span><span class="sxs-lookup"><span data-stu-id="0aacd-190">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="0aacd-191">Tyto kolace určení platnosti určité porovnání.</span><span class="sxs-lookup"><span data-stu-id="0aacd-191">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="0aacd-192">Například dva sloupce s jinou kolací explicitní porovnávání se o chybu.</span><span class="sxs-lookup"><span data-stu-id="0aacd-192">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="0aacd-193">Použití typu řetězec mnohem jednodušší CTS nezpůsobí tyto chyby.</span><span class="sxs-lookup"><span data-stu-id="0aacd-193">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="0aacd-194">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0aacd-194">Consider the following example:</span></span>

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

<span data-ttu-id="0aacd-195">V důsledku toho se vytvoří klauzule kolace *s omezením pomocí specifikátoru typu* , který není zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="0aacd-195">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>

<span data-ttu-id="0aacd-196">Pořadí řazení podobně, může být výrazně liší mezi systémy typu.</span><span class="sxs-lookup"><span data-stu-id="0aacd-196">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="0aacd-197">Tento rozdíl se týká řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="0aacd-197">This difference affects the sorting of results.</span></span> <span data-ttu-id="0aacd-198"><xref:System.Guid> je ve slovníkovém pořadí seřazená podle všech 16 bajtů (`IComparable()`), zatímco T-SQL porovnává GUID v následujícím pořadí: node(10-15) clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span><span class="sxs-lookup"><span data-stu-id="0aacd-198"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="0aacd-199">Toto uspořádání bylo provedeno SQL 7.0, kdy tyto objednávky octet NT generované identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="0aacd-199">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="0aacd-200">Tento přístup, že jsou splněné, GUID, které jsou generované na stejném uzlu clusteru pochází společně v postupném pořadí podle časového razítka.</span><span class="sxs-lookup"><span data-stu-id="0aacd-200">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="0aacd-201">Přístup byl také užitečné pro vytváření indexů (vložení stát připojí namísto náhodného IOs).</span><span class="sxs-lookup"><span data-stu-id="0aacd-201">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="0aacd-202">Pořadí se kódována později ve Windows z důvodu aspekty ochrany osobních údajů, ale SQL musí zachovat kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="0aacd-202">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="0aacd-203">Alternativní řešení, je použít <xref:System.Data.SqlTypes.SqlGuid> místo <xref:System.Guid>.</span><span class="sxs-lookup"><span data-stu-id="0aacd-203">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>

### <a name="operator-and-function-differences"></a><span data-ttu-id="0aacd-204">Operátor a rozdíly ve funkcích</span><span class="sxs-lookup"><span data-stu-id="0aacd-204">Operator and Function Differences</span></span>

<span data-ttu-id="0aacd-205">Operátory a funkce, které jsou v podstatě srovnatelné mají mírně odlišnou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="0aacd-205">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="0aacd-206">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0aacd-206">For example:</span></span>

- <span data-ttu-id="0aacd-207">C#Určuje sémantiku zkráceného vyhodnocení na základě lexikální pořadí operandy pro logické operátory `&&` a `||`.</span><span class="sxs-lookup"><span data-stu-id="0aacd-207">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="0aacd-208">SQL na druhé straně je určena pro dotazy založené na sadě a proto poskytuje více volnosti pro Optimalizátor rozhodnout pořadí provádění.</span><span class="sxs-lookup"><span data-stu-id="0aacd-208">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="0aacd-209">Důsledky patří následující:</span><span class="sxs-lookup"><span data-stu-id="0aacd-209">Some of the implications include the following:</span></span>

  - <span data-ttu-id="0aacd-210">Sémanticky ekvivalentní překlad by vyžadovaly "`CASE` ...</span><span class="sxs-lookup"><span data-stu-id="0aacd-210">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="0aacd-211">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="0aacd-211">`WHEN` …</span></span> <span data-ttu-id="0aacd-212">`THEN`"vytvořit v SQL, aby se zabránilo změny pořadí spouštění operand.</span><span class="sxs-lookup"><span data-stu-id="0aacd-212">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>

  - <span data-ttu-id="0aacd-213">Volný převod do kódu `AND` / `OR` operátory může způsobit neočekávané chyby, pokud C# výraz spoléhá na vyhodnocení druhého operandu je založeno na výsledku vyhodnocení prvním operandem.</span><span class="sxs-lookup"><span data-stu-id="0aacd-213">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>

- <span data-ttu-id="0aacd-214">`Round()` funkce má odlišnou sémantiku [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] a v T-SQL.</span><span class="sxs-lookup"><span data-stu-id="0aacd-214">`Round()` function has different semantics in [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] and in T-SQL.</span></span>

- <span data-ttu-id="0aacd-215">Počáteční index pro řetězce je 0 v modulu CLR, ale 1 v SQL.</span><span class="sxs-lookup"><span data-stu-id="0aacd-215">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="0aacd-216">Proto všechny funkce, které má index musí index překladu.</span><span class="sxs-lookup"><span data-stu-id="0aacd-216">Therefore, any function that has index needs index translation.</span></span>

- <span data-ttu-id="0aacd-217">Modul CLR podporuje operátor numerického zbytku (%) pro čísla s plovoucí desetinnou ale SQL to neuvádí.</span><span class="sxs-lookup"><span data-stu-id="0aacd-217">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>

- <span data-ttu-id="0aacd-218">`Like` Operátor efektivně získá automatické přetížení založené na implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="0aacd-218">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="0aacd-219">I když `Like` je operátor definován provozovat na znakové řetězce typy implicitní převod z číselných typů nebo `DateTime` umožňuje tyto typy jiné než řetězec, který se má použít s typy `Like` stejně.</span><span class="sxs-lookup"><span data-stu-id="0aacd-219">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="0aacd-220">V CTS neexistují porovnatelné implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="0aacd-220">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="0aacd-221">Proto je potřeba další přetížení.</span><span class="sxs-lookup"><span data-stu-id="0aacd-221">Therefore, additional overloads are needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0aacd-222">To `Like` operátor chování platí pro C# pouze; Visual Basic `Like` – klíčové slovo je beze změny.</span><span class="sxs-lookup"><span data-stu-id="0aacd-222">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>

- <span data-ttu-id="0aacd-223">Přetečení vždy změnami SQL ale musí být explicitně zadán v C# (nejsou v jazyce Visual Basic), aby vrácení.</span><span class="sxs-lookup"><span data-stu-id="0aacd-223">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in Visual Basic) to avoid wraparound.</span></span> <span data-ttu-id="0aacd-224">Zadaný sloupcích s celými čísly C1, C2 a C3, pokud je C1 + C2 je uložen v C3 (C3 nastavte aktualizace T = C1 + C2).</span><span class="sxs-lookup"><span data-stu-id="0aacd-224">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>

    ```sql
    create table T3 (
        Col1      integer,
        Col2      integer
    )
    insert into T3 (col1, col2) values (2147483647, 5)
    -- Valid values: max integer value and 5.
    select * from T3 where col1 + col2 < 0
    -- Produces arithmetic overflow error.
    ```

[!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
[!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]

- <span data-ttu-id="0aacd-225">SQL provede symetrický aritmetické operace při zaokrouhlení [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] společnosti používá bankovní zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="0aacd-225">SQL performs symmetric arithmetic rounding while [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] uses banker’s rounding.</span></span> <span data-ttu-id="0aacd-226">Najdete v článku znalostní báze 196652 další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="0aacd-226">See Knowledgebase article 196652 for additional details.</span></span>

- <span data-ttu-id="0aacd-227">Ve výchozím nastavení pro běžné národní prostředí jsou porovnávání řetězců znaků velkých a malých písmen v SQL.</span><span class="sxs-lookup"><span data-stu-id="0aacd-227">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="0aacd-228">V jazyce Visual Basic a v C#, jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="0aacd-228">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="0aacd-229">Například `s == "Food"` (`s = "Food"` v jazyce Visual Basic) a `s == "Food"` mohou přinést různé výsledky, pokud `s` je `food`.</span><span class="sxs-lookup"><span data-stu-id="0aacd-229">For example, `s == "Food"` (`s = "Food"` in Visual Basic) and `s == "Food"` can yield different results if `s` is `food`.</span></span>

    ```sql
    -- Assume default US-English locale (case insensitive).
    create table T4 (
        Col1      nvarchar (256)
    )
    insert into T4 values (‘Food’)
    insert into T4 values (‘FOOD’)
    select * from T4 where Col1 = ‘food’
    -- Both the rows are returned because of case-insensitive matching.
    ```

[!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
[!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]

- <span data-ttu-id="0aacd-230">Operátory nebo funkce použít pro argumenty typu znaků pevné délky v SQL mají výrazně odlišnou sémantiku než stejné operátory nebo funkce u CLR <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0aacd-230">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0aacd-231">To může také zobrazit jako rozšíření chybí problému protějšek popsáno v části o typech.</span><span class="sxs-lookup"><span data-stu-id="0aacd-231">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>

    ```sql
    create table T4 (
        Col1      nchar(4)
    )
    Insert into T5(Col1) values ('21');
    Insert into T5(Col1) values ('1021');
    Select * from T5 where Col1 like '%1'
    -- Only the second row with Col1 = '1021' is returned.
    -- Not the first row!
    ```

     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]

     <span data-ttu-id="0aacd-232">Podobný problém se vyskytuje pomocí zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="0aacd-232">A similar problem occurs with string concatenation.</span></span>

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

<span data-ttu-id="0aacd-233">Stručně řečeno složitými překladu může být nezbytný pro CLR výrazy a další operátory nebo funkce může být nutné vystavit funkčnost SQL.</span><span class="sxs-lookup"><span data-stu-id="0aacd-233">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>

### <a name="type-casting"></a><span data-ttu-id="0aacd-234">Přetypování typu</span><span class="sxs-lookup"><span data-stu-id="0aacd-234">Type Casting</span></span>

<span data-ttu-id="0aacd-235">V C# a v SQL, můžou uživatelé potlačit výchozí sémantika výrazů pomocí přetypování explicitních typů (`Cast` a `Convert`).</span><span class="sxs-lookup"><span data-stu-id="0aacd-235">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="0aacd-236">Vystavení tuto funkci systému hranice typu však představuje dilema.</span><span class="sxs-lookup"><span data-stu-id="0aacd-236">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="0aacd-237">Přetypování SQL, která poskytuje požadovanou sémantiku nejde přeložit snadno do odpovídající C# přetypování.</span><span class="sxs-lookup"><span data-stu-id="0aacd-237">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="0aacd-238">Na druhé straně C# přetypování nelze přeložit přímo na ekvivalentní SQL přetypovat z důvodu neshody typů, chybějící protějšky a hierarchie prioritu různých typů.</span><span class="sxs-lookup"><span data-stu-id="0aacd-238">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="0aacd-239">Je kompromis mezi vystavení Neshoda typu systému a ztrátě významné sílu výrazu.</span><span class="sxs-lookup"><span data-stu-id="0aacd-239">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>

<span data-ttu-id="0aacd-240">V jiných případech nemusí být potřeba v obou domén pro ověření výrazu přetypování typu, ale může být vyžadováno, aby se zajistilo, že je správně použít jiné než výchozí mapování pro výraz.</span><span class="sxs-lookup"><span data-stu-id="0aacd-240">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a><span data-ttu-id="0aacd-241">Problémy s výkonem</span><span class="sxs-lookup"><span data-stu-id="0aacd-241">Performance Issues</span></span>

<span data-ttu-id="0aacd-242">Monitorování účtů pro některé-modulu CLR SQL serveru rozdíly typu může vést ke snížení výkonu při přecházení mezi mezi CLR a systému SQL Server typu systémy.</span><span class="sxs-lookup"><span data-stu-id="0aacd-242">Accounting for some SQL Server-CLR type differences may result in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="0aacd-243">Příklady scénářů vliv na výkon, patří:</span><span class="sxs-lookup"><span data-stu-id="0aacd-243">Examples of scenarios impacting performance include the following:</span></span>

- <span data-ttu-id="0aacd-244">Vynutit pořadí vyhodnocování pro logické a/nebo operátory</span><span class="sxs-lookup"><span data-stu-id="0aacd-244">Forced order of evaluation for logical and/or operators</span></span>

- <span data-ttu-id="0aacd-245">Generování SQL k vynucení pořadí vyhodnocení predikátu omezuje možnost optimalizace SQL.</span><span class="sxs-lookup"><span data-stu-id="0aacd-245">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>

- <span data-ttu-id="0aacd-246">Převody typů, ať už zavedené kompilátorem CLR nebo implementaci objektově-relační dotazu, může omezovat použití indexu.</span><span class="sxs-lookup"><span data-stu-id="0aacd-246">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>

     <span data-ttu-id="0aacd-247">Například</span><span class="sxs-lookup"><span data-stu-id="0aacd-247">For example,</span></span>

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     <span data-ttu-id="0aacd-248">Vezměte v úvahu překladu výrazu `(s = SOME_STRING_CONSTANT)`.</span><span class="sxs-lookup"><span data-stu-id="0aacd-248">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

<span data-ttu-id="0aacd-249">Kromě menší významové rozdíly je důležité vzít v úvahu dopad na výkon při přecházení mezi mezi SQL serverem a systémy typ CLR.</span><span class="sxs-lookup"><span data-stu-id="0aacd-249">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="0aacd-250">Pro velké datové sady můžete tyto problémy s výkonem zjistit, zda je aplikace nasadit.</span><span class="sxs-lookup"><span data-stu-id="0aacd-250">For large data sets, such performance issues can determine whether an application is deployable.</span></span>

## <a name="see-also"></a><span data-ttu-id="0aacd-251">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0aacd-251">See also</span></span>

- [<span data-ttu-id="0aacd-252">Základní informace</span><span class="sxs-lookup"><span data-stu-id="0aacd-252">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
