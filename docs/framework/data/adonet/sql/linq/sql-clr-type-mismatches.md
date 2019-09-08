---
title: Neshody typů SQL a CLR
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 27708f4bb8e191156f578132602570bc4a6337b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781196"
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="e656b-102">Neshody typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="e656b-102">SQL-CLR Type Mismatches</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="e656b-103">automatizuje většinu překladu mezi objektovým modelem a SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e656b-103">automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="e656b-104">Nicméně některé situace zabraňují přesnému překladu.</span><span class="sxs-lookup"><span data-stu-id="e656b-104">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="e656b-105">Tyto klíče se neshodují mezi typy modulu CLR (Common Language Runtime) a typy SQL Server databáze jsou shrnuty v následujících oddílech.</span><span class="sxs-lookup"><span data-stu-id="e656b-105">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="e656b-106">Další podrobnosti o konkrétních mapováních typů a překladu funkcí najdete v [mapování typů SQL-CLR](sql-clr-type-mapping.md) a [datových typů a funkcí](data-types-and-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e656b-106">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](sql-clr-type-mapping.md) and [Data Types and Functions](data-types-and-functions.md).</span></span>

## <a name="data-types"></a><span data-ttu-id="e656b-107">Datové typy</span><span class="sxs-lookup"><span data-stu-id="e656b-107">Data Types</span></span>

<span data-ttu-id="e656b-108">K překladu mezi CLR a SQL Server dochází při posílání dotazu do databáze a při posílání výsledků zpět do objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="e656b-108">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="e656b-109">Například následující dotaz Transact-SQL vyžaduje dva převody hodnot:</span><span class="sxs-lookup"><span data-stu-id="e656b-109">For example, the following Transact-SQL query requires two value conversions:</span></span>

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

<span data-ttu-id="e656b-110">Než bude možné spustit dotaz na SQL Server, musí být zadána hodnota parametru Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="e656b-110">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="e656b-111">V tomto příkladu `id` musí být hodnota parametru nejprve přeložena z typu CLR <xref:System.Int32?displayProperty=nameWithType> na typ SQL Server `INT` tak, aby databáze mohla pochopit, co je hodnota.</span><span class="sxs-lookup"><span data-stu-id="e656b-111">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="e656b-112">Pak pro načtení výsledků musí být sloupec SQL Server `DateOfBirth` přeložen z SQL Server `DATETIME` typu na typ CLR <xref:System.DateTime?displayProperty=nameWithType> pro použití v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="e656b-112">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="e656b-113">V tomto příkladu mají typy v objektovém modelu CLR a v databázi SQL Server přirozené mapování.</span><span class="sxs-lookup"><span data-stu-id="e656b-113">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="e656b-114">Nejedná se však vždy o případ.</span><span class="sxs-lookup"><span data-stu-id="e656b-114">But, this is not always the case.</span></span>

### <a name="missing-counterparts"></a><span data-ttu-id="e656b-115">Chybějící protějšky</span><span class="sxs-lookup"><span data-stu-id="e656b-115">Missing Counterparts</span></span>

<span data-ttu-id="e656b-116">Následující typy nemají přiměřené protějšky.</span><span class="sxs-lookup"><span data-stu-id="e656b-116">The following types do not have reasonable counterparts.</span></span>

