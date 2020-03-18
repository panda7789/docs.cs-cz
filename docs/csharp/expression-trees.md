---
title: Stromy výrazů
description: Další informace o stromech výrazů v .NET Core a jak je použít k reprezentaci kódu jako struktur, které můžete zkoumat, upravovat a spouštět.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: e1026ef70860da519b688a9d67181b88d03f6f0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145836"
---
# <a name="expression-trees"></a><span data-ttu-id="5a267-103">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="5a267-103">Expression Trees</span></span>

<span data-ttu-id="5a267-104">Pokud jste použili LINQ, máte zkušenosti s `Func` bohatou knihovnou, kde jsou typy součástí sady rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5a267-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="5a267-105">(Pokud nejste obeznámeni s LINQ, pravděpodobně budete chtít přečíst [linq tutorial](linq/index.md) a článek o [lambda výrazy](./programming-guide/statements-expressions-operators/lambda-expressions.md) před tímto jeden.) *Výraz stromy* poskytují bohatší interakci s argumenty, které jsou funkce.</span><span class="sxs-lookup"><span data-stu-id="5a267-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="5a267-106">Při vytváření dotazů LINQ se při zapisují argumenty funkce, obvykle pomocí výrazů Lambda.</span><span class="sxs-lookup"><span data-stu-id="5a267-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="5a267-107">V typickélinq dotazu jsou tyto argumenty funkce transformovány do delegáta, který vytvoří kompilátor.</span><span class="sxs-lookup"><span data-stu-id="5a267-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span>

<span data-ttu-id="5a267-108">Chcete-li mít bohatší interakci, je třeba použít *stromy výrazů*.</span><span class="sxs-lookup"><span data-stu-id="5a267-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="5a267-109">Stromy výrazů představují kód jako strukturu, kterou můžete prozkoumat, upravit nebo spustit.</span><span class="sxs-lookup"><span data-stu-id="5a267-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="5a267-110">Tyto nástroje vám dávají možnost manipulovat s kódem za běhu.</span><span class="sxs-lookup"><span data-stu-id="5a267-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="5a267-111">Můžete napsat kód, který zkoumá spuštěné algoritmy nebo vloží nové funkce.</span><span class="sxs-lookup"><span data-stu-id="5a267-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="5a267-112">V pokročilejších scénářích můžete upravit běžící algoritmy a dokonce přeložit výrazy Jazyka C# do jiného formuláře pro spuštění v jiném prostředí.</span><span class="sxs-lookup"><span data-stu-id="5a267-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="5a267-113">Pravděpodobně jste již napsali kód, který používá stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="5a267-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="5a267-114">Rozhraní LINQ rozhraní LINQ frameworku entity přijímají stromy výrazů jako argumenty pro vzorek výrazu dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="5a267-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="5a267-115">To umožňuje [entity Framework](/ef/) přeložit dotaz, který jste napsali v C# do SQL, který se spustí v databázovém stroji.</span><span class="sxs-lookup"><span data-stu-id="5a267-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="5a267-116">Dalším příkladem je [Moq](https://github.com/Moq/moq), což je populární mocking framework pro .NET.</span><span class="sxs-lookup"><span data-stu-id="5a267-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="5a267-117">Zbývající části tohoto kurzu se budou zabývat tím, co jsou stromy výrazů, prozkoumáme třídy architektury, které podporují stromy výrazů, a ukáží vám, jak pracovat se stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="5a267-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="5a267-118">Dozvíte se, jak číst stromy výrazů, jak vytvářet stromy výrazů, jak vytvářet změněné stromy výrazů a jak spustit kód reprezentovaný stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="5a267-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="5a267-119">Po přečtení budete připraveni použít tyto struktury k vytvoření bohatých adaptivních algoritmů.</span><span class="sxs-lookup"><span data-stu-id="5a267-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="5a267-120">Vysvětlení stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="5a267-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="5a267-121">Seznamte se s strukturou a koncepty za *stromy výrazů*.</span><span class="sxs-lookup"><span data-stu-id="5a267-121">Understand the structure and concepts behind *Expression Trees*.</span></span>

2. [<span data-ttu-id="5a267-122">Typy architektur podporující stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="5a267-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

    <span data-ttu-id="5a267-123">Seznamte se s strukturami a třídami, které definují stromy výrazů a manipulují s nimi.</span><span class="sxs-lookup"><span data-stu-id="5a267-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>

3. [<span data-ttu-id="5a267-124">Provádění výrazů</span><span class="sxs-lookup"><span data-stu-id="5a267-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="5a267-125">Zjistěte, jak převést strom výrazů reprezentovaný jako výraz Lambda na delegáta a provést výsledného delegáta.</span><span class="sxs-lookup"><span data-stu-id="5a267-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="5a267-126">Interpretace výrazů</span><span class="sxs-lookup"><span data-stu-id="5a267-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="5a267-127">Zjistěte, jak procházet a zkoumat *stromy výrazů,* abyste pochopili, jaký kód strom výrazu představuje.</span><span class="sxs-lookup"><span data-stu-id="5a267-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="5a267-128">Vytváření výrazů</span><span class="sxs-lookup"><span data-stu-id="5a267-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="5a267-129">Naučte se, jak vytvořit uzly pro strom výrazů a vytvořit stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="5a267-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="5a267-130">Překlad výrazů</span><span class="sxs-lookup"><span data-stu-id="5a267-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="5a267-131">Zjistěte, jak vytvořit upravenou kopii stromu výrazů nebo přeložit strom výrazů do jiného formátu.</span><span class="sxs-lookup"><span data-stu-id="5a267-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="5a267-132">Sečtením</span><span class="sxs-lookup"><span data-stu-id="5a267-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="5a267-133">Zkontrolujte informace o stromech výrazů.</span><span class="sxs-lookup"><span data-stu-id="5a267-133">Review the information on expression trees.</span></span>
