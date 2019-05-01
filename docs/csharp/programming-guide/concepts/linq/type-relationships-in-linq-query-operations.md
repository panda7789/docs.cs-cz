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
ms.openlocfilehash: 3b8ae80ff17ea2cf12c3d78c092dd3233ac0751d
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63774015"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="a4140-102">Vztahy typů v operacích dotazu LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="a4140-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="a4140-103">Chcete-li psát dotazy efektivně, je třeba porozumět, jak typy proměnných v dokončeném dotazu operace všechny vzájemně souvisí.</span><span class="sxs-lookup"><span data-stu-id="a4140-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="a4140-104">Když pochopíte tyto vztahy se snadněji pochopit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a příklady kódu v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="a4140-104">If you understand these relationships you will more easily comprehend the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and code examples in the documentation.</span></span> <span data-ttu-id="a4140-105">Kromě toho budete rozumět co děje na pozadí, když jsou proměnné implicitně typované pomocí `var`.</span><span class="sxs-lookup"><span data-stu-id="a4140-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="a4140-106">operace dotazu jsou silně typované ve zdroji dat, v samotném dotazu a ve spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="a4140-106">query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="a4140-107">Typ proměnné dotazů musí být kompatibilní s typem prvků ve zdroji dat a typem iterační proměnné v `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a4140-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="a4140-108">Tvorba silných typů zaručuje, že jsou zachyceny chyby typu v době kompilace, kdy je lze opravit dříve, než se dotknou uživatelů.</span><span class="sxs-lookup"><span data-stu-id="a4140-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="a4140-109">Pro ukázání těchto vztahů typů většina příkladů, které následují, používá explicitní zadání pro všechny proměnné.</span><span class="sxs-lookup"><span data-stu-id="a4140-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="a4140-110">Poslední příklad ukazuje, jak stejné zásady platí i při použití implicitního zápisu pomocí [var](../../../../csharp/language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="a4140-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../../csharp/language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="a4140-111">Dotazy, které Netransformují zdrojová Data</span><span class="sxs-lookup"><span data-stu-id="a4140-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="a4140-112">Následující ilustrace ukazuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] na objekty dotazování operace, která neslouží k transformaci na data.</span><span class="sxs-lookup"><span data-stu-id="a4140-112">The following illustration shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="a4140-113">Zdroj obsahuje posloupnosti řetězců a výstup dotazu je také posloupnost řetězců.</span><span class="sxs-lookup"><span data-stu-id="a4140-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![Diagram znázorňující vztah datových typů v dotazu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="a4140-115">Argument typu zdroje dat určuje typ rozsahu proměnných.</span><span class="sxs-lookup"><span data-stu-id="a4140-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="a4140-116">Určuje typ objektu, který je vybraný typ proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="a4140-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="a4140-117">Tady `name` je řetězec.</span><span class="sxs-lookup"><span data-stu-id="a4140-117">Here `name` is a string.</span></span> <span data-ttu-id="a4140-118">Proto, že je proměnná dotazu `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="a4140-118">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="a4140-119">Proměnná dotazu je procházena `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="a4140-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="a4140-120">Vzhledem k tomu, že je proměnná dotazu sekvencí řetězců, iterační proměnná je také řetězec.</span><span class="sxs-lookup"><span data-stu-id="a4140-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="a4140-121">Dotazy, které transformují zdrojová Data</span><span class="sxs-lookup"><span data-stu-id="a4140-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="a4140-122">Následující ilustrace ukazuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] dotazové operace, který provádí jednoduché transformaci na data.</span><span class="sxs-lookup"><span data-stu-id="a4140-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="a4140-123">Dotaz přebírá řadu `Customer` objektů jako vstup a vybere pouze `Name` vlastnosti ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="a4140-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="a4140-124">Protože `Name` je řetězec, dotaz vyprodukuje sekvenci řetězců jako výstup.</span><span class="sxs-lookup"><span data-stu-id="a4140-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Diagram znázorňující, který transformuje datový typ dotazu.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="a4140-126">Argument typu zdroje dat určuje typ rozsahu proměnných.</span><span class="sxs-lookup"><span data-stu-id="a4140-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="a4140-127">`select` Příkaz vrátí `Name` vlastnosti namísto kompletního `Customer` objektu.</span><span class="sxs-lookup"><span data-stu-id="a4140-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="a4140-128">Protože `Name` je řetězec argument typu `custNameQuery` je `string`, nikoli `Customer`.</span><span class="sxs-lookup"><span data-stu-id="a4140-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="a4140-129">Protože `custNameQuery` je posloupnost řetězců `foreach` iterační proměnná smyčky musí být také `string`.</span><span class="sxs-lookup"><span data-stu-id="a4140-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="a4140-130">Následující obrázek znázorňuje poněkud složitější transformaci.</span><span class="sxs-lookup"><span data-stu-id="a4140-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="a4140-131">`select` Příkaz vrátí anonymní typ, který zachycuje pouze dva členy původního `Customer` objektu.</span><span class="sxs-lookup"><span data-stu-id="a4140-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Diagram znázorňující komplexnější dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="a4140-133">Argument typu zdroje dat je vždy typ rozsahu proměnných v dotazu.</span><span class="sxs-lookup"><span data-stu-id="a4140-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="a4140-134">Vzhledem k tomu, `select` příkaz produkuje anonymní typ, proměnná dotazu musí být implicitně typována pomocí `var`.</span><span class="sxs-lookup"><span data-stu-id="a4140-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="a4140-135">Protože je typ proměnné dotazu implicitní, iterační proměnná ve `foreach` smyčky musí být také implicitní.</span><span class="sxs-lookup"><span data-stu-id="a4140-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="a4140-136">Umožnit kompilátoru odvodit informace o typu</span><span class="sxs-lookup"><span data-stu-id="a4140-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="a4140-137">Přestože byste měli rozumět vztahům typů v operaci dotazu, máte možnost nechat kompilátor, aby udělal všechnu práci za vás.</span><span class="sxs-lookup"><span data-stu-id="a4140-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="a4140-138">Klíčové slovo [var](../../../../csharp/language-reference/keywords/var.md) lze použít pro všechny místní proměnné v rámci operace dotazu.</span><span class="sxs-lookup"><span data-stu-id="a4140-138">The keyword [var](../../../../csharp/language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="a4140-139">Na následujícím obrázku je podobně jako u příkladu 2, který byl popsán výše.</span><span class="sxs-lookup"><span data-stu-id="a4140-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="a4140-140">Kompilátor však dodává silný typ pro každou proměnnou v operaci dotazu.</span><span class="sxs-lookup"><span data-stu-id="a4140-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Diagram znázorňující tok typ s implicitního zápisu.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="a4140-142">Další informace o `var`, naleznete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="a4140-142">For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4140-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4140-143">See also</span></span>

- [<span data-ttu-id="a4140-144">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a4140-144">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