- <span data-ttu-id="e656b-117">Neshoda v oboru názvů CLR <xref:System> :</span><span class="sxs-lookup"><span data-stu-id="e656b-117">Mismatches in the CLR <xref:System> namespace:</span></span>

  - <span data-ttu-id="e656b-118">**Celá čísla bez znaménka**.</span><span class="sxs-lookup"><span data-stu-id="e656b-118">**Unsigned integers**.</span></span> <span data-ttu-id="e656b-119">Tyto typy jsou obvykle mapovány na jejich podepsané protějšky větší velikosti, aby se předešlo přetečení.</span><span class="sxs-lookup"><span data-stu-id="e656b-119">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="e656b-120">Literály lze převést na číslo se znaménkem stejné nebo menší velikosti na základě hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e656b-120">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>

  - <span data-ttu-id="e656b-121">**Logická hodnota**.</span><span class="sxs-lookup"><span data-stu-id="e656b-121">**Boolean**.</span></span> <span data-ttu-id="e656b-122">Tyto typy mohou být mapovány na bit nebo větší řetězec čísla nebo řetězce.</span><span class="sxs-lookup"><span data-stu-id="e656b-122">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="e656b-123">Literál lze namapovat na výraz, který je vyhodnocen na stejnou hodnotu (například `1=1` v SQL pro `True` ve specifikaci CLS).</span><span class="sxs-lookup"><span data-stu-id="e656b-123">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>

  - <span data-ttu-id="e656b-124">**Časový**rozsah.</span><span class="sxs-lookup"><span data-stu-id="e656b-124">**TimeSpan**.</span></span> <span data-ttu-id="e656b-125">Tento typ představuje rozdíl mezi dvěma `DateTime` hodnotami a neodpovídá hodnotě `timestamp` SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e656b-125">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="e656b-126">CLR <xref:System.TimeSpan?displayProperty=nameWithType> může v některých případech také namapovat `TIME` na typ SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e656b-126">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="e656b-127">Typ SQL Server `TIME` měl představovat kladné hodnoty méně než 24 hodin.</span><span class="sxs-lookup"><span data-stu-id="e656b-127">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="e656b-128">CLR <xref:System.TimeSpan> má mnohem větší rozsah.</span><span class="sxs-lookup"><span data-stu-id="e656b-128">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e656b-129">V tomto porovnání nejsou zahrnuty SQL Server <xref:System.Data.SqlTypes> .NET Framework typy v nástroji.</span><span class="sxs-lookup"><span data-stu-id="e656b-129">SQL Server-specific .NET Framework types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>

- <span data-ttu-id="e656b-130">Neshoda v SQL Server:</span><span class="sxs-lookup"><span data-stu-id="e656b-130">Mismatches in SQL Server:</span></span>

  - <span data-ttu-id="e656b-131">**Typy znaků s pevnou délkou**.</span><span class="sxs-lookup"><span data-stu-id="e656b-131">**Fixed length character types**.</span></span> <span data-ttu-id="e656b-132">Transact-SQL rozlišuje mezi kategoriemi Unicode a non-Unicode a má tři různé typy v každé kategorii: pevná délka `nchar` `varchar` / `char`, proměnlivá `nvarchar`délka /a větší velikost `ntext`. / `text`</span><span class="sxs-lookup"><span data-stu-id="e656b-132">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="e656b-133">Typy znaků s pevnou délkou mohou být mapovány na <xref:System.Char?displayProperty=nameWithType> typ CLR pro načítání znaků, ale ve skutečnosti neodpovídají stejnému typu v rámci převodů a chování.</span><span class="sxs-lookup"><span data-stu-id="e656b-133">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>

  - <span data-ttu-id="e656b-134">**Bit**.</span><span class="sxs-lookup"><span data-stu-id="e656b-134">**Bit**.</span></span> <span data-ttu-id="e656b-135">I když má `Nullable<Boolean>`doména stejný počet hodnot, jsou tyto dva různé typy. `bit`</span><span class="sxs-lookup"><span data-stu-id="e656b-135">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="e656b-136">`Bit`přebírá `1` hodnoty `0` a místo `true`anelzeje použítjakoekvivalentlogickýchvýrazů/. `false`</span><span class="sxs-lookup"><span data-stu-id="e656b-136">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>

  - <span data-ttu-id="e656b-137">**Časové razítko**.</span><span class="sxs-lookup"><span data-stu-id="e656b-137">**Timestamp**.</span></span> <span data-ttu-id="e656b-138">Na rozdíl od typu <xref:System.TimeSpan?displayProperty=nameWithType> CLR představuje typ SQL Server `TIMESTAMP` číslo o velikosti 8 bajtů generované databází, která je jedinečná pro každou aktualizaci a není založena na rozdílu mezi <xref:System.DateTime> hodnotami.</span><span class="sxs-lookup"><span data-stu-id="e656b-138">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>

  - <span data-ttu-id="e656b-139">**Peníze** a **smallmoney**.</span><span class="sxs-lookup"><span data-stu-id="e656b-139">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="e656b-140">Tyto typy lze namapovat na <xref:System.Decimal> , ale jsou v podstatě různé typy a jsou zpracovány jako takové funkce a převody založené na serveru.</span><span class="sxs-lookup"><span data-stu-id="e656b-140">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>

