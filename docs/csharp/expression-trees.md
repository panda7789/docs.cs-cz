---
title: Stromy výrazů
description: Další informace o stromů výrazů v .NET Core a jak se dají použít k reprezentaci kód jako struktury, které můžete zkontrolovat, upravit a spustit.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: 56509f1eb0f2bdca8a8f3a51df958d42e95af6f4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190733"
---
# <a name="expression-trees"></a><span data-ttu-id="ae79c-103">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="ae79c-103">Expression Trees</span></span>

<span data-ttu-id="ae79c-104">Pokud jste použili LINQ, budete mít prostředí, bohatá knihovna kde `Func` typy jsou součástí sady rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ae79c-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="ae79c-105">(Pokud nejste obeznámeni s jazykem LINQ, pravděpodobně chtít číst [kurzu LINQ](linq/index.md) a kurz týkající se [výrazy lambda](lambda-expressions.md) před tímto.) *Stromy výrazů* poskytovat lepší interakci s argumenty, které jsou funkce.</span><span class="sxs-lookup"><span data-stu-id="ae79c-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the tutorial on [lambda expressions](lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="ae79c-106">Můžete napsat argumenty funkce, obvykle pomocí výrazů Lambda, při vytváření dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="ae79c-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="ae79c-107">V typické dotaz LINQ jsou tyto argumenty funkce transformuje na delegáta, který kompilátor vytvoří.</span><span class="sxs-lookup"><span data-stu-id="ae79c-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="ae79c-108">Pokud chcete mít lepší interakci, budete muset použít *stromů výrazů*.</span><span class="sxs-lookup"><span data-stu-id="ae79c-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="ae79c-109">Stromy výrazů reprezentovala strukturu, která můžete zkontrolovat, upravit nebo spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="ae79c-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="ae79c-110">Tyto nástroje vám poskytnou výkon během manipulace s kódem.</span><span class="sxs-lookup"><span data-stu-id="ae79c-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="ae79c-111">Můžete napsat kód, který prověří spuštěnými algoritmy nebo vloží nové funkce.</span><span class="sxs-lookup"><span data-stu-id="ae79c-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="ae79c-112">V pokročilejších scénářích, můžete upravit, spouštění algoritmů a dokonce i přeložit C# výrazy do jiného formátu pro spuštění v jiném prostředí.</span><span class="sxs-lookup"><span data-stu-id="ae79c-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="ae79c-113">Pravděpodobně jste už napsali kód, který používá stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="ae79c-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="ae79c-114">Rozhraní Entity Framework LINQ API přijmout stromů výrazů jako argumenty pro vzor výrazu dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="ae79c-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="ae79c-115">Která umožňuje [Entity Framework](/ef/) přeložit dotazu, který jste napsali v C# do SQL, který se spustí v databázovém stroji.</span><span class="sxs-lookup"><span data-stu-id="ae79c-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="ae79c-116">Dalším příkladem je [Moq](https://github.com/Moq/moq), což je oblíbená architektura napodobování .NET.</span><span class="sxs-lookup"><span data-stu-id="ae79c-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="ae79c-117">Zbývající části tohoto kurzu bude prozkoumejte, jaké jsou stromů výrazů, prozkoumejte třídy rozhraní, které podporují stromů výrazů a ukazují, jak pracovat s stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="ae79c-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="ae79c-118">Dozvíte se, jak číst stromů výrazů, k vytvoření stromů výrazu, k vytvoření stromů výrazu upravené a ke spouštění kódu vytvořeného reprezentována stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="ae79c-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="ae79c-119">Po přečtení, bude připravené k použití těchto struktur vytvořit bohaté adaptivní algoritmy.</span><span class="sxs-lookup"><span data-stu-id="ae79c-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="ae79c-120">Vysvětlení stromů výrazů</span><span class="sxs-lookup"><span data-stu-id="ae79c-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="ae79c-121">Princip struktury a Principy *stromů výrazů*.</span><span class="sxs-lookup"><span data-stu-id="ae79c-121">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="ae79c-122">Typy architektur podporující stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="ae79c-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="ae79c-123">Další informace o struktur a tříd, které definují a manipulaci s stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="ae79c-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="ae79c-124">Provádění výrazů</span><span class="sxs-lookup"><span data-stu-id="ae79c-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="ae79c-125">Zjistěte, jak převést na strom výrazu, který je reprezentován jako výraz Lambda delegátovi a spusťte Výsledný delegát.</span><span class="sxs-lookup"><span data-stu-id="ae79c-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="ae79c-126">Interpretace výrazů</span><span class="sxs-lookup"><span data-stu-id="ae79c-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="ae79c-127">Další informace o procházení a prozkoumání *stromů výrazů* pochopit, co kód stromu výrazů představuje.</span><span class="sxs-lookup"><span data-stu-id="ae79c-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="ae79c-128">Vytváření výrazů</span><span class="sxs-lookup"><span data-stu-id="ae79c-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="ae79c-129">Zjistěte, jak můžete vytvářet na uzly stromu výrazů a vytváření stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="ae79c-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="ae79c-130">Překlad výrazů</span><span class="sxs-lookup"><span data-stu-id="ae79c-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="ae79c-131">Zjistěte, jak sestavovat upravenou kopii strom výrazu, nebo strom výrazů se převedou do jiného formátu.</span><span class="sxs-lookup"><span data-stu-id="ae79c-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="ae79c-132">Shrnutí</span><span class="sxs-lookup"><span data-stu-id="ae79c-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="ae79c-133">Projděte si informace na stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="ae79c-133">Review the information on expression trees.</span></span>
    
