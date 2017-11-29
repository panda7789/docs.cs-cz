---
title: "Stromy výrazů"
description: "Další informace o stromů výrazů v .NET Core a jakým způsobem je použít k reprezentování kód jako struktury, které můžete prozkoumat, upravit a spustit."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: 3935906d9fca81a094999eefdd49ae4ed56990bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="expression-trees"></a><span data-ttu-id="3e50c-104">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="3e50c-104">Expression Trees</span></span>

<span data-ttu-id="3e50c-105">Pokud jste použili LINQ, máte zkušenosti s bohatou knihovny kde `Func` typy jsou součástí sada rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3e50c-105">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="3e50c-106">(Pokud nejste obeznámeni s dotazy LINQ, budete ho zřejmě chtít číst [kurzu LINQ](linq/index.md) a kurz týkající se [výrazy lambda](lambda-expressions.md) před tímto.) *Stromy výrazů* poskytovat lepší integrace s argumenty, které jsou funkce.</span><span class="sxs-lookup"><span data-stu-id="3e50c-106">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the tutorial on [lambda expressions](lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="3e50c-107">Psaní argumenty funkce, obvykle pomocí výrazů Lambda, při vytváření dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="3e50c-107">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="3e50c-108">V typické dotazu LINQ se tyto argumenty funkce převede na delegáta, který vytvoří kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="3e50c-108">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="3e50c-109">Pokud chcete mít lepší integrace, budete muset použít *stromů výrazů*.</span><span class="sxs-lookup"><span data-stu-id="3e50c-109">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="3e50c-110">Stromy výrazů představují kód jako strukturu, která můžete prozkoumat, upravit nebo provést.</span><span class="sxs-lookup"><span data-stu-id="3e50c-110">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="3e50c-111">Tyto nástroje vám power k manipulaci s kód za běhu.</span><span class="sxs-lookup"><span data-stu-id="3e50c-111">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="3e50c-112">Můžete napsat kód, který hledá spuštěné algoritmy nebo vloží nové funkce.</span><span class="sxs-lookup"><span data-stu-id="3e50c-112">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="3e50c-113">V pokročilejších scénářích můžete upravit, s algoritmy a i převede výrazy jazyka C# do jiného formátu pro spuštění v jiném prostředí.</span><span class="sxs-lookup"><span data-stu-id="3e50c-113">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="3e50c-114">Pravděpodobně jste již zapsány kód, který používá stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3e50c-114">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="3e50c-115">Rozhraní Entity Framework LINQ API přijmout stromů výrazů jako argumenty pro vzor výrazu dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="3e50c-115">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="3e50c-116">Umožňující [Entity Framework](http://docs.efproject.net/en/latest/) přeložit dotaz jste napsali v jazyce C# do SQL, který se spustí v databázovém stroji.</span><span class="sxs-lookup"><span data-stu-id="3e50c-116">That enables [Entity Framework](http://docs.efproject.net/en/latest/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="3e50c-117">Dalším příkladem je [Moq](https://github.com/Moq/moq), což je Oblíbené mocking rozhraní pro rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3e50c-117">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="3e50c-118">Zbývající části tohoto kurzu bude prozkoumejte, jaké jsou stromů výrazů, zkontrolujte framework třídy, které podporují stromů výrazů a ukazují, jak pracovat s stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3e50c-118">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="3e50c-119">Dozvíte se, jak číst stromů výrazů, vytváření stromů výrazů, jak vytvořit stromů výrazů upravené a jak ke spouštění kódu vytvořeného reprezentována stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3e50c-119">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="3e50c-120">Po přečtení, bude připravená k použití těchto struktur vytvořit bohaté adaptivní algoritmy.</span><span class="sxs-lookup"><span data-stu-id="3e50c-120">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="3e50c-121">Stromy výrazů vysvětlené</span><span class="sxs-lookup"><span data-stu-id="3e50c-121">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="3e50c-122">Pochopit strukturu a koncepty za *stromů výrazů*.</span><span class="sxs-lookup"><span data-stu-id="3e50c-122">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="3e50c-123">Framework typy podpůrné stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="3e50c-123">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="3e50c-124">Další informace o struktury a třídy, které definují a manipulaci s stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3e50c-124">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="3e50c-125">Provádění výrazy</span><span class="sxs-lookup"><span data-stu-id="3e50c-125">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="3e50c-126">Zjistěte, jak převést strom výrazu, který je reprezentován jako výraz Lambda do delegáta a provést Výsledný delegát.</span><span class="sxs-lookup"><span data-stu-id="3e50c-126">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="3e50c-127">Interpretace výrazy</span><span class="sxs-lookup"><span data-stu-id="3e50c-127">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="3e50c-128">Zjistěte, jak procházet a prozkoumat *stromů výrazů* zjistit, co kód strom výrazu představuje.</span><span class="sxs-lookup"><span data-stu-id="3e50c-128">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="3e50c-129">Vytváření výrazů</span><span class="sxs-lookup"><span data-stu-id="3e50c-129">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="3e50c-130">Zjistěte, jak sestavit uzlů pro strom výrazu a sestavení stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3e50c-130">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="3e50c-131">Překlad výrazů</span><span class="sxs-lookup"><span data-stu-id="3e50c-131">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="3e50c-132">Naučte se vytvořit kopii strom výrazu upravené nebo přeložit strom výrazu do jiného formátu.</span><span class="sxs-lookup"><span data-stu-id="3e50c-132">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="3e50c-133">Shrnutí</span><span class="sxs-lookup"><span data-stu-id="3e50c-133">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="3e50c-134">Projděte si informace na stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3e50c-134">Review the information on expression trees.</span></span>
    