### <a name="multiple-mappings"></a><span data-ttu-id="e656b-141">Vícenásobné mapování</span><span class="sxs-lookup"><span data-stu-id="e656b-141">Multiple Mappings</span></span>

<span data-ttu-id="e656b-142">Existuje mnoho SQL Server datových typů, které lze mapovat na jeden nebo více datových typů CLR.</span><span class="sxs-lookup"><span data-stu-id="e656b-142">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="e656b-143">Existuje také řada typů CLR, které lze namapovat na jeden nebo více typů SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e656b-143">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="e656b-144">I když mapování může být podporováno LINQ to SQL, neznamená to, že dva typy namapované mezi CLR a SQL Server jsou dokonalými shodami v přesnosti, rozsahu a sémantikě.</span><span class="sxs-lookup"><span data-stu-id="e656b-144">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="e656b-145">Některá mapování mohou zahrnovat rozdíly v některých nebo všech těchto dimenzích.</span><span class="sxs-lookup"><span data-stu-id="e656b-145">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="e656b-146">Můžete najít podrobnosti o těchto potenciálních rozdílech pro různé možnosti mapování v [mapování typu SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e656b-146">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

### <a name="user-defined-types"></a><span data-ttu-id="e656b-147">Uživatelsky definované typy</span><span class="sxs-lookup"><span data-stu-id="e656b-147">User-defined Types</span></span>

<span data-ttu-id="e656b-148">Uživatelsky definované typy CLR jsou navržené tak, aby pomohly přemostěníovat systémovou mezeru typu.</span><span class="sxs-lookup"><span data-stu-id="e656b-148">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="e656b-149">Nicméně mají na starosti zajímavé problémy se správou verzí typů.</span><span class="sxs-lookup"><span data-stu-id="e656b-149">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="e656b-150">Změna verze v klientovi se nemusí shodovat s změnou typu uloženého na databázovém serveru.</span><span class="sxs-lookup"><span data-stu-id="e656b-150">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="e656b-151">Tato změna způsobí neshodu jiného typu, kde se Sémantika typu neshoduje, a je pravděpodobné, že by se měla zobrazit mezera verze.</span><span class="sxs-lookup"><span data-stu-id="e656b-151">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="e656b-152">K dalším komplikacím dochází při refaktorování hierarchií dědičnosti v následných verzích.</span><span class="sxs-lookup"><span data-stu-id="e656b-152">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>

## <a name="expression-semantics"></a><span data-ttu-id="e656b-153">Sémantika výrazu</span><span class="sxs-lookup"><span data-stu-id="e656b-153">Expression Semantics</span></span>

<span data-ttu-id="e656b-154">Kromě neshody s neshodou mezi CLR a typy databází přidávají výrazy složitost k neshodě.</span><span class="sxs-lookup"><span data-stu-id="e656b-154">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="e656b-155">Neshoda sémantiky operátora, sémantika funkce, implicitní převod typu a pravidla priority musí být zvážena.</span><span class="sxs-lookup"><span data-stu-id="e656b-155">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>

