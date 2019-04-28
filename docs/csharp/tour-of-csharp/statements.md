---
title: C#Příkazy – připravuje C# jazyka
description: Vytvoření akce C# programu pomocí příkazů
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 75f6c7bb29af7f9c809c5278c97d21683166a8e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706478"
---
# <a name="statements"></a><span data-ttu-id="d1bf5-103">Příkazy</span><span class="sxs-lookup"><span data-stu-id="d1bf5-103">Statements</span></span>

<span data-ttu-id="d1bf5-104">Akce programu jsou vyjádřeny pomocí *příkazy*.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="d1bf5-105">C# podporuje několik různých druhů příkazů, číslo, které jsou definovány z hlediska vložených příkazů.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="d1bf5-106">A *bloku* povoluje více příkazů, které má být zapsán v kontextech, kde je povoleno jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="d1bf5-107">Blok obsahuje seznam příkazů, které jsou napsané mezi oddělovači `{` a `}`.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="d1bf5-108">*Příkazy deklarace* se používají k deklarování místní proměnné a konstanty.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="d1bf5-109">*Příkazy výrazů* se používají k vyhodnocení výrazů.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="d1bf5-110">Volání metod, obsahovat výrazy, které lze použít jako příkazy přidělení pomocí objektu `new` operátora, přiřazení pomocí `=` a operátory složeného přiřazení, operace Inkrementace a dekrementace pomocí `++`a `--` operátory a `await` výrazy.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="d1bf5-111">*Příkazy výběru* se používají k výběru jedním z možných příkazů pro spuštění na základě hodnoty některých výrazu.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="d1bf5-112">V této skupině jsou `if` a `switch` příkazy.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-112">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="d1bf5-113">*Příkazy iterace* se používají ke spouštění opakovaně vloženým příkazem.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="d1bf5-114">V této skupině jsou `while`, `do`, `for`, a `foreach` příkazy.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-114">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="d1bf5-115">*Jump – příkazy* slouží k předání řízení.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="d1bf5-116">V této skupině jsou `break`, `continue`, `goto`, `throw`, `return`, a `yield` příkazy.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-116">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="d1bf5-117">`try`... `catch` prohlášení se používá k zachycení výjimek, ke kterým dochází při provádění bloku, a `try`... `finally` prohlášení se používá k určení dokončovacího kódu, který je vždy spuštěn, zda došlo k výjimce, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="d1bf5-118">`checked` a `unchecked` příkazy se používají k řízení kontextu kontrol přetečení pro aritmetické operace s celými čísly a převody.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="d1bf5-119">`lock` Prohlášení se používá k získání zámku vzájemné vyloučení pro daný objekt, provedení příkazu a uvolněte zámek.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="d1bf5-120">`using` Prohlášení se používá k získání prostředku, provedení příkazu a potom tento prostředek.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="d1bf5-121">Následuje seznam typy příkazů, které lze použít a poskytuje příklad pro každý.</span><span class="sxs-lookup"><span data-stu-id="d1bf5-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="d1bf5-122">Deklarace lokální proměnné:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="d1bf5-123">Místní deklarace konstanty:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="d1bf5-124">Příkaz výrazu:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="d1bf5-125">`if` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="d1bf5-126">`switch` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="d1bf5-127">`while` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="d1bf5-128">`do` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="d1bf5-129">`for` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="d1bf5-130">`foreach` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="d1bf5-131">`break` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="d1bf5-132">`continue` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="d1bf5-133">`goto` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="d1bf5-134">`return` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="d1bf5-135">`yield` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="d1bf5-136">`throw` Příkazy a `try` příkazy:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="d1bf5-137">`checked` a `unchecked` příkazy:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="d1bf5-138">`lock` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="d1bf5-139">`using` příkaz:</span><span class="sxs-lookup"><span data-stu-id="d1bf5-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
><span data-ttu-id="d1bf5-140">[Předchozí](expressions.md)
>[další](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="d1bf5-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>