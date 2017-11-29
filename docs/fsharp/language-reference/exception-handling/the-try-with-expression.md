---
title: "Výjimky: Výraz try...with (F#)"
description: "Naučte se používat pro zpracovávání výjimek v jazyce F # 'try... with' výraz."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 36721076-95cd-4636-ae43-79dd512bee6c
ms.openlocfilehash: 163dfab49d4aaf23123800246fae2cad33e2257c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="f51d6-104">Výjimky: Výraz try...with</span><span class="sxs-lookup"><span data-stu-id="f51d6-104">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="f51d6-105">Toto téma popisuje `try...with` výrazu, výraz, který se používá pro zpracování výjimek v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="f51d6-105">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>


## <a name="syntax"></a><span data-ttu-id="f51d6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f51d6-106">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="f51d6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f51d6-107">Remarks</span></span>
<span data-ttu-id="f51d6-108">`try...with` Výraz se používá pro zpracování výjimek v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="f51d6-108">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="f51d6-109">Je podobná `try...catch` příkaz v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="f51d6-109">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="f51d6-110">V předchozím syntaxi kód v *expression1* může generovat výjimku.</span><span class="sxs-lookup"><span data-stu-id="f51d6-110">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="f51d6-111">`try...with` Vrací hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="f51d6-111">The `try...with` expression returns a value.</span></span> <span data-ttu-id="f51d6-112">Pokud nedojde k výjimce, celý výraz vrací hodnotu *expression1*.</span><span class="sxs-lookup"><span data-stu-id="f51d6-112">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="f51d6-113">Pokud je vyvolána výjimka, každý *vzor* se pak porovná s výjimkou a pro první odpovídající vzor odpovídající *výraz*, označovaný jako *obslužná rutina výjimky*, je proveden uvedené pobočky a celkové výraz vrací hodnotu výrazu v této obslužné rutiny výjimek.</span><span class="sxs-lookup"><span data-stu-id="f51d6-113">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="f51d6-114">Pokud žádné vzor odpovídá, výjimka šíří zásobníkem volání, dokud nebude nalezen odpovídající obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="f51d6-114">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="f51d6-115">Typy hodnot vrácených z každého výrazu v obslužné rutiny výjimek musí odpovídat typ vrácený z výrazu v `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="f51d6-115">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="f51d6-116">Fakt, že došlo k chybě také často, znamená, že je žádné platnou hodnotu, která lze vrátit ze výrazy v každé obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="f51d6-116">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="f51d6-117">Časté vzor je tak, aby měl být typu možnost Typ výrazu.</span><span class="sxs-lookup"><span data-stu-id="f51d6-117">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="f51d6-118">Následující příklad kódu ukazuje tento vzor.</span><span class="sxs-lookup"><span data-stu-id="f51d6-118">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="f51d6-119">Výjimky může být výjimky .NET, nebo mohou být výjimky F #.</span><span class="sxs-lookup"><span data-stu-id="f51d6-119">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="f51d6-120">Můžete taky definovat výjimky F # pomocí `exception` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="f51d6-120">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="f51d6-121">Řadu vzorů můžete použít k filtrování na typ výjimky a další podmínky; Možnosti jsou shrnuty v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="f51d6-121">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>


|<span data-ttu-id="f51d6-122">Vzor</span><span class="sxs-lookup"><span data-stu-id="f51d6-122">Pattern</span></span>|<span data-ttu-id="f51d6-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f51d6-123">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="f51d6-124">:?</span><span class="sxs-lookup"><span data-stu-id="f51d6-124">:?</span></span> <span data-ttu-id="f51d6-125">*Typ výjimky*</span><span class="sxs-lookup"><span data-stu-id="f51d6-125">*exception-type*</span></span>|<span data-ttu-id="f51d6-126">Odpovídá zadaný typ výjimky .NET.</span><span class="sxs-lookup"><span data-stu-id="f51d6-126">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="f51d6-127">:?</span><span class="sxs-lookup"><span data-stu-id="f51d6-127">:?</span></span> <span data-ttu-id="f51d6-128">*Typ výjimky* jako *identifikátor*</span><span class="sxs-lookup"><span data-stu-id="f51d6-128">*exception-type* as *identifier*</span></span>|<span data-ttu-id="f51d6-129">Odpovídá zadaný typ výjimky .NET, ale dává výjimka pojmenované hodnotě.</span><span class="sxs-lookup"><span data-stu-id="f51d6-129">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="f51d6-130">*název výjimky*(*argumenty*)</span><span class="sxs-lookup"><span data-stu-id="f51d6-130">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="f51d6-131">Odpovídá typ výjimky F # a sváže argumenty.</span><span class="sxs-lookup"><span data-stu-id="f51d6-131">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="f51d6-132">*identifikátor*</span><span class="sxs-lookup"><span data-stu-id="f51d6-132">*identifier*</span></span>|<span data-ttu-id="f51d6-133">Odpovídá jakékoli výjimky a sváže název objekt výjimky.</span><span class="sxs-lookup"><span data-stu-id="f51d6-133">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="f51d6-134">Ekvivalentní **:? System.Exception jako***identifikátor*</span><span class="sxs-lookup"><span data-stu-id="f51d6-134">Equivalent to **:? System.Exception as***identifier*</span></span>|
|<span data-ttu-id="f51d6-135">*identifikátor* při *podmínky*</span><span class="sxs-lookup"><span data-stu-id="f51d6-135">*identifier* when *condition*</span></span>|<span data-ttu-id="f51d6-136">Odpovídá jakékoli výjimky, pokud je podmínka vyhodnocena jako true.</span><span class="sxs-lookup"><span data-stu-id="f51d6-136">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="f51d6-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="f51d6-137">Examples</span></span>
<span data-ttu-id="f51d6-138">Následující příklady kódu ilustrují použití různých vzorů obslužná rutina výjimky.</span><span class="sxs-lookup"><span data-stu-id="f51d6-138">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]
    
>[!NOTE] 
<span data-ttu-id="f51d6-139">`try...with` Konstrukce je samostatného výrazu z `try...finally` výraz.</span><span class="sxs-lookup"><span data-stu-id="f51d6-139">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="f51d6-140">Proto pokud kódu vyžaduje, aby obě `with` bloku a `finally` bloku, budete muset vnořit dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="f51d6-140">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

>[!NOTE] 
<span data-ttu-id="f51d6-141">Můžete použít `try...with` v asynchronní pracovní postupy a další výpočetní výrazy, ve kterém případ přizpůsobená verze `try...with` použit výraz.</span><span class="sxs-lookup"><span data-stu-id="f51d6-141">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="f51d6-142">Další informace najdete v tématu [asynchronní pracovní postupy](../asynchronous-workflows.md), a [výpočetní výrazy](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f51d6-142">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="f51d6-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="f51d6-143">See Also</span></span>
[<span data-ttu-id="f51d6-144">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="f51d6-144">Exception Handling</span></span>](index.md)

[<span data-ttu-id="f51d6-145">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="f51d6-145">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="f51d6-146">Výjimky: `try...finally` výraz</span><span class="sxs-lookup"><span data-stu-id="f51d6-146">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