<span data-ttu-id="e656b-156">Následující pododdíly ilustrují neshodu mezi zjevnými podobnými výrazy.</span><span class="sxs-lookup"><span data-stu-id="e656b-156">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="e656b-157">Je možné generovat výrazy SQL, které jsou sémanticky ekvivalentní danému výrazu CLR.</span><span class="sxs-lookup"><span data-stu-id="e656b-157">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="e656b-158">Není však jasné, zda jsou sémantické rozdíly mezi zjevnými podobnými výrazy zřejmé pro uživatele CLR, a proto zda jsou zamýšlené a nepotřebné změny pro sémantickou rovnocennost.</span><span class="sxs-lookup"><span data-stu-id="e656b-158">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="e656b-159">Jedná se o obzvláště kritický problém při vyhodnocování výrazu pro sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="e656b-159">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="e656b-160">Viditelnost rozdílu může záviset na datech a být obtížné identifikovat během kódování a ladění.</span><span class="sxs-lookup"><span data-stu-id="e656b-160">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>

### <a name="null-semantics"></a><span data-ttu-id="e656b-161">Sémantika s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="e656b-161">Null Semantics</span></span>

<span data-ttu-id="e656b-162">Výrazy SQL poskytují logiku se třemi hodnotami pro logické výrazy.</span><span class="sxs-lookup"><span data-stu-id="e656b-162">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="e656b-163">Výsledek může být true, false nebo null.</span><span class="sxs-lookup"><span data-stu-id="e656b-163">The result can be true, false, or null.</span></span> <span data-ttu-id="e656b-164">Naproti tomu CLR Určuje logický výsledek se dvěma hodnotami pro porovnání zahrnující hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="e656b-164">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="e656b-165">Vezměte v úvahu následující kód:</span><span class="sxs-lookup"><span data-stu-id="e656b-165">Consider the following code:</span></span>

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

<span data-ttu-id="e656b-166">K podobnému problému dochází se zachováním u výsledků se dvěma hodnotami.</span><span class="sxs-lookup"><span data-stu-id="e656b-166">A similar problem occurs with the assumption about two-valued results.</span></span>

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

<span data-ttu-id="e656b-167">V předchozím případě můžete získat ekvivalentní chování při generování SQL, ale překlad nemusí přesně odpovídat vašemu záměru.</span><span class="sxs-lookup"><span data-stu-id="e656b-167">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="e656b-168">nezavádí C# `null` ani neVisual Basic `nothing` sémantiky porovnání na SQL.</span><span class="sxs-lookup"><span data-stu-id="e656b-168">does not impose C# `null` or Visual Basic `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="e656b-169">Operátory porovnání jsou syntakticky přeloženy na jejich ekvivalenty SQL.</span><span class="sxs-lookup"><span data-stu-id="e656b-169">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="e656b-170">Sémantika odráží sémantiku systému SQL definovanou nastavením serveru nebo připojení.</span><span class="sxs-lookup"><span data-stu-id="e656b-170">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="e656b-171">Dvě hodnoty null se považují za neshodné s výchozím nastavením SQL Server (i když můžete změnit nastavení pro změnu sémantiky).</span><span class="sxs-lookup"><span data-stu-id="e656b-171">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="e656b-172">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bez ohledu na to nebere v úvahu nastavení serveru v překladu dotazů.</span><span class="sxs-lookup"><span data-stu-id="e656b-172">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>

<span data-ttu-id="e656b-173">Porovnání s literálem `null` (`nothing`) je přeloženo na odpovídající verzi SQL (`is null` nebo `is not null`).</span><span class="sxs-lookup"><span data-stu-id="e656b-173">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="e656b-174">Hodnota `null` (`nothing`) v kolaci je definována SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nemění kolaci.</span><span class="sxs-lookup"><span data-stu-id="e656b-174">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>

### <a name="type-conversion-and-promotion"></a><span data-ttu-id="e656b-175">Konverze a propagace typu</span><span class="sxs-lookup"><span data-stu-id="e656b-175">Type Conversion and Promotion</span></span>

<span data-ttu-id="e656b-176">SQL podporuje bohatou sadu implicitních převodů ve výrazech.</span><span class="sxs-lookup"><span data-stu-id="e656b-176">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="e656b-177">Podobné výrazy C# by vyžadovaly explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="e656b-177">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="e656b-178">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e656b-178">For example:</span></span>

