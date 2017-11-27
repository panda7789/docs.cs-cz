---
title: "C# příkazy – přehled používání jazyka C#"
description: "Vytvoříte akce programu v C# pomocí příkazů"
keywords: "Rozhraní .NET, csharp, příkazy, syntaxe"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 99ec2489daf89926da9b8c4e148965412826a8a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="statements"></a><span data-ttu-id="02636-104">Příkazy</span><span class="sxs-lookup"><span data-stu-id="02636-104">Statements</span></span>

<span data-ttu-id="02636-105">Akce programu jsou vyjádřeny pomocí *příkazy*.</span><span class="sxs-lookup"><span data-stu-id="02636-105">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="02636-106">C# podporuje několik různých druhů příkazy, počet jsou definována v embedded příkazy.</span><span class="sxs-lookup"><span data-stu-id="02636-106">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="02636-107">A *bloku* umožňuje více příkazů, které má být zapsán v kontextu, kde je povoleno jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="02636-107">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="02636-108">Blok sestává ze seznamu příkazů, které jsou zapsány mezi oddělovače `{` a `}`.</span><span class="sxs-lookup"><span data-stu-id="02636-108">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="02636-109">*Deklarační příkazy* se používá k deklaraci místní proměnné a konstanty.</span><span class="sxs-lookup"><span data-stu-id="02636-109">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="02636-110">*Příkazy výrazu* se používají k vyhodnocení výrazů.</span><span class="sxs-lookup"><span data-stu-id="02636-110">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="02636-111">Výrazy, které lze použít jako příkazy zahrnují volání metod objektu přidělení pomocí `new` operátor, přiřazení pomocí `=` a složené operátory přiřazení, přírůstek a snížení operace pomocí `++`a `--` operátory a `await` výrazy.</span><span class="sxs-lookup"><span data-stu-id="02636-111">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="02636-112">*Příkazy výběru* slouží k výběru jedné počet možných příkazů pro spuštění na základě hodnoty některých výrazu.</span><span class="sxs-lookup"><span data-stu-id="02636-112">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="02636-113">V této skupině se `if` a `switch` příkazy.</span><span class="sxs-lookup"><span data-stu-id="02636-113">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="02636-114">*Příkazy iterace* se používají k provedení příkazu embedded opakovaně.</span><span class="sxs-lookup"><span data-stu-id="02636-114">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="02636-115">V této skupině se `while`, `do`, `for`, a `foreach` příkazy.</span><span class="sxs-lookup"><span data-stu-id="02636-115">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="02636-116">*Jump – příkazy* se používá k přenosu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="02636-116">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="02636-117">V této skupině se `break`, `continue`, `goto`, `throw`, `return`, a `yield` příkazy.</span><span class="sxs-lookup"><span data-stu-id="02636-117">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="02636-118">`try`... `catch` příkaz se používá k zachycení výjimky, ke kterým došlo během provádění blok, a `try`... `finally` příkaz slouží k určení finalizace kód, který je spuštěn vždy, zda došlo k chybě, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="02636-118">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="02636-119">`checked` a `unchecked` příkazy jsou používány k ovládání kontext kontrola Přetečení aritmetické operace integrální type a převody.</span><span class="sxs-lookup"><span data-stu-id="02636-119">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="02636-120">`lock` Se použije příkaz získat zámek vzájemné vyloučení pro daný objekt, provedení příkazu a pak uvolní zámek.</span><span class="sxs-lookup"><span data-stu-id="02636-120">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="02636-121">`using` Se použije příkaz získat prostředek, provedení příkazu a pak odstranění tohoto prostředku.</span><span class="sxs-lookup"><span data-stu-id="02636-121">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="02636-122">V následujícím seznamu uvedeny druhy příkazy, které lze použít a představuje příklad.</span><span class="sxs-lookup"><span data-stu-id="02636-122">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="02636-123">Místní deklarace proměnné:</span><span class="sxs-lookup"><span data-stu-id="02636-123">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="02636-124">Místní deklarace konstanty:</span><span class="sxs-lookup"><span data-stu-id="02636-124">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="02636-125">Příkaz výrazu:</span><span class="sxs-lookup"><span data-stu-id="02636-125">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="02636-126">`if`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-126">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="02636-127">`switch`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-127">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="02636-128">`while`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-128">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="02636-129">`do`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-129">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="02636-130">`for`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-130">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="02636-131">`foreach`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-131">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="02636-132">`break`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-132">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="02636-133">`continue`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-133">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="02636-134">`goto`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-134">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="02636-135">`return`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-135">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="02636-136">`yield`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-136">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="02636-137">`throw`Příkazy a `try` příkazy:</span><span class="sxs-lookup"><span data-stu-id="02636-137">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="02636-138">`checked`a `unchecked` příkazy:</span><span class="sxs-lookup"><span data-stu-id="02636-138">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="02636-139">`lock`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-139">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="02636-140">`using`příkaz:</span><span class="sxs-lookup"><span data-stu-id="02636-140">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
<span data-ttu-id="02636-141">[Předchozí](expressions.md)
[další](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="02636-141">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
