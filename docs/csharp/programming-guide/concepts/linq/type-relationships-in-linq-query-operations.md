---
title: Vztahy typů v operacích dotazu LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 41853e6858fae9e8d449aeed95a6a84f343d5874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635610"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="827b2-102">Vztahy typů v operacích dotazu LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="827b2-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="827b2-103">Chcete-li psát dotazy efektivně, měli byste pochopit, jak typy proměnných v operaci úplnédotaz všechny vzájemně souvisejí.</span><span class="sxs-lookup"><span data-stu-id="827b2-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="827b2-104">Pokud rozumíte těmto vztahům, budete snadněji pochopit linq ukázky a příklady kódu v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="827b2-104">If you understand these relationships you will more easily comprehend the LINQ samples and code examples in the documentation.</span></span> <span data-ttu-id="827b2-105">Kromě toho pochopíte, co se děje na pozadí, když proměnné `var`implicitně zadali pomocí .</span><span class="sxs-lookup"><span data-stu-id="827b2-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 <span data-ttu-id="827b2-106">Linq operace dotazu jsou silně zadali ve zdroji dat, v samotném dotazu a v provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="827b2-106">LINQ query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="827b2-107">Typ proměnných v dotazu musí být kompatibilní s typem prvků ve zdroji dat a s `foreach` typem iterace proměnné v příkazu.</span><span class="sxs-lookup"><span data-stu-id="827b2-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="827b2-108">Toto silné psaní zaručuje, že chyby typu jsou zachyceny v době kompilace, kdy je lze opravit dříve, než se s nimi uživatelé setkají.</span><span class="sxs-lookup"><span data-stu-id="827b2-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="827b2-109">Chcete-li demonstrovat tyto vztahy typu, většina příkladů, které následují použít explicitní psaní pro všechny proměnné.</span><span class="sxs-lookup"><span data-stu-id="827b2-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="827b2-110">Poslední příklad ukazuje, jak platí stejné zásady i v případě, že používáte implicitní psaní pomocí [var](../../../language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="827b2-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="827b2-111">Dotazy, které netransformují zdrojová data</span><span class="sxs-lookup"><span data-stu-id="827b2-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="827b2-112">Následující obrázek znázorňuje operaci dotazu LINQ to Objects, která neprovádí žádné transformace na data.</span><span class="sxs-lookup"><span data-stu-id="827b2-112">The following illustration shows a LINQ to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="827b2-113">Zdroj obsahuje posloupnost řetězců a výstup dotazu je také posloupnost řetězců.</span><span class="sxs-lookup"><span data-stu-id="827b2-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![Diagram, který zobrazuje vztah datových typů v dotazu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="827b2-115">Typ argumentu zdroje dat určuje typ proměnné rozsahu.</span><span class="sxs-lookup"><span data-stu-id="827b2-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="827b2-116">Typ vybraného objektu určuje typ proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="827b2-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="827b2-117">Tady `name` je provázek.</span><span class="sxs-lookup"><span data-stu-id="827b2-117">Here `name` is a string.</span></span> <span data-ttu-id="827b2-118">Proměnná dotazu je `IEnumerable<string>`proto .</span><span class="sxs-lookup"><span data-stu-id="827b2-118">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="827b2-119">Proměnná dotazu je v `foreach` příkazu iterována.</span><span class="sxs-lookup"><span data-stu-id="827b2-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="827b2-120">Vzhledem k tomu, že proměnná dotazu je posloupnost řetězců, itidati proměnná je také řetězec.</span><span class="sxs-lookup"><span data-stu-id="827b2-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="827b2-121">Dotazy, které transformují zdrojová data</span><span class="sxs-lookup"><span data-stu-id="827b2-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="827b2-122">Následující obrázek [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] znázorňuje operaci dotazu, která provádí jednoduchou transformaci dat.</span><span class="sxs-lookup"><span data-stu-id="827b2-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="827b2-123">Dotaz přebírá posloupnost `Customer` objektů jako vstup a `Name` vybere pouze vlastnost ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="827b2-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="827b2-124">Protože `Name` je řetězec, dotaz vytvoří posloupnost řetězců jako výstup.</span><span class="sxs-lookup"><span data-stu-id="827b2-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Diagram znázorňující dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="827b2-126">Typ argumentu zdroje dat určuje typ proměnné rozsahu.</span><span class="sxs-lookup"><span data-stu-id="827b2-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="827b2-127">Příkaz `select` vrátí `Name` vlastnost namísto `Customer` úplného objektu.</span><span class="sxs-lookup"><span data-stu-id="827b2-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="827b2-128">Protože `Name` je řetězec, argument `custNameQuery` typu `string`je `Customer`, není .</span><span class="sxs-lookup"><span data-stu-id="827b2-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="827b2-129">Protože `custNameQuery` je posloupnost řetězců, iterace `foreach` smyčky proměnné `string`musí být také .</span><span class="sxs-lookup"><span data-stu-id="827b2-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="827b2-130">Následující obrázek znázorňuje o něco složitější transformaci.</span><span class="sxs-lookup"><span data-stu-id="827b2-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="827b2-131">Příkaz `select` vrátí anonymní typ, který zachycuje pouze `Customer` dva členy původního objektu.</span><span class="sxs-lookup"><span data-stu-id="827b2-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Diagram znázorňující složitější dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="827b2-133">Argument typu zdroje dat je vždy typem proměnné rozsahu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="827b2-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="827b2-134">Vzhledem `select` k tomu, že příkaz vytváří anonymní typ, musí `var`být proměnná dotazu implicitně zadána pomocí .</span><span class="sxs-lookup"><span data-stu-id="827b2-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="827b2-135">Vzhledem k tomu, že typ proměnné dotazu je implicitní, musí být implicitní také iterace proměnné ve `foreach` smyčce.</span><span class="sxs-lookup"><span data-stu-id="827b2-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="827b2-136">Možnost, aby kompilátor odvodil informace o typu</span><span class="sxs-lookup"><span data-stu-id="827b2-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="827b2-137">I když byste měli pochopit vztahy typu v operaci dotazu, máte možnost nechat kompilátor uděláte veškerou práci za vás.</span><span class="sxs-lookup"><span data-stu-id="827b2-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="827b2-138">Klíčové slovo [var](../../../language-reference/keywords/var.md) lze použít pro libovolnou místní proměnnou v operaci dotazu.</span><span class="sxs-lookup"><span data-stu-id="827b2-138">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="827b2-139">Následující obrázek je podobný příkladčíslo 2, který byl popsán dříve.</span><span class="sxs-lookup"><span data-stu-id="827b2-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="827b2-140">Kompilátor však poskytuje silný typ pro každou proměnnou v operaci dotazu.</span><span class="sxs-lookup"><span data-stu-id="827b2-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Diagram, který zobrazuje tok typu s implicitním psaním.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="827b2-142">Další informace `var`o [souborech naleznete v tématu Implicitně zadané místní proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="827b2-142">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