- <span data-ttu-id="e656b-179">`Nvarchar`typy `DateTime` a lze v SQL porovnat bez explicitního přetypování; C# vyžaduje explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="e656b-179">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>

- <span data-ttu-id="e656b-180">`Decimal`je implicitně převeden na `DateTime` v SQL.</span><span class="sxs-lookup"><span data-stu-id="e656b-180">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="e656b-181">C#nepovoluje implicitní převod.</span><span class="sxs-lookup"><span data-stu-id="e656b-181">C# does not allow for an implicit conversion.</span></span>

<span data-ttu-id="e656b-182">Podobně, priorita typu v jazyce Transact-SQL se liší od priority typu v C# , protože podkladová sada typů je odlišná.</span><span class="sxs-lookup"><span data-stu-id="e656b-182">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="e656b-183">Ve skutečnosti neexistují žádné jasné vztahy mezi podmnožinou a nadmnožinou mezi seznamy priorit.</span><span class="sxs-lookup"><span data-stu-id="e656b-183">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="e656b-184">Například porovnávání `nvarchar` s objektem `varchar` způsobí implicitní převod `varchar` výrazu na `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="e656b-184">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="e656b-185">CLR neposkytuje žádnou ekvivalentní povýšení.</span><span class="sxs-lookup"><span data-stu-id="e656b-185">The CLR provides no equivalent promotion.</span></span>

<span data-ttu-id="e656b-186">V jednoduchých případech tyto rozdíly způsobují, že výrazy CLR s přetypováními mají být redundantní pro odpovídající výraz SQL.</span><span class="sxs-lookup"><span data-stu-id="e656b-186">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="e656b-187">Důležitější je, že mezilehlé výsledky výrazu SQL mohou být implicitně povýšeny na typ, který nemá přesnou protějšek v C#a naopak.</span><span class="sxs-lookup"><span data-stu-id="e656b-187">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="e656b-188">Celkový počet, testování, ladění a ověřování těchto výrazů přináší významné zatížení uživatele.</span><span class="sxs-lookup"><span data-stu-id="e656b-188">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>

### <a name="collation"></a><span data-ttu-id="e656b-189">Kolace</span><span class="sxs-lookup"><span data-stu-id="e656b-189">Collation</span></span>

<span data-ttu-id="e656b-190">Transact-SQL podporuje explicitní kolace jako anotace typů řetězců znaků.</span><span class="sxs-lookup"><span data-stu-id="e656b-190">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="e656b-191">Tato kolace určují platnost určitých porovnání.</span><span class="sxs-lookup"><span data-stu-id="e656b-191">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="e656b-192">Například porovnávání dvou sloupců s různými explicitními kolací je chyba.</span><span class="sxs-lookup"><span data-stu-id="e656b-192">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="e656b-193">Použití mnohem zjednodušeného typu řetězce CTS nezpůsobuje takové chyby.</span><span class="sxs-lookup"><span data-stu-id="e656b-193">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="e656b-194">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e656b-194">Consider the following example:</span></span>

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

<span data-ttu-id="e656b-195">V důsledku toho podklauzule kolace vytvoří *omezený typ* , který nelze nahradit.</span><span class="sxs-lookup"><span data-stu-id="e656b-195">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>

