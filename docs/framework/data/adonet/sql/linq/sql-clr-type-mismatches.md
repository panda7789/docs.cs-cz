---
title: Neshody typu SQL CLR
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
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cc1458996e70e8af05c4e2bc9e6c61a5d8a9f87d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="sql-clr-type-mismatches"></a><span data-ttu-id="c3347-102">Neshody typu SQL CLR</span><span class="sxs-lookup"><span data-stu-id="c3347-102">SQL-CLR Type Mismatches</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c3347-103">umožňuje automatizovat většinu překlad mezi objektový model a SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c3347-103"> automates much of the translation between the object model and SQL Server.</span></span> <span data-ttu-id="c3347-104">Nicméně některých situacích zabránit přesný překlad.</span><span class="sxs-lookup"><span data-stu-id="c3347-104">Nevertheless, some situations prevent exact translation.</span></span> <span data-ttu-id="c3347-105">Tyto klíče neshody mezi běžné typy language runtime (CLR) a typy databáze systému SQL Server jsou shrnuty v následující části.</span><span class="sxs-lookup"><span data-stu-id="c3347-105">These key mismatches between the common language runtime (CLR) types and the SQL Server database types are summarized in the following sections.</span></span> <span data-ttu-id="c3347-106">Můžete najít další podrobnosti o konkrétní typ mapování a funkce překladu v [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) a [datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span><span class="sxs-lookup"><span data-stu-id="c3347-106">You can find more details about specific type mappings and function translation at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) and [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="c3347-107">Datové typy</span><span class="sxs-lookup"><span data-stu-id="c3347-107">Data Types</span></span>  
 <span data-ttu-id="c3347-108">Při odesílání dotazu do databáze, a při výsledky budou odeslány do objektový model dochází k převodu mezi CLR a SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c3347-108">Translation between the CLR and SQL Server occurs when a query is being sent to the database, and when the results are sent back to your object model.</span></span> <span data-ttu-id="c3347-109">Například následující dotaz jazyka Transact-SQL vyžaduje dva převody hodnot:</span><span class="sxs-lookup"><span data-stu-id="c3347-109">For example, the following Transact-SQL query requires two value conversions:</span></span>  
  
```  
Select DateOfBirth From Customer Where CustomerId = @id     
```  
  
 <span data-ttu-id="c3347-110">Aby bylo možné spustit dotaz na serveru SQL Server, musí být zadána hodnota pro parametr Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="c3347-110">Before the query can be executed on SQL Server, the value for the Transact-SQL parameter must be specified.</span></span> <span data-ttu-id="c3347-111">V tomto příkladu `id` hodnota parametru musí být nejprve převedeny z modulu CLR <xref:System.Int32?displayProperty=nameWithType> typ k systému SQL Server `INT` zadejte tak, aby databáze můžete porozumět, co je hodnota.</span><span class="sxs-lookup"><span data-stu-id="c3347-111">In this example, the `id` parameter value must first be translated from a CLR <xref:System.Int32?displayProperty=nameWithType> type to a SQL Server `INT` type so that the database can understand what the value is.</span></span> <span data-ttu-id="c3347-112">Pak se načíst výsledky, SQL Server `DateOfBirth` sloupec musí být převedeny z SQL serveru `DATETIME` typ, který má CLR <xref:System.DateTime?displayProperty=nameWithType> typ pro použití v modelu objektu.</span><span class="sxs-lookup"><span data-stu-id="c3347-112">Then to retrieve the results, the SQL Server `DateOfBirth` column must be translated from a SQL Server `DATETIME` type to a CLR <xref:System.DateTime?displayProperty=nameWithType> type for use in the object model.</span></span> <span data-ttu-id="c3347-113">Typy v modelu objektu CLR a databáze systému SQL Server v tomto příkladu se mít fyzické mapování.</span><span class="sxs-lookup"><span data-stu-id="c3347-113">In this example, the types in the CLR object model and SQL Server database have natural mappings.</span></span> <span data-ttu-id="c3347-114">Ale není to vždy.</span><span class="sxs-lookup"><span data-stu-id="c3347-114">But, this is not always the case.</span></span>  
  
### <a name="missing-counterparts"></a><span data-ttu-id="c3347-115">Chybí svými protějšky</span><span class="sxs-lookup"><span data-stu-id="c3347-115">Missing Counterparts</span></span>  
 <span data-ttu-id="c3347-116">Následující typy nemají přiměřené svými protějšky.</span><span class="sxs-lookup"><span data-stu-id="c3347-116">The following types do not have reasonable counterparts.</span></span>  
  
-   <span data-ttu-id="c3347-117">V modulu CLR se neshoduje <xref:System> obor názvů:</span><span class="sxs-lookup"><span data-stu-id="c3347-117">Mismatches in the CLR <xref:System> namespace:</span></span>  
  
    -   <span data-ttu-id="c3347-118">**Nepodepsané celá čísla**.</span><span class="sxs-lookup"><span data-stu-id="c3347-118">**Unsigned integers**.</span></span> <span data-ttu-id="c3347-119">Tyto typy jsou obvykle namapované na jejich podepsané svými protějšky větší velikosti předejdete přetečení.</span><span class="sxs-lookup"><span data-stu-id="c3347-119">These types are typically mapped to their signed counterparts of larger size to avoid overflow.</span></span> <span data-ttu-id="c3347-120">Literály lze převést na podepsané číselný stejné nebo menší velikosti, na základě hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c3347-120">Literals can be converted to a signed numeric of the same or smaller size, based on value.</span></span>  
  
    -   <span data-ttu-id="c3347-121">**Logická hodnota**.</span><span class="sxs-lookup"><span data-stu-id="c3347-121">**Boolean**.</span></span> <span data-ttu-id="c3347-122">Tyto typy lze mapovat na bit nebo větší číselnou nebo řetězec.</span><span class="sxs-lookup"><span data-stu-id="c3347-122">These types can be mapped to a bit or larger numeric or string.</span></span> <span data-ttu-id="c3347-123">Literál lze mapovat na výraz, který se vyhodnotí na stejnou hodnotu (například `1=1` v SQL pro `True` ve CLS).</span><span class="sxs-lookup"><span data-stu-id="c3347-123">A literal can be mapped to an expression that evaluates to the same value (for example, `1=1` in SQL for `True` in CLS).</span></span>  
  
    -   <span data-ttu-id="c3347-124">**Časový interval**.</span><span class="sxs-lookup"><span data-stu-id="c3347-124">**TimeSpan**.</span></span> <span data-ttu-id="c3347-125">Tento typ reprezentuje rozdíl mezi dvěma `DateTime` hodnoty a nemusí odpovídat `timestamp` systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c3347-125">This type represents the difference between two `DateTime` values and does not correspond to the `timestamp` of SQL Server.</span></span> <span data-ttu-id="c3347-126">Modul CLR <xref:System.TimeSpan?displayProperty=nameWithType> také mapovat k systému SQL Server `TIME` typu v některých případech.</span><span class="sxs-lookup"><span data-stu-id="c3347-126">The CLR <xref:System.TimeSpan?displayProperty=nameWithType> may also map to the SQL Server `TIME` type in some cases.</span></span> <span data-ttu-id="c3347-127">SQL Server `TIME` typu byla určena pouze kladné hodnoty představují méně než 24 hodin.</span><span class="sxs-lookup"><span data-stu-id="c3347-127">The SQL Server `TIME` type was only intended to represent positive values less than 24 hours.</span></span> <span data-ttu-id="c3347-128">Modul CLR <xref:System.TimeSpan> má mnohem větší rozsah.</span><span class="sxs-lookup"><span data-stu-id="c3347-128">The CLR <xref:System.TimeSpan> has a much larger range.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3347-129">Specifické pro službu SQL Server [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] typy v <xref:System.Data.SqlTypes> nejsou součástí Toto porovnání.</span><span class="sxs-lookup"><span data-stu-id="c3347-129">SQL Server-specific [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] types in <xref:System.Data.SqlTypes> are not included in this comparison.</span></span>  
  
-   <span data-ttu-id="c3347-130">Neshody v systému SQL Server:</span><span class="sxs-lookup"><span data-stu-id="c3347-130">Mismatches in SQL Server:</span></span>  
  
    -   <span data-ttu-id="c3347-131">**Pevná délka znakové typy**.</span><span class="sxs-lookup"><span data-stu-id="c3347-131">**Fixed length character types**.</span></span> <span data-ttu-id="c3347-132">Příkaz Transact-SQL rozlišuje mezi kategorií kódování Unicode a kódování Unicode a má tři odlišné typy v každé kategorii: pevná délka `nchar` / `char`, proměnlivou délkou `nvarchar` / `varchar`, a větší velikost `ntext` / `text`.</span><span class="sxs-lookup"><span data-stu-id="c3347-132">Transact-SQL distinguishes between Unicode and non-Unicode categories and has three distinct types in each category: fixed length `nchar`/`char`, variable length `nvarchar`/`varchar`, and larger-sized `ntext`/`text`.</span></span> <span data-ttu-id="c3347-133">Typy znaků pevnou délkou mapovat modulu CLR <xref:System.Char?displayProperty=nameWithType> typ pro načítání znaků, ale jejich nemusí odpovídat skutečně stejného typu v převody a chování.</span><span class="sxs-lookup"><span data-stu-id="c3347-133">The fixed length character types could be mapped to the CLR <xref:System.Char?displayProperty=nameWithType> type for retrieving characters, but they do not really correspond to the same type in conversions and behavior.</span></span>  
  
    -   <span data-ttu-id="c3347-134">**Bit**.</span><span class="sxs-lookup"><span data-stu-id="c3347-134">**Bit**.</span></span> <span data-ttu-id="c3347-135">I když `bit` stejný počet hodnot, jako má doména `Nullable<Boolean>`, jsou dva různé typy.</span><span class="sxs-lookup"><span data-stu-id="c3347-135">Although the `bit` domain has the same number of values as `Nullable<Boolean>`, the two are different types.</span></span> <span data-ttu-id="c3347-136">`Bit`přijímá hodnoty `1` a `0` místo `true` / `false`a nelze jej použít jako rovnocenné výrazy logických hodnot.</span><span class="sxs-lookup"><span data-stu-id="c3347-136">`Bit` takes values `1` and `0` instead of `true`/`false`, and cannot be used as an equivalent to Boolean expressions.</span></span>  
  
    -   <span data-ttu-id="c3347-137">**Časové razítko**.</span><span class="sxs-lookup"><span data-stu-id="c3347-137">**Timestamp**.</span></span> <span data-ttu-id="c3347-138">Na rozdíl od CLR <xref:System.TimeSpan?displayProperty=nameWithType> typ, SQL Server `TIMESTAMP` typ představuje číslo 8 bajtů generovaných databázi, která je jedinečné pro jednotlivé aktualizace a není založena na rozdíl mezi <xref:System.DateTime> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c3347-138">Unlike the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type, the SQL Server `TIMESTAMP` type represents an 8-byte number generated by the database that is unique for each update and is not based on the difference between <xref:System.DateTime> values.</span></span>  
  
    -   <span data-ttu-id="c3347-139">**Peníze** a **SmallMoney**.</span><span class="sxs-lookup"><span data-stu-id="c3347-139">**Money** and **SmallMoney**.</span></span> <span data-ttu-id="c3347-140">Tyto typy lze mapovat na <xref:System.Decimal> , ale jsou v podstatě různé typy a jako takový nakládá serverových funkcí a převody.</span><span class="sxs-lookup"><span data-stu-id="c3347-140">These types can be mapped to <xref:System.Decimal> but are basically different types and are treated as such by server-based functions and conversions.</span></span>  
  
### <a name="multiple-mappings"></a><span data-ttu-id="c3347-141">Víc mapování</span><span class="sxs-lookup"><span data-stu-id="c3347-141">Multiple Mappings</span></span>  
 <span data-ttu-id="c3347-142">Existuje mnoho typů dat systému SQL Server, které můžete namapovat na jeden nebo více typů CLR data.</span><span class="sxs-lookup"><span data-stu-id="c3347-142">There are many SQL Server data types that you can map to one or more CLR data types.</span></span> <span data-ttu-id="c3347-143">Existují také mnoho typů CLR, které můžete namapovat na jeden nebo více typů systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c3347-143">There are also many CLR types that you can map to one or more SQL Server types.</span></span> <span data-ttu-id="c3347-144">I když mapování může být podporovaná technologií LINQ to SQL, neznamená to, že existují dva typy namapované mezi CLR a SQL Server jsou ideální shoda v přesnost, rozsah a sémantiku.</span><span class="sxs-lookup"><span data-stu-id="c3347-144">Although a mapping may be supported by LINQ to SQL, it does not mean that the two types mapped between the CLR and SQL Server are a perfect match in precision, range, and semantics.</span></span> <span data-ttu-id="c3347-145">Některé mapování může zahrnovat rozdíly v některého nebo všech z těchto dimenzí.</span><span class="sxs-lookup"><span data-stu-id="c3347-145">Some mappings may include differences in any or all of these dimensions.</span></span> <span data-ttu-id="c3347-146">Můžete najít podrobnosti o těchto potenciální rozdíly pro různé možnosti mapování na [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="c3347-146">You can find details about these potential differences for the various mapping possibilities at [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
### <a name="user-defined-types"></a><span data-ttu-id="c3347-147">Uživatelem definované typy</span><span class="sxs-lookup"><span data-stu-id="c3347-147">User-defined Types</span></span>  
 <span data-ttu-id="c3347-148">Uživatelem definované typy CLR jsou navržené tak, abyste přemostění mezery typ systému.</span><span class="sxs-lookup"><span data-stu-id="c3347-148">User-defined CLR types are designed to help bridge the type system gap.</span></span> <span data-ttu-id="c3347-149">Nicméně surface zajímavé problémy o správě verzí typu.</span><span class="sxs-lookup"><span data-stu-id="c3347-149">Nevertheless they surface interesting issues about type versioning.</span></span> <span data-ttu-id="c3347-150">Ke změně verze na klienta nemusí odpovídat změnou v typu uložené na serveru databáze.</span><span class="sxs-lookup"><span data-stu-id="c3347-150">A change in the version on the client might not be matched by a change in the type stored on the database server.</span></span> <span data-ttu-id="c3347-151">Všechny tyto změny způsobí, že jiný Neshoda typu, kde nemusí odpovídat Sémantika typu a mezera verze je pravděpodobně budou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="c3347-151">Any such change causes another type mismatch where the type semantics might not match and the version gap is likely to become visible.</span></span> <span data-ttu-id="c3347-152">Další komplikace docházet k hierarchie dědičnosti jsou rozdělili v následných verzí.</span><span class="sxs-lookup"><span data-stu-id="c3347-152">Further complications occur as inheritance hierarchies are refactored in successive versions.</span></span>  
  
## <a name="expression-semantics"></a><span data-ttu-id="c3347-153">Sémantika výrazů</span><span class="sxs-lookup"><span data-stu-id="c3347-153">Expression Semantics</span></span>  
 <span data-ttu-id="c3347-154">Kromě pairwise neshody mezi typy CLR a databáze výrazy přidání složitosti do neshody.</span><span class="sxs-lookup"><span data-stu-id="c3347-154">In addition to the pairwise mismatch between CLR and database types, expressions add complexity to the mismatch.</span></span> <span data-ttu-id="c3347-155">Je třeba zvážit neshody v operátor sémantiku, funkce sémantiku, převod implicitní typu a pravidla priorit.</span><span class="sxs-lookup"><span data-stu-id="c3347-155">Mismatches in operator semantics, function semantics, implicit type conversion, and precedence rules must be considered.</span></span>  
  
 <span data-ttu-id="c3347-156">Následující témata ukazují neshody mezi zjevně podobné výrazy.</span><span class="sxs-lookup"><span data-stu-id="c3347-156">The following subsections illustrate the mismatch between apparently similar expressions.</span></span> <span data-ttu-id="c3347-157">Může být možné generovat SQL výrazů, které odpovídají sémanticky daného výrazu CLR.</span><span class="sxs-lookup"><span data-stu-id="c3347-157">It might be possible to generate SQL expressions that are semantically equivalent to a given CLR expression.</span></span> <span data-ttu-id="c3347-158">Ale není jasné jestli sémantického rozdíly mezi zjevně podobné výrazy jsou zřejmá CLR uživateli, a proto jestli jsou změny, které jsou požadovány pro sémantické ekvivalenční určené nebo ne.</span><span class="sxs-lookup"><span data-stu-id="c3347-158">However, it is not clear whether the semantic differences between apparently similar expressions are evident to a CLR user, and therefore whether the changes that are required for semantic equivalence are intended or not.</span></span> <span data-ttu-id="c3347-159">To je obzvláště důležité problém při vyhodnocování výrazu pro sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="c3347-159">This is an especially critical issue when an expression is evaluated for a set of values.</span></span> <span data-ttu-id="c3347-160">Viditelnost rozdíl může závisí na data - a bude obtížné určit během kódování a ladění.</span><span class="sxs-lookup"><span data-stu-id="c3347-160">The visibility of the difference might depend on data- and be hard to identify during coding and debugging.</span></span>  
  
### <a name="null-semantics"></a><span data-ttu-id="c3347-161">Sémantika hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="c3347-161">Null Semantics</span></span>  
 <span data-ttu-id="c3347-162">Výrazy SQL zadejte s hodnotou tři logiku pro výrazy logických hodnot.</span><span class="sxs-lookup"><span data-stu-id="c3347-162">SQL expressions provide three-valued logic for Boolean expressions.</span></span> <span data-ttu-id="c3347-163">Výsledkem mohou být true, false nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c3347-163">The result can be true, false, or null.</span></span> <span data-ttu-id="c3347-164">Naopak CLR určuje dvěma hodnotami výsledek logickou hodnotu pro porovnání zahrnující hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="c3347-164">By contrast, CLR specifies two-valued Boolean result for comparisons involving null values.</span></span> <span data-ttu-id="c3347-165">Vezměte v úvahu následující kód:</span><span class="sxs-lookup"><span data-stu-id="c3347-165">Consider the following code:</span></span>  
  
 [!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
 [!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]  
  
```  
-- Assume col1 and col2 are integer columns with null values.   
-- Assume that ANSI null behavior has not been explicitly  
--    turned off.  
Select …  
From …  
Where col1 = col2  
-- Evaluates to null, not true and the corresponding row is not  
--     selected.  
-- To obtain matching behavior (i -> col1, j -> col2) change  
--     the query to the following:  
Select …  
From …  
Where  
    col1 = col2   
or (col1 is null and col2 is null)  
-- (Visual Basic 'Nothing'.)  
```  
  
 <span data-ttu-id="c3347-166">Podobně jako nastaly problémy s předpokladem o výsledcích dvěma hodnotami.</span><span class="sxs-lookup"><span data-stu-id="c3347-166">A similar problem occurs with the assumption about two-valued results.</span></span>  
  
 [!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
 [!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]  
  
```  
-- Assume col1 and col2 are nullable columns.  
-- Assume that ANSI null behavior has not been explicitly  
--     turned off.  
Select …  
From …  
Where  
    col1 = col2        
or col1 != col2  
-- Visual Basic: col1 <> col2.  
  
-- Excludes the case where the boolean expression evaluates  
--     to null. Therefore the where clause does not always  
--     evaluate to true.  
```  
  
 <span data-ttu-id="c3347-167">V předchozím případě můžete získat ekvivalentní chování při generování SQL, ale překlad nemusí přesně odrážet svůj záměr.</span><span class="sxs-lookup"><span data-stu-id="c3347-167">In the previous case, you can get equivalent behavior in generating SQL, but the translation might not accurately reflect your intention.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c3347-168">nepředstavuje C# `null` nebo [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `nothing` porovnání sémantiku SQL.</span><span class="sxs-lookup"><span data-stu-id="c3347-168"> does not impose C# `null` or [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `nothing` comparison semantics on SQL.</span></span> <span data-ttu-id="c3347-169">Operátory porovnání jsou syntakticky převedeny na jejich ekvivalenty SQL.</span><span class="sxs-lookup"><span data-stu-id="c3347-169">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="c3347-170">Sémantika projeví SQL sémantiku podle definice nastavení serveru nebo připojení.</span><span class="sxs-lookup"><span data-stu-id="c3347-170">The semantics reflect SQL semantics as defined by server or connection settings.</span></span> <span data-ttu-id="c3347-171">Dvě hodnoty null považovány za nerovné pod výchozí nastavení serveru SQL (i když můžete změnit nastavení můžete změnit sémantiky).</span><span class="sxs-lookup"><span data-stu-id="c3347-171">Two null values are considered unequal under default SQL Server settings (although you can change the settings to change the semantics).</span></span> <span data-ttu-id="c3347-172">Bez ohledu na to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nebere v úvahu nastavení serveru v překlad dotazu.</span><span class="sxs-lookup"><span data-stu-id="c3347-172">Regardless, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not consider server settings in query translation.</span></span>  
  
 <span data-ttu-id="c3347-173">Porovnání s literálové `null` (`nothing`) je přeložená na příslušnou verzi SQL (`is null` nebo `is not null`).</span><span class="sxs-lookup"><span data-stu-id="c3347-173">A comparison with the literal `null` (`nothing`) is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>  
  
 <span data-ttu-id="c3347-174">Hodnota `null` (`nothing`) v kolaci je definovaný systémem SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nezmění kolace.</span><span class="sxs-lookup"><span data-stu-id="c3347-174">The value of `null` (`nothing`) in collation is defined by SQL Server; [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not change the collation.</span></span>  
  
### <a name="type-conversion-and-promotion"></a><span data-ttu-id="c3347-175">Převod typů a povýšení</span><span class="sxs-lookup"><span data-stu-id="c3347-175">Type Conversion and Promotion</span></span>  
 <span data-ttu-id="c3347-176">SQL podporuje širokou škálu implicitní převody ve výrazech.</span><span class="sxs-lookup"><span data-stu-id="c3347-176">SQL supports a rich set of implicit conversions in expressions.</span></span> <span data-ttu-id="c3347-177">Podobné výrazy v jazyce C# by vyžadovaly explicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="c3347-177">Similar expressions in C# would require an explicit cast.</span></span> <span data-ttu-id="c3347-178">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c3347-178">For example:</span></span>  
  
-   <span data-ttu-id="c3347-179">`Nvarchar`a `DateTime` typy je možné porovnávat v SQL bez žádné explicitní přetypování; C# vyžaduje explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="c3347-179">`Nvarchar` and `DateTime` types can be compared in SQL without any explicit casts; C# requires explicit conversion.</span></span>  
  
-   <span data-ttu-id="c3347-180">`Decimal`je implicitně převést na `DateTime` v systému SQL.</span><span class="sxs-lookup"><span data-stu-id="c3347-180">`Decimal` is implicitly converted to `DateTime` in SQL.</span></span> <span data-ttu-id="c3347-181">C# neumožňuje pro implicitní převod.</span><span class="sxs-lookup"><span data-stu-id="c3347-181">C# does not allow for an implicit conversion.</span></span>  
  
 <span data-ttu-id="c3347-182">Typ priority v Transact-SQL se podobně liší od priority typu v C# protože základní sadu typů se liší.</span><span class="sxs-lookup"><span data-stu-id="c3347-182">Likewise, type precedence in Transact-SQL differs from type precedence in C# because the underlying set of types is different.</span></span> <span data-ttu-id="c3347-183">Mezi seznamy přednost ve skutečnosti není žádný vztah zrušte podmnožinu nebo nadmnožinou.</span><span class="sxs-lookup"><span data-stu-id="c3347-183">In fact, there is no clear subset/superset relationship between the precedence lists.</span></span> <span data-ttu-id="c3347-184">Například porovnání `nvarchar` s `varchar` způsobí, že implicitní převod `varchar` výraz, který se `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="c3347-184">For example, comparing an `nvarchar` with a `varchar` causes the implicit conversion of the `varchar` expression to `nvarchar`.</span></span> <span data-ttu-id="c3347-185">Modul CLR poskytuje žádná ekvivalentní povýšení.</span><span class="sxs-lookup"><span data-stu-id="c3347-185">The CLR provides no equivalent promotion.</span></span>  
  
 <span data-ttu-id="c3347-186">Tyto rozdíly v jednoduchých případech způsobit CLR výrazy s přetypování být redundantní pro odpovídající výraz SQL.</span><span class="sxs-lookup"><span data-stu-id="c3347-186">In simple cases, these differences cause CLR expressions with casts to be redundant for a corresponding SQL expression.</span></span> <span data-ttu-id="c3347-187">Je důležité, mezilehlých výsledků výrazu SQL může implicitně převést na typ, který nemá přesné protějšek v C#, a naopak.</span><span class="sxs-lookup"><span data-stu-id="c3347-187">More importantly, the intermediate results of a SQL expression might be implicitly promoted to a type that has no accurate counterpart in C#, and vice versa.</span></span> <span data-ttu-id="c3347-188">Celkově platí testování, ladění a ověření těchto výrazů přidá významné zatížení na uživatele.</span><span class="sxs-lookup"><span data-stu-id="c3347-188">Overall, the testing, debugging, and validation of such expressions adds significant burden on the user.</span></span>  
  
### <a name="collation"></a><span data-ttu-id="c3347-189">Kolace</span><span class="sxs-lookup"><span data-stu-id="c3347-189">Collation</span></span>  
 <span data-ttu-id="c3347-190">Příkaz Transact-SQL podporuje explicitní řazení jako poznámky typy řetězec znaků.</span><span class="sxs-lookup"><span data-stu-id="c3347-190">Transact-SQL supports explicit collations as annotations to character string types.</span></span> <span data-ttu-id="c3347-191">Tyto kolace určit platnost určité porovnání.</span><span class="sxs-lookup"><span data-stu-id="c3347-191">These collations determine the validity of certain comparisons.</span></span> <span data-ttu-id="c3347-192">Porovnání dva sloupce s jinou kolací explicitní je například k chybě.</span><span class="sxs-lookup"><span data-stu-id="c3347-192">For example, comparing two columns with different explicit collations is an error.</span></span> <span data-ttu-id="c3347-193">Použití mnohem jednodušší typu řetězec CTS nezpůsobí takové chyby.</span><span class="sxs-lookup"><span data-stu-id="c3347-193">The use of much simplified CTS string type does not cause such errors.</span></span> <span data-ttu-id="c3347-194">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c3347-194">Consider the following example:</span></span>  
  
```  
create table T2 (  
    Col1 nvarchar(10),  
    Col2      nvarchar(10) collate Latin_general_ci_as  
)  
```  
  
 [!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
 [!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]  
  
```  
Select …  
From …  
Where Col1 = Col2  
-- Error, collation conflict.  
```  
  
 <span data-ttu-id="c3347-195">Ve skutečnosti dílčí kolace vytvoří *omezený typ* není nahraditelné.</span><span class="sxs-lookup"><span data-stu-id="c3347-195">In effect, the collation subclause creates a *restricted type* that is not substitutable.</span></span>  
  
 <span data-ttu-id="c3347-196">Pořadí řazení podobně, může být výrazně odlišné mezi systémy typu.</span><span class="sxs-lookup"><span data-stu-id="c3347-196">Similarly, the sort order can be significantly different across the type systems.</span></span> <span data-ttu-id="c3347-197">Tento rozdíl ovlivňuje řazení výsledků.</span><span class="sxs-lookup"><span data-stu-id="c3347-197">This difference affects the sorting of results.</span></span> <span data-ttu-id="c3347-198"><xref:System.Guid>je na všech 16 bajtů seřazené podle lexicographic pořadí (`IComparable()`), zatímco T-SQL porovná identifikátory GUID v následujícím pořadí: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span><span class="sxs-lookup"><span data-stu-id="c3347-198"><xref:System.Guid> is sorted on all 16 bytes by lexicographic order (`IComparable()`), whereas T-SQL compares GUIDs in the following order: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3).</span></span> <span data-ttu-id="c3347-199">Toto uspořádání bylo provedeno v SQL 7.0 při generované NT identifikátory GUID měl takový octet příkaz.</span><span class="sxs-lookup"><span data-stu-id="c3347-199">This ordering was done in SQL 7.0 when NT-generated GUIDs had such an octet order.</span></span> <span data-ttu-id="c3347-200">Přístup zajistit společně pocházejí identifikátory GUID, které jsou generované na stejném uzlu clusteru v postupném pořadí podle časového razítka.</span><span class="sxs-lookup"><span data-stu-id="c3347-200">The approach ensured that GUIDs generated at the same node cluster came together in sequential order according to timestamp.</span></span> <span data-ttu-id="c3347-201">Přístup byl také užitečná pro vytváření indexů (vložení stát připojí místo náhodných IOs).</span><span class="sxs-lookup"><span data-stu-id="c3347-201">The approach was also useful for building indexes (inserts become appends instead of random IOs).</span></span> <span data-ttu-id="c3347-202">Pořadí byl kódována později v systému Windows z důvodu aspekty ochrany osobních údajů, ale SQL musí udržovat kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="c3347-202">The order was scrambled later in Windows because of privacy concerns, but SQL must maintain compatibility.</span></span> <span data-ttu-id="c3347-203">Alternativní řešení je použití <xref:System.Data.SqlTypes.SqlGuid> místo <xref:System.Guid>.</span><span class="sxs-lookup"><span data-stu-id="c3347-203">A workaround is to use <xref:System.Data.SqlTypes.SqlGuid> instead of <xref:System.Guid>.</span></span>  
  
### <a name="operator-and-function-differences"></a><span data-ttu-id="c3347-204">Operátor a rozdíly ve funkcích</span><span class="sxs-lookup"><span data-stu-id="c3347-204">Operator and Function Differences</span></span>  
 <span data-ttu-id="c3347-205">Operátory a funkce, které jsou v podstatě srovnatelné mají podobný sémantiku.</span><span class="sxs-lookup"><span data-stu-id="c3347-205">Operators and functions that are essentially comparable have subtly different semantics.</span></span> <span data-ttu-id="c3347-206">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c3347-206">For example:</span></span>  
  
-   <span data-ttu-id="c3347-207">C# určuje sémantiku krátké okruh založený na lexikální pořadí operandy pro logické operátory `&&` a `||`.</span><span class="sxs-lookup"><span data-stu-id="c3347-207">C# specifies short circuit semantics based on lexical order of operands for logical operators `&&` and `||`.</span></span> <span data-ttu-id="c3347-208">SQL na druhé straně je určená pro dotazy založené na sadě a proto poskytuje dává větší svobodu pro Optimalizátor k rozhodování o pořadí zpracování.</span><span class="sxs-lookup"><span data-stu-id="c3347-208">SQL on the other hand is targeted for set-based queries and therefore provides more freedom for the optimizer to decide the order of execution.</span></span> <span data-ttu-id="c3347-209">Některé důsledky zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="c3347-209">Some of the implications include the following:</span></span>  
  
    -   <span data-ttu-id="c3347-210">Sémanticky ekvivalentní překlad by vyžadovaly "`CASE` ...</span><span class="sxs-lookup"><span data-stu-id="c3347-210">Semantically equivalent translation would require "`CASE` …</span></span> <span data-ttu-id="c3347-211">`WHEN` …</span><span class="sxs-lookup"><span data-stu-id="c3347-211">`WHEN` …</span></span> <span data-ttu-id="c3347-212">`THEN`"vytvořit v systému SQL, aby se zabránilo změny pořadí spouštění operand.</span><span class="sxs-lookup"><span data-stu-id="c3347-212">`THEN`" construct in SQL to avoid reordering of operand execution.</span></span>  
  
    -   <span data-ttu-id="c3347-213">Přijít překlad, aby `AND` / `OR` operátory může způsobit neočekávané chyby, pokud výraz jazyka C# závisí na vyhodnocení Druhý operand založen na výsledek vyhodnocení první operand.</span><span class="sxs-lookup"><span data-stu-id="c3347-213">A loose translation to `AND`/`OR` operators could cause unexpected errors if the C# expression relies on evaluation the second operand being based on the result of the evaluation of the first operand.</span></span>  
  
-   <span data-ttu-id="c3347-214">`Round()`funkce má jinou sémantiku [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] a v T-SQL.</span><span class="sxs-lookup"><span data-stu-id="c3347-214">`Round()` function has different semantics in [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] and in T-SQL.</span></span>  
  
-   <span data-ttu-id="c3347-215">Počáteční index pro řetězce je 0 v modulu CLR ale 1 v systému SQL.</span><span class="sxs-lookup"><span data-stu-id="c3347-215">Starting index for strings is 0 in the CLR but 1 in SQL.</span></span> <span data-ttu-id="c3347-216">Proto všechny funkce, která má index musí překlad index.</span><span class="sxs-lookup"><span data-stu-id="c3347-216">Therefore, any function that has index needs index translation.</span></span>  
  
-   <span data-ttu-id="c3347-217">Modul CLR podporuje operátor numerického zbytku (%) pro čísla s plovoucí desetinnou ale SQL neexistuje.</span><span class="sxs-lookup"><span data-stu-id="c3347-217">The CLR supports modulus (‘%’) operator for floating point numbers but SQL does not.</span></span>  
  
-   <span data-ttu-id="c3347-218">`Like` Operátor efektivně získá automatické přetížení podle implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="c3347-218">The `Like` operator effectively acquires automatic overloads based on implicit conversions.</span></span> <span data-ttu-id="c3347-219">I když `Like` operátor je definována pro provoz na typy řetězec znaků, implicitní převod z číselnými typy nebo `DateTime` typy umožňuje tyto typy jiné než řetězec, který se má použít s `Like` stejně dobře.</span><span class="sxs-lookup"><span data-stu-id="c3347-219">Although the `Like` operator is defined to operate on character string types, implicit conversion from numeric types or `DateTime` types allows for those non-string types to be used with `Like` just as well.</span></span> <span data-ttu-id="c3347-220">V CTS neexistují porovnatelné implicitní převody.</span><span class="sxs-lookup"><span data-stu-id="c3347-220">In CTS, comparable implicit conversions do not exist.</span></span> <span data-ttu-id="c3347-221">Proto je potřeba další přetížení.</span><span class="sxs-lookup"><span data-stu-id="c3347-221">Therefore, additional overloads are needed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3347-222">To `Like` operátor chování platí pouze; pro C# jazyka Visual Basic `Like` – klíčové slovo je beze změny.</span><span class="sxs-lookup"><span data-stu-id="c3347-222">This `Like` operator behavior applies to C# only; the Visual Basic `Like` keyword is unchanged.</span></span>  
  
-   <span data-ttu-id="c3347-223">Přetečení je vždy zaškrtnuto v systému SQL, ale musí být explicitně určena v jazyce C# (ne v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) předejdete wraparound.</span><span class="sxs-lookup"><span data-stu-id="c3347-223">Overflow is always checked in SQL but it has to be explicitly specified in C# (not in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) to avoid wraparound.</span></span> <span data-ttu-id="c3347-224">Zadané číslo sloupce C1, C2 a C3, pokud je C1 + C2 uložen v C3 (C3 nastavte aktualizace T = C1 + C2).</span><span class="sxs-lookup"><span data-stu-id="c3347-224">Given integer columns C1, C2 and C3, if C1+C2 is stored in C3 (Update T Set C3 = C1 + C2).</span></span>  
  
    ```  
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
  
-   <span data-ttu-id="c3347-225">SQL provede symetrický aritmetické operace zaokrouhlení při [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] používá banker je zaokrouhlení.</span><span class="sxs-lookup"><span data-stu-id="c3347-225">SQL performs symmetric arithmetic rounding while [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] uses banker’s rounding.</span></span> <span data-ttu-id="c3347-226">Najdete v článku Knowledge Base 196652 další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="c3347-226">See Knowledgebase article 196652 for additional details.</span></span>  
  
-   <span data-ttu-id="c3347-227">Ve výchozím nastavení pro běžné národní prostředí porovnání řetězců znaků se velká a malá písmena v systému SQL.</span><span class="sxs-lookup"><span data-stu-id="c3347-227">By default, for common locales, character-string comparisons are case-insensitive in SQL.</span></span> <span data-ttu-id="c3347-228">V jazyce Visual Basic a v jazyce C# jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="c3347-228">In Visual Basic and in C#, they are case-sensitive.</span></span> <span data-ttu-id="c3347-229">Například `s == "Food"` (`s = "Food"` v [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) a `s == "Food"` přispět odlišné výsledky, pokud `s` je `food`.</span><span class="sxs-lookup"><span data-stu-id="c3347-229">For example, `s == "Food"` (`s = "Food"` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and `s == "Food"` can yield different results if `s` is `food`.</span></span>  
  
    ```  
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
  
-   <span data-ttu-id="c3347-230">Operátory / funkce u argumenty typu znak pevnou délkou v systému SQL, že výrazně odlišné sémantiku než stejné operátory nebo funkce modulu CLR u <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c3347-230">Operators/ functions applied to fixed length character type arguments in SQL have significantly different semantics than the same operators/functions applied to the CLR <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c3347-231">Může zobrazit také jako rozšíření popsané v části o typech chybějící příslušného problému.</span><span class="sxs-lookup"><span data-stu-id="c3347-231">This could also be viewed as an extension of the missing counterpart problem discussed in the section about types.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="c3347-232">Podobný problém se vyskytuje v zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="c3347-232">A similar problem occurs with string concatenation.</span></span>  
  
    ```  
    create table T6 (  
        Col1      nchar(4)  
        Col2       nchar(4)  
    )  
    Insert into T6 values ('a', 'b');  
    Select Col1+Col2 from T6  
    -- Returns concatenation of padded strings "a   b   " and not "ab".  
    ```  
  
 <span data-ttu-id="c3347-233">Souhrnně convoluted překlad mohou být požadovány pro CLR výrazy a další operátory nebo funkce může být nutné vystavit funkcionalitu SQL.</span><span class="sxs-lookup"><span data-stu-id="c3347-233">In summary, a convoluted translation might be required for CLR expressions and additional operators/functions may be necessary to expose SQL functionality.</span></span>  
  
### <a name="type-casting"></a><span data-ttu-id="c3347-234">Přetypování typu</span><span class="sxs-lookup"><span data-stu-id="c3347-234">Type Casting</span></span>  
 <span data-ttu-id="c3347-235">V jazyce C# a v systému SQL, uživatelé mohou přepsat výchozí sémantika výrazů pomocí explicitního typu přetypování (`Cast` a `Convert`).</span><span class="sxs-lookup"><span data-stu-id="c3347-235">In C# and in SQL, users can override the default semantics of expressions by using explicit type casts (`Cast` and `Convert`).</span></span> <span data-ttu-id="c3347-236">Tato funkce vystavení přes hranice typu systému však představuje dilematem.</span><span class="sxs-lookup"><span data-stu-id="c3347-236">However, exposing this capability across the type system boundary poses a dilemma.</span></span> <span data-ttu-id="c3347-237">Přetypování SQL poskytující požadované sémantiku nelze přeložit snadno odpovídající jazyka C# přetypování.</span><span class="sxs-lookup"><span data-stu-id="c3347-237">A SQL cast that provides the desired semantics cannot be easily translated to a corresponding C# cast.</span></span> <span data-ttu-id="c3347-238">Na druhé straně nejde přetypování C# přeložit přímo na ekvivalentní SQL přetypování z důvodu neshody typu, chybějící svými protějšky a jiný typ přednost hierarchií.</span><span class="sxs-lookup"><span data-stu-id="c3347-238">On the other hand, a C# cast cannot be directly translated into an equivalent SQL cast because of type mismatches, missing counterparts, and different type precedence hierarchies.</span></span> <span data-ttu-id="c3347-239">Je kompromis mezi vystavení Neshoda typu systému a ztrátě významné power výrazu.</span><span class="sxs-lookup"><span data-stu-id="c3347-239">There is a trade-off between exposing the type system mismatch and losing significant power of expression.</span></span>  
  
 <span data-ttu-id="c3347-240">Přetypování typu v ostatních případech nemusí být potřeba v obou doménách pro ověření výrazu ale můžou požadovat, abyste měli jistotu, že je jiné než výchozí mapování správně použít pro výraz.</span><span class="sxs-lookup"><span data-stu-id="c3347-240">In other cases, type casting might not be needed in either domain for validation of an expression but might be required to make sure that a non-default mapping is correctly applied to the expression.</span></span>  
  
```  
-- Example from "Non-default Mapping" section extended  
create table T5 (  
    Col1      nvarchar(10),  
    Col2      nvarchar(10)  
)  
Insert into T5(col1, col2) values (‘3’, ‘2’);  
```  
  
 [!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
 [!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]  
  
```  
Select *  
From T5  
Where Col1 + Col2 > 4     
-- "Col1 + Col2" expr evaluates to '32'   
```  
  
## <a name="performance-issues"></a><span data-ttu-id="c3347-241">Problémy s výkonem</span><span class="sxs-lookup"><span data-stu-id="c3347-241">Performance Issues</span></span>  
 <span data-ttu-id="c3347-242">Monitorování účtů pro některé-modulu CLR SQL serveru rozdíly typu může resut k poklesu výkonu při překračování mezi CLR a SQL Server typu systémy.</span><span class="sxs-lookup"><span data-stu-id="c3347-242">Accounting for some SQL Server-CLR type differences may resut in a decrease in performance when crossing between the CLR and SQL Server type systems.</span></span> <span data-ttu-id="c3347-243">Příklady situací, což ovlivňuje výkon, patří:</span><span class="sxs-lookup"><span data-stu-id="c3347-243">Examples of scenarios impacting performance include the following:</span></span>  
  
-   <span data-ttu-id="c3347-244">Vynutit pořadí vyhodnocení pro logické a operátory</span><span class="sxs-lookup"><span data-stu-id="c3347-244">Forced order of evaluation for logical and/or operators</span></span>  
  
-   <span data-ttu-id="c3347-245">Generování SQL k vynucení pořadí predikátem vyhodnocení omezuje možnost Optimalizátor SQL.</span><span class="sxs-lookup"><span data-stu-id="c3347-245">Generating SQL to enforce order of predicate evaluation restricts the SQL optimizer’s ability.</span></span>  
  
-   <span data-ttu-id="c3347-246">Převody typů zda zavedená kompilátorem CLR nebo objekt relační implementací dotaz, může omezovat použití indexu.</span><span class="sxs-lookup"><span data-stu-id="c3347-246">Type conversions, whether introduced by a CLR compiler or by an Object-Relational query implementation, may curtail index usage.</span></span>  
  
     <span data-ttu-id="c3347-247">Například</span><span class="sxs-lookup"><span data-stu-id="c3347-247">For example,</span></span>  
  
    ```  
    -- Table DDL  
    create table T5 (  
        Col1      varchar(100)  
    )  
    ```  
  
     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]  
  
     <span data-ttu-id="c3347-248">Vezměte v úvahu překlad výrazu `(s = SOME_STRING_CONSTANT)`.</span><span class="sxs-lookup"><span data-stu-id="c3347-248">Consider the translation of expression `(s = SOME_STRING_CONSTANT)`.</span></span>  
  
    ```  
    -- Corresponding part of SQL where clause  
    Where …  
    Col1 = SOME_STRING_CONSTANT  
    -- This expression is of the form <varchar> = <nvarchar>.  
    -- Hence SQL introduces a conversion from varchar to nvarchar,  
    --     resulting in  
    Where …  
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT  
    -- Cannot use the index for column Col1 for some implementations.  
    ```  
  
 <span data-ttu-id="c3347-249">Kromě sémantického rozdílů je důležité vzít v úvahu dopad na výkon při překročení meze mezi SQL serverem a systémy typu CLR.</span><span class="sxs-lookup"><span data-stu-id="c3347-249">In addition to semantic differences, it is important to consider impacts to performance when crossing between the SQL Server and CLR type systems.</span></span> <span data-ttu-id="c3347-250">Pro velké sady dat můžete tyto problémy s výkonem určit, zda je aplikace nasadit.</span><span class="sxs-lookup"><span data-stu-id="c3347-250">For large data sets, such performance issues can determine whether an application is deployable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3347-251">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3347-251">See Also</span></span>  
 [<span data-ttu-id="c3347-252">Základní informace</span><span class="sxs-lookup"><span data-stu-id="c3347-252">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
