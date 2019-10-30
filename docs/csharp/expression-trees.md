---
title: Stromy výrazů
description: Přečtěte si o stromech výrazů v .NET Core a jejich použití k reprezentaci kódu jako struktur, které můžete prozkoumávat, upravovat a spouštět.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: b7d039ea4585953473dc88cebcc516ea240cdc3a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036326"
---
# <a name="expression-trees"></a><span data-ttu-id="33df1-103">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="33df1-103">Expression Trees</span></span>

<span data-ttu-id="33df1-104">Pokud jste použili LINQ, máte zkušenosti s bohatou knihovnou, kde `Func` typy jsou součástí sady rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="33df1-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="33df1-105">(Pokud nejste obeznámeni s LINQ, pravděpodobně budete chtít přečíst [kurz LINQ](linq/index.md) a článek o [výrazech lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) před tímto.) *Stromy výrazů* poskytují bohatou interakci s argumenty, které jsou funkcemi.</span><span class="sxs-lookup"><span data-stu-id="33df1-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="33df1-106">Při vytváření dotazů LINQ píšete argumenty funkce, obvykle pomocí výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="33df1-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="33df1-107">V typických dotazech LINQ jsou tyto argumenty funkce transformovány na delegáta, který kompilátor vytvoří.</span><span class="sxs-lookup"><span data-stu-id="33df1-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="33df1-108">Pokud chcete mít rozsáhlejší interakci, je nutné použít *stromy výrazů*.</span><span class="sxs-lookup"><span data-stu-id="33df1-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="33df1-109">Stromy výrazů reprezentují kód jako strukturu, kterou můžete prostudovat, upravit nebo spustit.</span><span class="sxs-lookup"><span data-stu-id="33df1-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="33df1-110">Tyto nástroje umožňují pracovat s kódem během běhu.</span><span class="sxs-lookup"><span data-stu-id="33df1-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="33df1-111">Můžete napsat kód, který prověřuje spuštěné algoritmy nebo vloží nové funkce.</span><span class="sxs-lookup"><span data-stu-id="33df1-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="33df1-112">V pokročilejších scénářích můžete upravovat spuštěné algoritmy a dokonce i překládat C# výrazy do jiné formy pro provádění v jiném prostředí.</span><span class="sxs-lookup"><span data-stu-id="33df1-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="33df1-113">Pravděpodobně jste již napsali kód, který používá stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="33df1-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="33df1-114">Rozhraní API LINQ Entity Framework akceptují stromy výrazů jako argumenty pro vzor výrazu dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="33df1-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="33df1-115">Umožňuje [Entity Framework](/ef/) přeložit dotaz, který jste napsali, C# do jazyka SQL, který se spouští v databázovém stroji.</span><span class="sxs-lookup"><span data-stu-id="33df1-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="33df1-116">Dalším příkladem je [MOQ](https://github.com/Moq/moq), což je oblíbená rozhraní pro návrhy rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="33df1-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="33df1-117">Zbývající části tohoto kurzu budou zkoumat, jaké stromy výrazů jsou, prozkoumat třídy architektury, které podporují stromy výrazů, a Ukázat, jak pracovat se stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="33df1-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="33df1-118">Naučíte se, jak číst stromy výrazů, jak vytvářet stromy výrazů, jak vytvářet stromy upravených výrazů a jak spustit kód reprezentovaný stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="33df1-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="33df1-119">Po přečtení budete připraveni tyto struktury použít k vytváření bohatých adaptivních algoritmů.</span><span class="sxs-lookup"><span data-stu-id="33df1-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="33df1-120">Vysvětlení stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="33df1-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="33df1-121">Pochopení struktury a konceptů za *stromy výrazů*.</span><span class="sxs-lookup"><span data-stu-id="33df1-121">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="33df1-122">Typy architektur podporující stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="33df1-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="33df1-123">Přečtěte si o strukturách a třídách, které definují a manipulují s stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="33df1-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="33df1-124">Provádění výrazů</span><span class="sxs-lookup"><span data-stu-id="33df1-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="33df1-125">Přečtěte si, jak převést strom výrazu reprezentovaný jako výraz lambda do delegáta a provést výsledný delegát.</span><span class="sxs-lookup"><span data-stu-id="33df1-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="33df1-126">Interpretace výrazů</span><span class="sxs-lookup"><span data-stu-id="33df1-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="33df1-127">Naučte se procházet a prozkoumávat *stromy výrazů* , abyste pochopili, jaký kód strom výrazu představuje.</span><span class="sxs-lookup"><span data-stu-id="33df1-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="33df1-128">Vytváření výrazů</span><span class="sxs-lookup"><span data-stu-id="33df1-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="33df1-129">Naučte se vytvářet uzly pro strom výrazů a stromy výrazů sestavení.</span><span class="sxs-lookup"><span data-stu-id="33df1-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="33df1-130">Překlad výrazů</span><span class="sxs-lookup"><span data-stu-id="33df1-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="33df1-131">Naučte se, jak vytvořit upravenou kopii stromu výrazů nebo jak přeložit strom výrazu do jiného formátu.</span><span class="sxs-lookup"><span data-stu-id="33df1-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="33df1-132">Sčítání</span><span class="sxs-lookup"><span data-stu-id="33df1-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="33df1-133">Projděte si informace o stromech výrazů.</span><span class="sxs-lookup"><span data-stu-id="33df1-133">Review the information on expression trees.</span></span>