<span data-ttu-id="e656b-196">Podobně je možné pořadí řazení výrazně lišit napříč systémy typů.</span><span class="sxs-lookup"><span data-stu-id="e656b-196">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="e656b-197">Tento rozdíl ovlivňuje řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="e656b-197">This difference affects the sorting of results.</span></span> <span data-ttu-id="e656b-198"><xref:System.Guid>je řazeno na všech 16 bajtů podle lexikografickým pořadím Order`IComparable()`(), zatímco T-SQL porovnává identifikátory GUID v následujícím pořadí: node (10-15), Clock-SEQ (8-9), Time-high (6-7), Time-Mid (4-5), časový-dolní (0-3).</span><span class="sxs-lookup"><span data-stu-id="e656b-198"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="e656b-199">Toto řazení bylo provedeno ve formátu SQL 7,0, pokud měly identifikátory GUID generované systémem NT takové pořadí oktetů.</span><span class="sxs-lookup"><span data-stu-id="e656b-199">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="e656b-200">Přístup zajišťuje, aby identifikátory GUID generované v clusteru stejného uzlu byly společně v sekvenčním pořadí podle časového razítka.</span><span class="sxs-lookup"><span data-stu-id="e656b-200">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="e656b-201">Přístup byl také užitečný pro vytváření indexů (příkazy INSERT se stanou připojením místo náhodného IOs).</span><span class="sxs-lookup"><span data-stu-id="e656b-201">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="e656b-202">Pořadí bylo ve Windows později zakódované z důvodu ochrany osobních údajů, ale SQL musí zachovat kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="e656b-202">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="e656b-203">Alternativním řešením je použít <xref:System.Data.SqlTypes.SqlGuid> <xref:System.Guid>místo.</span><span class="sxs-lookup"><span data-stu-id="e656b-203">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>

### <a name="operator-and-function-differences"></a><span data-ttu-id="e656b-204">Operátory a funkce – rozdíly</span><span class="sxs-lookup"><span data-stu-id="e656b-204">Operator and Function Differences</span></span>

<span data-ttu-id="e656b-205">Operátory a funkce, které jsou v podstatě srovnatelné, mají mírně odlišnou sémantiku.</span><span class="sxs-lookup"><span data-stu-id="e656b-205">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="e656b-206">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e656b-206">For example:</span></span>

- <span data-ttu-id="e656b-207">C#Určuje sémantiku krátkého okruhu na základě lexikálního pořadí operandů pro `&&` logické `||`operátory a.</span><span class="sxs-lookup"><span data-stu-id="e656b-207">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="e656b-208">SQL na druhé straně je zaměřený na dotazy založené na sadě, a proto nabízí větší volnost v tom, aby Optimalizátor určilo pořadí spouštění.</span><span class="sxs-lookup"><span data-stu-id="e656b-208">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="e656b-209">Mezi důsledky patří následující:</span><span class="sxs-lookup"><span data-stu-id="e656b-209">Some of the implications include the following:</span></span>

  - <span data-ttu-id="e656b-210">Překlad sémanticky ekvivalentního překladu by`CASE` vyžadoval "...</span><span class="sxs-lookup"><span data-stu-id="e656b-210">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="e656b-211">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="e656b-211">`WHEN` …</span></span> <span data-ttu-id="e656b-212">`THEN`"konstrukce v jazyce SQL, aby se zabránilo přeřazení spuštění operandu.</span><span class="sxs-lookup"><span data-stu-id="e656b-212">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>

  - <span data-ttu-id="e656b-213">Volný `AND` převod na / operátory`OR` může způsobit neočekávané chyby, pokud C# výraz spoléhá na vyhodnocení druhého operandu na základě výsledku vyhodnocení prvního operandu.</span><span class="sxs-lookup"><span data-stu-id="e656b-213">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>

- <span data-ttu-id="e656b-214">`Round()`funkce má odlišnou sémantiku v .NET Framework a v T-SQL.</span><span class="sxs-lookup"><span data-stu-id="e656b-214">`Round()` function has different semantics in .NET Framework and in T-SQL.</span></span>

- <span data-ttu-id="e656b-215">Počáteční index pro řetězce je 0 v modulu CLR, ale 1 v SQL.</span><span class="sxs-lookup"><span data-stu-id="e656b-215">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="e656b-216">Proto všechny funkce, které mají index, vyžadují překlad indexu.</span><span class="sxs-lookup"><span data-stu-id="e656b-216">Therefore, any function that has index needs index translation.</span></span>

- <span data-ttu-id="e656b-217">Modul CLR podporuje operátor dělení ('% ') pro čísla s plovoucí desetinnou čárkou, ale SQL nikoli.</span><span class="sxs-lookup"><span data-stu-id="e656b-217">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>

