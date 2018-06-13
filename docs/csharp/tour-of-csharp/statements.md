---
title: C# příkazy – přehled používání jazyka C#
description: Vytvoříte akce programu v C# pomocí příkazů
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 2f25c07ccc0af27a503465b9414bf607c61d1b2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351976"
---
# <a name="statements"></a><span data-ttu-id="93e5e-103">Příkazy</span><span class="sxs-lookup"><span data-stu-id="93e5e-103">Statements</span></span>

<span data-ttu-id="93e5e-104">Akce programu jsou vyjádřeny pomocí *příkazy*.</span><span class="sxs-lookup"><span data-stu-id="93e5e-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="93e5e-105">C# podporuje několik různých druhů příkazy, počet jsou definována v embedded příkazy.</span><span class="sxs-lookup"><span data-stu-id="93e5e-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="93e5e-106">A *bloku* umožňuje více příkazů, které má být zapsán v kontextu, kde je povoleno jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="93e5e-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="93e5e-107">Blok sestává ze seznamu příkazů, které jsou zapsány mezi oddělovače `{` a `}`.</span><span class="sxs-lookup"><span data-stu-id="93e5e-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="93e5e-108">*Deklarační příkazy* se používá k deklaraci místní proměnné a konstanty.</span><span class="sxs-lookup"><span data-stu-id="93e5e-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="93e5e-109">*Příkazy výrazu* se používají k vyhodnocení výrazů.</span><span class="sxs-lookup"><span data-stu-id="93e5e-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="93e5e-110">Výrazy, které lze použít jako příkazy zahrnují volání metod objektu přidělení pomocí `new` operátor, přiřazení pomocí `=` a složené operátory přiřazení, přírůstek a snížení operace pomocí `++`a `--` operátory a `await` výrazy.</span><span class="sxs-lookup"><span data-stu-id="93e5e-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="93e5e-111">*Příkazy výběru* slouží k výběru jedné počet možných příkazů pro spuštění na základě hodnoty některých výrazu.</span><span class="sxs-lookup"><span data-stu-id="93e5e-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="93e5e-112">V této skupině se `if` a `switch` příkazy.</span><span class="sxs-lookup"><span data-stu-id="93e5e-112">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="93e5e-113">*Příkazy iterace* se používají k provedení příkazu embedded opakovaně.</span><span class="sxs-lookup"><span data-stu-id="93e5e-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="93e5e-114">V této skupině se `while`, `do`, `for`, a `foreach` příkazy.</span><span class="sxs-lookup"><span data-stu-id="93e5e-114">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="93e5e-115">*Jump – příkazy* se používá k přenosu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="93e5e-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="93e5e-116">V této skupině se `break`, `continue`, `goto`, `throw`, `return`, a `yield` příkazy.</span><span class="sxs-lookup"><span data-stu-id="93e5e-116">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="93e5e-117">`try`... `catch` příkaz se používá k zachycení výjimky, ke kterým došlo během provádění blok, a `try`... `finally` příkaz slouží k určení finalizace kód, který je spuštěn vždy, zda došlo k chybě, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="93e5e-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="93e5e-118">`checked` a `unchecked` příkazy jsou používány k ovládání kontext kontrola Přetečení aritmetické operace integrální type a převody.</span><span class="sxs-lookup"><span data-stu-id="93e5e-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="93e5e-119">`lock` Se použije příkaz získat zámek vzájemné vyloučení pro daný objekt, provedení příkazu a pak uvolní zámek.</span><span class="sxs-lookup"><span data-stu-id="93e5e-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="93e5e-120">`using` Se použije příkaz získat prostředek, provedení příkazu a pak odstranění tohoto prostředku.</span><span class="sxs-lookup"><span data-stu-id="93e5e-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="93e5e-121">V následujícím seznamu uvedeny druhy příkazy, které lze použít a představuje příklad.</span><span class="sxs-lookup"><span data-stu-id="93e5e-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="93e5e-122">Místní deklarace proměnné:</span><span class="sxs-lookup"><span data-stu-id="93e5e-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="93e5e-123">Místní deklarace konstanty:</span><span class="sxs-lookup"><span data-stu-id="93e5e-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="93e5e-124">Příkaz výrazu:</span><span class="sxs-lookup"><span data-stu-id="93e5e-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="93e5e-125">`if` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="93e5e-126">`switch` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="93e5e-127">`while` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="93e5e-128">`do` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="93e5e-129">`for` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="93e5e-130">`foreach` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="93e5e-131">`break` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="93e5e-132">`continue` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="93e5e-133">`goto` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="93e5e-134">`return` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="93e5e-135">`yield` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="93e5e-136">`throw` Příkazy a `try` příkazy:</span><span class="sxs-lookup"><span data-stu-id="93e5e-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="93e5e-137">`checked` a `unchecked` příkazy:</span><span class="sxs-lookup"><span data-stu-id="93e5e-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="93e5e-138">`lock` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="93e5e-139">`using` příkaz:</span><span class="sxs-lookup"><span data-stu-id="93e5e-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
<span data-ttu-id="93e5e-140">[Předchozí](expressions.md)
[další](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="93e5e-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
