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
ms.openlocfilehash: 42519a74be1bd6934bc7a3304d154321697d128c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591017"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="85d8e-102">Vztahy typů v operacích dotazu LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="85d8e-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="85d8e-103">Chcete-li efektivně zapisovat dotazy, měli byste pochopit, jak typy proměnných v úplné operaci dotazu vzájemně souvisí.</span><span class="sxs-lookup"><span data-stu-id="85d8e-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="85d8e-104">Pokud rozumíte těmto vztahům, budete snadněji pochopit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a příklady kódu v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="85d8e-104">If you understand these relationships you will more easily comprehend the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and code examples in the documentation.</span></span> <span data-ttu-id="85d8e-105">Kromě toho můžete pochopit, co se stane na pozadí, pokud jsou proměnné implicitně typované pomocí `var`.</span><span class="sxs-lookup"><span data-stu-id="85d8e-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="85d8e-106">operace dotazů jsou silně typované ve zdroji dat, v samotném dotazu a v provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="85d8e-106">query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="85d8e-107">Typ proměnných v dotazu musí být kompatibilní s typem prvků ve zdroji dat a typem proměnné iterace v `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="85d8e-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="85d8e-108">Toto silné zadání zaručuje, že při kompilaci jsou zachyceny chyby typu, pokud je lze opravit předtím, než se uživatelé dostanou.</span><span class="sxs-lookup"><span data-stu-id="85d8e-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="85d8e-109">Aby bylo možné předvést tyto vztahy typů, většina příkladů, které následují, používá explicitní psaní pro všechny proměnné.</span><span class="sxs-lookup"><span data-stu-id="85d8e-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="85d8e-110">Poslední příklad ukazuje, jak se stejné zásady použijí, i když použijete implicitní zadání pomocí [var](../../../language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="85d8e-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="85d8e-111">Dotazy, které netransformují zdrojová data</span><span class="sxs-lookup"><span data-stu-id="85d8e-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="85d8e-112">Následující ilustrace znázorňuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operaci dotazování na objekty, která neprovede žádné transformace dat.</span><span class="sxs-lookup"><span data-stu-id="85d8e-112">The following illustration shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="85d8e-113">Zdroj obsahuje posloupnost řetězců a výstup dotazu je také posloupnost řetězců.</span><span class="sxs-lookup"><span data-stu-id="85d8e-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![Diagram, který zobrazuje vztah datových typů v dotazu LINQ.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="85d8e-115">Argument typu zdroje dat určuje typ proměnné rozsahu.</span><span class="sxs-lookup"><span data-stu-id="85d8e-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="85d8e-116">Typ objektu, který je vybrán, určuje typ proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="85d8e-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="85d8e-117">Zde `name` je řetězec.</span><span class="sxs-lookup"><span data-stu-id="85d8e-117">Here `name` is a string.</span></span> <span data-ttu-id="85d8e-118">Proto proměnná dotazu je `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="85d8e-118">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="85d8e-119">Proměnná dotazu se opakuje v `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="85d8e-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="85d8e-120">Vzhledem k tomu, že je proměnná dotazu posloupností řetězců, je proměnná iterace také řetězcem.</span><span class="sxs-lookup"><span data-stu-id="85d8e-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="85d8e-121">Dotazy, které transformují zdrojová data</span><span class="sxs-lookup"><span data-stu-id="85d8e-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="85d8e-122">Následující ilustrace znázorňuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operaci dotazu, která provádí jednoduchou transformaci dat.</span><span class="sxs-lookup"><span data-stu-id="85d8e-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="85d8e-123">Dotaz provede jako vstup sekvenci `Customer` objektů a ve výsledku vybere `Name` pouze vlastnost.</span><span class="sxs-lookup"><span data-stu-id="85d8e-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="85d8e-124">Vzhledem `Name` k tomu, že je řetězec, dotaz vytváří sekvenci řetězců jako výstup.</span><span class="sxs-lookup"><span data-stu-id="85d8e-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Diagram znázorňující dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="85d8e-126">Argument typu zdroje dat určuje typ proměnné rozsahu.</span><span class="sxs-lookup"><span data-stu-id="85d8e-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="85d8e-127">Příkaz vrátí vlastnost namísto celého `Customer`objektu. `Name` `select`</span><span class="sxs-lookup"><span data-stu-id="85d8e-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="85d8e-128">Protože `Name` je řetězec, `custNameQuery` argument typu je `string`, not `Customer`.</span><span class="sxs-lookup"><span data-stu-id="85d8e-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="85d8e-129">Vzhledem `custNameQuery` k tomu `foreach` , že je sekvence řetězců, iterační `string`proměnná smyčky musí být také.</span><span class="sxs-lookup"><span data-stu-id="85d8e-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="85d8e-130">Následující ilustrace znázorňuje mírně složitější transformaci.</span><span class="sxs-lookup"><span data-stu-id="85d8e-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="85d8e-131">Příkaz vrátí anonymní typ, který zachycuje pouze dva členy původního `Customer` objektu. `select`</span><span class="sxs-lookup"><span data-stu-id="85d8e-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Diagram znázorňující složitější dotaz, který transformuje datový typ.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="85d8e-133">Argument typu zdroje dat je vždy typ proměnné rozsahu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="85d8e-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="85d8e-134">Vzhledem k tomu, že `var` příkazvytvoříanonymnítyp,proměnnádotazumusíbýtimplicitnězadánapomocí.`select`</span><span class="sxs-lookup"><span data-stu-id="85d8e-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="85d8e-135">Vzhledem k tomu, že typ proměnné dotazu je implicitní, musí být proměnná iterace ve `foreach` smyčce také implicitní.</span><span class="sxs-lookup"><span data-stu-id="85d8e-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="85d8e-136">Umožnění odvození informací o typu kompilátoru</span><span class="sxs-lookup"><span data-stu-id="85d8e-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="85d8e-137">I když byste měli pochopit vztahy typů v operaci dotazu, máte možnost nechat kompilátor provádět veškerou práci za vás.</span><span class="sxs-lookup"><span data-stu-id="85d8e-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="85d8e-138">Klíčové slovo [var](../../../language-reference/keywords/var.md) lze použít pro libovolnou místní proměnnou v operaci dotazu.</span><span class="sxs-lookup"><span data-stu-id="85d8e-138">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="85d8e-139">Následující obrázek je podobný ukázkovému číslu 2, které bylo popsáno dříve.</span><span class="sxs-lookup"><span data-stu-id="85d8e-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="85d8e-140">Nicméně kompilátor poskytuje silný typ pro každou proměnnou v operaci dotazu.</span><span class="sxs-lookup"><span data-stu-id="85d8e-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Diagram, který zobrazuje tok typu s implicitním zadáním.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="85d8e-142">Další informace o `var`naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="85d8e-142">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