- <span data-ttu-id="e656b-218">`Like` Operátor efektivně získá Automatická přetížení na základě implicitních převodů.</span><span class="sxs-lookup"><span data-stu-id="e656b-218">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="e656b-219">I když je `DateTime` `Like` operátor definován pro práci na typech řetězců znaků, implicitní převod z číselných typů nebo typů umožňuje používat tyto neřetězcové typy, a to stejně. `Like`</span><span class="sxs-lookup"><span data-stu-id="e656b-219">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="e656b-220">V CTS neexistují srovnatelné implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="e656b-220">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="e656b-221">Proto jsou potřeba další přetížení.</span><span class="sxs-lookup"><span data-stu-id="e656b-221">Therefore, additional overloads are needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e656b-222">Toto `Like` chování operátoru platí C# jenom pro; klíčové `Like` slovo Visual Basic se nezměnilo.</span><span class="sxs-lookup"><span data-stu-id="e656b-222">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>

- <span data-ttu-id="e656b-223">Přetečení je vždy zaškrtnuto v SQL, ale je nutné ji explicitně zadat C# v (ne v Visual Basic), aby se předešlo wraparound.</span><span class="sxs-lookup"><span data-stu-id="e656b-223">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in Visual Basic) to avoid wraparound.</span></span> <span data-ttu-id="e656b-224">Předané celočíselné sloupce C1, C2 a C3, pokud je C1 + C2 uložen v C3 (Update T set C3 = C1 + C2).</span><span class="sxs-lookup"><span data-stu-id="e656b-224">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>

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

- <span data-ttu-id="e656b-225">SQL provádí symetrické aritmetické zaokrouhlování při .NET Framework používá zaokrouhlování bank.</span><span class="sxs-lookup"><span data-stu-id="e656b-225">SQL performs symmetric arithmetic rounding while .NET Framework uses banker’s rounding.</span></span> <span data-ttu-id="e656b-226">Další podrobnosti najdete v článku 196652 znalostní báze.</span><span class="sxs-lookup"><span data-stu-id="e656b-226">See Knowledgebase article 196652 for additional details.</span></span>

- <span data-ttu-id="e656b-227">Ve výchozím nastavení se u běžných národních prostředí a porovnávání znakových řetězců rozlišují velká a malá písmena v SQL.</span><span class="sxs-lookup"><span data-stu-id="e656b-227">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="e656b-228">V Visual Basic a v C#se rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="e656b-228">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="e656b-229">Například `s == "Food"` `s` (`s = "Food"` v Visual Basic) a `s == "Food"` mohou vracet různé výsledky, pokud je `food`.</span><span class="sxs-lookup"><span data-stu-id="e656b-229">For example, `s == "Food"` (`s = "Food"` in Visual Basic) and `s == "Food"` can yield different results if `s` is `food`.</span></span>

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

- <span data-ttu-id="e656b-230">Operátory nebo funkce aplikované na argumenty znakového typu s pevnou délkou v SQL mají výrazně odlišnou sémantiku než stejné operátory nebo funkce <xref:System.String?displayProperty=nameWithType>aplikované na CLR.</span><span class="sxs-lookup"><span data-stu-id="e656b-230">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e656b-231">Může se také zobrazit jako rozšíření chybějícího problému s protějškem, který je popsán v části o typech.</span><span class="sxs-lookup"><span data-stu-id="e656b-231">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>

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

     <span data-ttu-id="e656b-232">K podobnému problému dochází při zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="e656b-232">A similar problem occurs with string concatenation.</span></span>

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

<span data-ttu-id="e656b-233">V souhrnu může být pro výrazy CLR vyžadován překlad konvoluce a další operátory/funkce mohou být nezbytné k vystavení funkcí SQL.</span><span class="sxs-lookup"><span data-stu-id="e656b-233">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>

### <a name="type-casting"></a><span data-ttu-id="e656b-234">Přetypování typu</span><span class="sxs-lookup"><span data-stu-id="e656b-234">Type Casting</span></span>

