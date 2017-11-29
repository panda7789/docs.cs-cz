---
title: "Vztahy typů v operacích dotazu LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a088a7f673a9f6aea7a0f50e18746259171bb7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="1431d-102">Vztahy typů v operacích dotazu LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="1431d-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="1431d-103">Zápis dotazů efektivně, byste měli porozumět, jak typy proměnných v rámci dokončení dotazu operace všechny vztahují k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="1431d-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="1431d-104">Pokud budete rozumět tomu tyto vztahy se snadněji pochopit [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ukázky a příklady kódu v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="1431d-104">If you understand these relationships you will more easily comprehend the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and code examples in the documentation.</span></span> <span data-ttu-id="1431d-105">Kromě toho bude pochopit, co se děje na pozadí při proměnné jsou implicitně typované pomocí `var`.</span><span class="sxs-lookup"><span data-stu-id="1431d-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="1431d-106">operace dotazů jsou silného typu ve zdroji dat, v samotném dotazu a při provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="1431d-106"> query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="1431d-107">Typ proměnné v dotazu musí být kompatibilní s typem elementů ve zdroji dat a s typem proměnné iterace ve `foreach` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1431d-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="1431d-108">Tento silného typování zaručuje, že typ chyby jsou zachyceny v době kompilace při jejich lze opravit, než uživatelům stane je.</span><span class="sxs-lookup"><span data-stu-id="1431d-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="1431d-109">K prokázání tyto relace typu, většina příkladů, které následují použijte explicitní zadáte pro všechny proměnné.</span><span class="sxs-lookup"><span data-stu-id="1431d-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="1431d-110">Poslední příklad ukazuje, jak stejné zásady platí, i když použijete implicitní zadáte pomocí [var](../../../../csharp/language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="1431d-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../../csharp/language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="1431d-111">Dotazy, které nebudou transformovat zdrojová Data</span><span class="sxs-lookup"><span data-stu-id="1431d-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="1431d-112">Následující obrázek znázorňuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] na objekty dotazu operace, která provádí data žádná transformace.</span><span class="sxs-lookup"><span data-stu-id="1431d-112">The following illustration shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="1431d-113">Zdroj obsahuje posloupnost řetězce a výstupu dotazu je také pořadí řetězce.</span><span class="sxs-lookup"><span data-stu-id="1431d-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 <span data-ttu-id="1431d-114">![Typy vztah dat v dotazu LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")</span><span class="sxs-lookup"><span data-stu-id="1431d-114">![Relation of data types in a LINQ query](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")</span></span>  
  
1.  <span data-ttu-id="1431d-115">Argument typu zdroje dat určuje typ proměnné rozsahu.</span><span class="sxs-lookup"><span data-stu-id="1431d-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2.  <span data-ttu-id="1431d-116">Typ objektu, který je vybraný Určuje typ proměnné v dotazu.</span><span class="sxs-lookup"><span data-stu-id="1431d-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="1431d-117">Zde `name` je řetězec.</span><span class="sxs-lookup"><span data-stu-id="1431d-117">Here `name` is a string.</span></span> <span data-ttu-id="1431d-118">Proměnné dotazu je proto `IEnumerable` \<řetězec >.</span><span class="sxs-lookup"><span data-stu-id="1431d-118">Therefore, the query variable is an `IEnumerable`\<string>.</span></span>  
  
3.  <span data-ttu-id="1431d-119">Proměnné dotazu je vstupní přes `foreach` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1431d-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="1431d-120">Proměnné dotazu je posloupnost řetězce, a proto je řetězec také proměnné iterace.</span><span class="sxs-lookup"><span data-stu-id="1431d-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="1431d-121">Dotazy, které transformace zdrojová Data</span><span class="sxs-lookup"><span data-stu-id="1431d-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="1431d-122">Následující obrázek znázorňuje [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operace, která provádí jednoduché transformaci dat dotazů.</span><span class="sxs-lookup"><span data-stu-id="1431d-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="1431d-123">Dotaz trvá posloupnost `Customer` objekty jako vstup a vybere pouze `Name` vlastnost ve výsledku.</span><span class="sxs-lookup"><span data-stu-id="1431d-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="1431d-124">Protože `Name` je řetězec dotazu vytváří a pořadí řetězce jako výstup.</span><span class="sxs-lookup"><span data-stu-id="1431d-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 <span data-ttu-id="1431d-125">![Dotaz, který transformuje datový typ](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")</span><span class="sxs-lookup"><span data-stu-id="1431d-125">![A query that transforms the data type](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")</span></span>  
  
1.  <span data-ttu-id="1431d-126">Argument typu zdroje dat určuje typ proměnné rozsahu.</span><span class="sxs-lookup"><span data-stu-id="1431d-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2.  <span data-ttu-id="1431d-127">`select` Příkaz vrátí `Name` vlastnost místo kompletní `Customer` objektu.</span><span class="sxs-lookup"><span data-stu-id="1431d-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="1431d-128">Protože `Name` je řetězec, typ argument `custNameQuery` je `string`, nikoli `Customer`.</span><span class="sxs-lookup"><span data-stu-id="1431d-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3.  <span data-ttu-id="1431d-129">Protože `custNameQuery` je posloupnost řetězce, `foreach` musí být také proměnné iterace smyčky `string`.</span><span class="sxs-lookup"><span data-stu-id="1431d-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="1431d-130">Následující obrázek znázorňuje trochu složitější transformace.</span><span class="sxs-lookup"><span data-stu-id="1431d-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="1431d-131">`select` Příkaz vrací anonymní typ, který zachycuje právě dva členy původního `Customer` objektu.</span><span class="sxs-lookup"><span data-stu-id="1431d-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 <span data-ttu-id="1431d-132">![Dotaz, který transformuje datový typ](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")</span><span class="sxs-lookup"><span data-stu-id="1431d-132">![A query that transforms the data type](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")</span></span>  
  
1.  <span data-ttu-id="1431d-133">Argument typu zdroje dat je vždy typ proměnné rozsahu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="1431d-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2.  <span data-ttu-id="1431d-134">Protože `select` příkaz vytvořil anonymní typ, proměnné dotazu musí být implicitně typované pomocí `var`.</span><span class="sxs-lookup"><span data-stu-id="1431d-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3.  <span data-ttu-id="1431d-135">Typ proměnné v dotazu je implicitní, proměnné iterace ve `foreach` smyčky, musí být také implicitní.</span><span class="sxs-lookup"><span data-stu-id="1431d-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="1431d-136">Upozornění kompilátoru odvození informací o typu</span><span class="sxs-lookup"><span data-stu-id="1431d-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="1431d-137">I když byste měli porozumět vztahy typů v operaci dotazu, máte možnost povolit, aby kompilátoru to pro vás všechnu práci.</span><span class="sxs-lookup"><span data-stu-id="1431d-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="1431d-138">Klíčové slovo [var](../../../../csharp/language-reference/keywords/var.md) lze použít pro všechny místní proměnné v operaci dotazu.</span><span class="sxs-lookup"><span data-stu-id="1431d-138">The keyword [var](../../../../csharp/language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="1431d-139">Na následujícím obrázku je podobný příklad číslem 2, který byl dříve popsané.</span><span class="sxs-lookup"><span data-stu-id="1431d-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="1431d-140">Kompilátor však poskytuje silného typu pro každou proměnnou v operaci dotazu.</span><span class="sxs-lookup"><span data-stu-id="1431d-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 <span data-ttu-id="1431d-141">![Zadejte toku s implicitní zadáním](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")</span><span class="sxs-lookup"><span data-stu-id="1431d-141">![Type flow with implicit typing](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")</span></span>  
  
 <span data-ttu-id="1431d-142">Další informace o `var`, najdete v části [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="1431d-142">For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1431d-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="1431d-143">See Also</span></span>  
 [<span data-ttu-id="1431d-144">Začínáme s dotazy LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="1431d-144">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
