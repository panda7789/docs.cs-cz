---
title: Vztahy typů v operacích dotazu LINQ (C#)
description: Přečtěte si, jak typy proměnných v dotazu LINQ vzájemně souvisí. Operace dotazů LINQ jsou silně typované ve zdroji dat, v dotazu a v provádění.
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
ms.openlocfilehash: 20f0b37a156e3b3f9c63f14cb83d678d26f685ee
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302279"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="34778-104">Vztahy typů v operacích dotazu LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="34778-104">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="34778-105">Chcete-li efektivně zapisovat dotazy, měli byste pochopit, jak typy proměnných v úplné operaci dotazu vzájemně souvisí.</span><span class="sxs-lookup"><span data-stu-id="34778-105">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="34778-106">Pokud rozumíte těmto vztahům, budete snadněji pochopit ukázky LINQ a příklady kódu v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="34778-106">If you understand these relationships you will more easily comprehend the LINQ samples and code examples in the documentation.</span></span> <span data-ttu-id="34778-107">Kromě toho můžete pochopit, co se stane na pozadí, pokud jsou proměnné implicitně typované pomocí `var` .</span><span class="sxs-lookup"><span data-stu-id="34778-107">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 <span data-ttu-id="34778-108">Operace dotazů LINQ jsou silně typované ve zdroji dat, v samotném dotazu a v provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="34778-108">LINQ query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="34778-109">Typ proměnných v dotazu musí být kompatibilní s typem prvků ve zdroji dat a typem proměnné iterace v `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="34778-109">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="34778-110">Toto silné zadání zaručuje, že při kompilaci jsou zachyceny chyby typu, pokud je lze opravit předtím, než se uživatelé dostanou.</span><span class="sxs-lookup"><span data-stu-id="34778-110">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="34778-111">Aby bylo možné předvést tyto vztahy typů, většina příkladů, které následují, používá explicitní psaní pro všechny proměnné.</span><span class="sxs-lookup"><span data-stu-id="34778-111">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="34778-112">Poslední příklad ukazuje, jak se stejné zásady použijí, i když použijete implicitní zadání pomocí [var](../../../language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="34778-112">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="34778-113">Dotazy, které netransformují zdrojová data</span><span class="sxs-lookup"><span data-stu-id="34778-113">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="34778-114">Následující ilustrace znázorňuje LINQ to Objects operaci dotazování, která neprovede žádné transformace dat.</span><span class="sxs-lookup"><span data-stu-id="34778-114">The following illustration shows a LINQ to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="34778-115">Zdroj obsahuje posloupnost řetězců a výstup dotazu je také posloupnost řetězců.</span><span class="sxs-lookup"><span data-stu-id="34778-115">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![Diagram, který zobrazuje vztah datových typů v dotazu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="34778-117">Argument typu zdroje dat určuje typ proměnné rozsahu.</span><span class="sxs-lookup"><span data-stu-id="34778-117">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="34778-118">Typ objektu, který je vybrán, určuje typ proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="34778-118">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="34778-119">Zde `name` je řetězec.</span><span class="sxs-lookup"><span data-stu-id="34778-119">Here `name` is a string.</span></span> <span data-ttu-id="34778-120">Proto proměnná dotazu je `IEnumerable<string>` .</span><span class="sxs-lookup"><span data-stu-id="34778-120">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="34778-121">Proměnná dotazu se opakuje v `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="34778-121">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="34778-122">Vzhledem k tomu, že je proměnná dotazu posloupností řetězců, je proměnná iterace také řetězcem.</span><span class="sxs-lookup"><span data-stu-id="34778-122">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="34778-123">Dotazy, které transformují zdrojová data</span><span class="sxs-lookup"><span data-stu-id="34778-123">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="34778-124">Následující ilustrace znázorňuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operaci dotazu, která provádí jednoduchou transformaci dat.</span><span class="sxs-lookup"><span data-stu-id="34778-124">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="34778-125">Dotaz provede jako vstup sekvenci `Customer` objektů a `Name` ve výsledku vybere pouze vlastnost.</span><span class="sxs-lookup"><span data-stu-id="34778-125">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="34778-126">Vzhledem k tomu `Name` , že je řetězec, dotaz vytváří sekvenci řetězců jako výstup.</span><span class="sxs-lookup"><span data-stu-id="34778-126">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Diagram znázorňující dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="34778-128">Argument typu zdroje dat určuje typ proměnné rozsahu.</span><span class="sxs-lookup"><span data-stu-id="34778-128">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="34778-129">`select`Příkaz vrátí `Name` vlastnost namísto celého `Customer` objektu.</span><span class="sxs-lookup"><span data-stu-id="34778-129">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="34778-130">Protože `Name` je řetězec, argument typu `custNameQuery` je `string` , not `Customer` .</span><span class="sxs-lookup"><span data-stu-id="34778-130">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="34778-131">Vzhledem k tomu `custNameQuery` , že je sekvence řetězců, `foreach` iterační proměnná smyčky musí být také `string` .</span><span class="sxs-lookup"><span data-stu-id="34778-131">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="34778-132">Následující ilustrace znázorňuje mírně složitější transformaci.</span><span class="sxs-lookup"><span data-stu-id="34778-132">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="34778-133">`select`Příkaz vrátí anonymní typ, který zachycuje pouze dva členy původního `Customer` objektu.</span><span class="sxs-lookup"><span data-stu-id="34778-133">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Diagram znázorňující složitější dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="34778-135">Argument typu zdroje dat je vždy typ proměnné rozsahu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="34778-135">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="34778-136">Vzhledem k tomu `select` , že příkaz vytvoří anonymní typ, proměnná dotazu musí být implicitně zadána pomocí `var` .</span><span class="sxs-lookup"><span data-stu-id="34778-136">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="34778-137">Vzhledem k tomu, že typ proměnné dotazu je implicitní, musí být proměnná iterace ve `foreach` smyčce také implicitní.</span><span class="sxs-lookup"><span data-stu-id="34778-137">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="34778-138">Umožnění odvození informací o typu kompilátoru</span><span class="sxs-lookup"><span data-stu-id="34778-138">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="34778-139">I když byste měli pochopit vztahy typů v operaci dotazu, máte možnost nechat kompilátor provádět veškerou práci za vás.</span><span class="sxs-lookup"><span data-stu-id="34778-139">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="34778-140">Klíčové slovo [var](../../../language-reference/keywords/var.md) lze použít pro libovolnou místní proměnnou v operaci dotazu.</span><span class="sxs-lookup"><span data-stu-id="34778-140">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="34778-141">Následující obrázek je podobný ukázkovému číslu 2, které bylo popsáno dříve.</span><span class="sxs-lookup"><span data-stu-id="34778-141">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="34778-142">Nicméně kompilátor poskytuje silný typ pro každou proměnnou v operaci dotazu.</span><span class="sxs-lookup"><span data-stu-id="34778-142">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Diagram, který zobrazuje tok typu s implicitním zadáním.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="34778-144">Další informace o naleznete `var` v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="34778-144">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