<span data-ttu-id="e656b-235">V C# a v SQL mohou uživatelé přepsat výchozí sémantiku výrazů pomocí explicitních přetypování typů (`Cast` a `Convert`).</span><span class="sxs-lookup"><span data-stu-id="e656b-235">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="e656b-236">Vystavení této funkce napříč hranicí systému typů ale představuje dilematem.</span><span class="sxs-lookup"><span data-stu-id="e656b-236">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="e656b-237">Přetypování SQL, které poskytuje požadovanou sémantiku, nelze snadno přeložit na odpovídající C# přetypování.</span><span class="sxs-lookup"><span data-stu-id="e656b-237">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="e656b-238">Na druhé straně C# přetypování nejde přímo přeložit do ekvivalentního přetypování SQL z důvodu neshody typů, chybějících protějšků a různých hierarchií s prioritami typů.</span><span class="sxs-lookup"><span data-stu-id="e656b-238">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="e656b-239">Vystavení neshody typů systému a ztráty významného výkonu výrazu je kompromis.</span><span class="sxs-lookup"><span data-stu-id="e656b-239">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>

<span data-ttu-id="e656b-240">V jiných případech nemusí být přetypování typu potřeba v žádné doméně pro ověření výrazu, ale může být potřeba, aby se zajistilo, že se pro výraz správně použije mapování bez výchozího nastavení.</span><span class="sxs-lookup"><span data-stu-id="e656b-240">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>

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

## <a name="performance-issues"></a><span data-ttu-id="e656b-241">Problémy s výkonem</span><span class="sxs-lookup"><span data-stu-id="e656b-241">Performance Issues</span></span>

<span data-ttu-id="e656b-242">Monitorování účtů pro některé rozdíly typu SQL Server-CLR může způsobit snížení výkonu při přechodu mezi systémy CLR a SQL Server typů.</span><span class="sxs-lookup"><span data-stu-id="e656b-242">Accounting for some SQL Server-CLR type differences may result in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="e656b-243">Mezi příklady scénářů, které mají vliv na výkon, patří následující:</span><span class="sxs-lookup"><span data-stu-id="e656b-243">Examples of scenarios impacting performance include the following:</span></span>

- <span data-ttu-id="e656b-244">Vynucené pořadí vyhodnocení pro logické operátory and/or</span><span class="sxs-lookup"><span data-stu-id="e656b-244">Forced order of evaluation for logical and/or operators</span></span>

- <span data-ttu-id="e656b-245">Generování SQL pro vynucení pořadí vyhodnocování predikátu omezuje schopnost Optimalizátoru SQL.</span><span class="sxs-lookup"><span data-stu-id="e656b-245">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>

- <span data-ttu-id="e656b-246">Převody typů, ať už zavedené kompilátorem CLR nebo implementace relačních dotazů objektu, můžou curtail využití indexu.</span><span class="sxs-lookup"><span data-stu-id="e656b-246">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>

     <span data-ttu-id="e656b-247">Například</span><span class="sxs-lookup"><span data-stu-id="e656b-247">For example,</span></span>

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     <span data-ttu-id="e656b-248">Zvažte převod výrazu `(s = SOME_STRING_CONSTANT)`.</span><span class="sxs-lookup"><span data-stu-id="e656b-248">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>

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

<span data-ttu-id="e656b-249">Kromě sémantických rozdílů je důležité vzít v úvahu dopady na výkon při přechodu mezi systémy SQL Server a CLR typů.</span><span class="sxs-lookup"><span data-stu-id="e656b-249">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="e656b-250">U velkých datových sad můžou takové problémy s výkonem určit, jestli je možné aplikaci nasadit.</span><span class="sxs-lookup"><span data-stu-id="e656b-250">For large data sets, such performance issues can determine whether an application is deployable.</span></span>

## <a name="see-also"></a><span data-ttu-id="e656b-251">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e656b-251">See also</span></span>

- [<span data-ttu-id="e656b-252">Základní informace</span><span class="sxs-lookup"><span data-stu-id="e656b-252">Background Information</span></span>](background-information.md)
