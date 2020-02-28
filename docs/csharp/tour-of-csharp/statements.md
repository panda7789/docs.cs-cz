---
title: C#Příkazy – prohlídka C# jazyka
description: Akce C# programu vytvoříte pomocí příkazů
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159101"
---
# <a name="statements"></a><span data-ttu-id="281b9-103">Příkazy</span><span class="sxs-lookup"><span data-stu-id="281b9-103">Statements</span></span>

<span data-ttu-id="281b9-104">Akce programu jsou vyjádřeny pomocí *příkazů*.</span><span class="sxs-lookup"><span data-stu-id="281b9-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="281b9-105">C#podporuje několik různých druhů příkazů, jejichž počet je definován z podmínek vložených příkazů.</span><span class="sxs-lookup"><span data-stu-id="281b9-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="281b9-106">*Blok* povoluje zápis více příkazů v kontextech, kde je povolen jediný příkaz.</span><span class="sxs-lookup"><span data-stu-id="281b9-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="281b9-107">Blok obsahuje seznam příkazů zapsaných mezi oddělovači `{` a `}`.</span><span class="sxs-lookup"><span data-stu-id="281b9-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="281b9-108">*Příkazy deklarace* slouží k deklaraci lokálních proměnných a konstant.</span><span class="sxs-lookup"><span data-stu-id="281b9-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="281b9-109">*Příkazy výrazů* se používají k vyhodnocení výrazů.</span><span class="sxs-lookup"><span data-stu-id="281b9-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="281b9-110">Výrazy, které lze použít jako příkazy, zahrnují vyvolání metod, přidělení objektů pomocí operátoru `new`, přiřazení pomocí `=` a operátory složeného přiřazení, zvýšení a snížení provozu pomocí operátorů `++` a `--` a `await` výrazů.</span><span class="sxs-lookup"><span data-stu-id="281b9-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="281b9-111">*Příkazy výběru* se používají k výběru jednoho z několika možných příkazů pro spuštění na základě hodnoty nějakého výrazu.</span><span class="sxs-lookup"><span data-stu-id="281b9-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="281b9-112">Tato skupina obsahuje příkazy `if` a `switch`.</span><span class="sxs-lookup"><span data-stu-id="281b9-112">This group contains the `if` and `switch` statements.</span></span>

<span data-ttu-id="281b9-113">*Příkazy iterace* se používají ke opakovanému provedení vloženého příkazu.</span><span class="sxs-lookup"><span data-stu-id="281b9-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="281b9-114">Tato skupina obsahuje příkazy `while`, `do`, `for`a `foreach`.</span><span class="sxs-lookup"><span data-stu-id="281b9-114">This group contains the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="281b9-115">*Příkazy skoku* slouží k přenosu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="281b9-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="281b9-116">Tato skupina obsahuje příkazy `break`, `continue`, `goto`, `throw`, `return`a `yield`.</span><span class="sxs-lookup"><span data-stu-id="281b9-116">This group contains the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="281b9-117">Příkaz `try`...`catch` slouží k zachycení výjimek, ke kterým dojde během provádění bloku, a příkaz `try`...`finally` slouží k určení finálního kódu, který je vždy spuštěn, bez ohledu na to, zda došlo k výjimce nebo nikoli.</span><span class="sxs-lookup"><span data-stu-id="281b9-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="281b9-118">Příkazy `checked` a `unchecked` slouží k řízení kontextu kontroly přetečení pro aritmetické operace a převody integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="281b9-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="281b9-119">Příkaz `lock` slouží k získání zámku vzájemného vyloučení pro daný objekt, spuštění příkazu a uvolnění zámku.</span><span class="sxs-lookup"><span data-stu-id="281b9-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="281b9-120">Příkaz `using` slouží k získání prostředku, spuštění příkazu a následnému uvolnění tohoto prostředku.</span><span class="sxs-lookup"><span data-stu-id="281b9-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="281b9-121">Následující seznam uvádí typy příkazů, které lze použít, a poskytuje příklad pro každý z nich.</span><span class="sxs-lookup"><span data-stu-id="281b9-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="281b9-122">Místní deklarace proměnné:</span><span class="sxs-lookup"><span data-stu-id="281b9-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="281b9-123">Deklarace místní konstanty:</span><span class="sxs-lookup"><span data-stu-id="281b9-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="281b9-124">Příkaz výrazu:</span><span class="sxs-lookup"><span data-stu-id="281b9-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="281b9-125">příkaz `if`:</span><span class="sxs-lookup"><span data-stu-id="281b9-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="281b9-126">příkaz `switch`:</span><span class="sxs-lookup"><span data-stu-id="281b9-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="281b9-127">příkaz `while`:</span><span class="sxs-lookup"><span data-stu-id="281b9-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="281b9-128">příkaz `do`:</span><span class="sxs-lookup"><span data-stu-id="281b9-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="281b9-129">příkaz `for`:</span><span class="sxs-lookup"><span data-stu-id="281b9-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="281b9-130">příkaz `foreach`:</span><span class="sxs-lookup"><span data-stu-id="281b9-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="281b9-131">příkaz `break`:</span><span class="sxs-lookup"><span data-stu-id="281b9-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="281b9-132">příkaz `continue`:</span><span class="sxs-lookup"><span data-stu-id="281b9-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="281b9-133">příkaz `goto`:</span><span class="sxs-lookup"><span data-stu-id="281b9-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="281b9-134">příkaz `return`:</span><span class="sxs-lookup"><span data-stu-id="281b9-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="281b9-135">příkaz `yield`:</span><span class="sxs-lookup"><span data-stu-id="281b9-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="281b9-136">příkazy `throw` a příkazy `try`:</span><span class="sxs-lookup"><span data-stu-id="281b9-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="281b9-137">příkazy `checked` a `unchecked`:</span><span class="sxs-lookup"><span data-stu-id="281b9-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="281b9-138">příkaz `lock`:</span><span class="sxs-lookup"><span data-stu-id="281b9-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="281b9-139">příkaz `using`:</span><span class="sxs-lookup"><span data-stu-id="281b9-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
><span data-ttu-id="281b9-140">[Předchozí](expressions.md)
>[Další](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="281b9-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
