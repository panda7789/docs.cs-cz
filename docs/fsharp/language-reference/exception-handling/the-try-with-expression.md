---
title: 'Výjimky: Výraz try...with'
description: Naučte se používat F# try... výraz with pro zpracování výjimek.
ms.date: 05/16/2016
ms.openlocfilehash: e4d615086a93e26b76cca460e797659ca13792b5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630244"
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="ef59e-103">Výjimky: Výraz try...with</span><span class="sxs-lookup"><span data-stu-id="ef59e-103">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="ef59e-104">Toto téma popisuje `try...with` výraz, který se používá pro zpracování výjimek v F# jazyce.</span><span class="sxs-lookup"><span data-stu-id="ef59e-104">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef59e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef59e-105">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="ef59e-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef59e-106">Remarks</span></span>

<span data-ttu-id="ef59e-107">Výraz se používá ke zpracování výjimek v F# `try...with`</span><span class="sxs-lookup"><span data-stu-id="ef59e-107">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="ef59e-108">Je podobný `try...catch` příkazu v. C#</span><span class="sxs-lookup"><span data-stu-id="ef59e-108">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="ef59e-109">V předchozí syntaxi kód v *Výraz1* může generovat výjimku.</span><span class="sxs-lookup"><span data-stu-id="ef59e-109">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="ef59e-110">`try...with` Výraz vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ef59e-110">The `try...with` expression returns a value.</span></span> <span data-ttu-id="ef59e-111">Pokud není vyvolána žádná výjimka, vrátí celý výraz hodnotu *Výraz1*.</span><span class="sxs-lookup"><span data-stu-id="ef59e-111">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="ef59e-112">Je-li vyvolána výjimka, je každý *vzor* porovnán s výjimkou a pro první odpovídající vzor, odpovídající *výraz*, který je známý jako *obslužná rutina výjimky*, pro tuto větev je spuštěn a celkový výraz Vrátí hodnotu výrazu v této obslužné rutině výjimky.</span><span class="sxs-lookup"><span data-stu-id="ef59e-112">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="ef59e-113">Pokud žádný vzor neodpovídá, výjimka rozšíří zásobník volání, dokud není nalezena odpovídající obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="ef59e-113">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="ef59e-114">Typy hodnot vrácených z každého výrazu v obslužných rutinách výjimek se musí shodovat s typem vráceným z výrazu v `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="ef59e-114">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="ef59e-115">Často skutečnost, že došlo k chybě, také znamená, že neexistuje žádná platná hodnota, která může být vrácena z výrazů v každé obslužné rutině výjimky.</span><span class="sxs-lookup"><span data-stu-id="ef59e-115">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="ef59e-116">Častým vzorem je, že typ výrazu je typ možnosti.</span><span class="sxs-lookup"><span data-stu-id="ef59e-116">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="ef59e-117">Následující příklad kódu ukazuje tento model.</span><span class="sxs-lookup"><span data-stu-id="ef59e-117">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="ef59e-118">Výjimky mohou být výjimky rozhraní .NET nebo mohou být F# výjimky.</span><span class="sxs-lookup"><span data-stu-id="ef59e-118">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="ef59e-119">Výjimky lze definovat F# pomocí `exception` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="ef59e-119">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="ef59e-120">Můžete použít celou řadu vzorů k filtrování typu výjimky a dalších podmínek. Tyto možnosti jsou shrnuté v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ef59e-120">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>

|<span data-ttu-id="ef59e-121">Vzor</span><span class="sxs-lookup"><span data-stu-id="ef59e-121">Pattern</span></span>|<span data-ttu-id="ef59e-122">Popis</span><span class="sxs-lookup"><span data-stu-id="ef59e-122">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="ef59e-123">:?</span><span class="sxs-lookup"><span data-stu-id="ef59e-123">:?</span></span> <span data-ttu-id="ef59e-124">*exception-type*</span><span class="sxs-lookup"><span data-stu-id="ef59e-124">*exception-type*</span></span>|<span data-ttu-id="ef59e-125">Odpovídá zadanému typu výjimky .NET.</span><span class="sxs-lookup"><span data-stu-id="ef59e-125">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="ef59e-126">:?</span><span class="sxs-lookup"><span data-stu-id="ef59e-126">:?</span></span> <span data-ttu-id="ef59e-127">*Typ výjimky* jako *identifikátoru*</span><span class="sxs-lookup"><span data-stu-id="ef59e-127">*exception-type* as *identifier*</span></span>|<span data-ttu-id="ef59e-128">Odpovídá zadanému typu výjimky .NET, ale poskytuje výjimku jako pojmenovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ef59e-128">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="ef59e-129">*název výjimky* (*argumenty*)</span><span class="sxs-lookup"><span data-stu-id="ef59e-129">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="ef59e-130">Odpovídá typu F# výjimky a váže argumenty.</span><span class="sxs-lookup"><span data-stu-id="ef59e-130">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="ef59e-131">*RID*</span><span class="sxs-lookup"><span data-stu-id="ef59e-131">*identifier*</span></span>|<span data-ttu-id="ef59e-132">Odpovídá jakékoli výjimce a váže název objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="ef59e-132">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="ef59e-133">**Ekvivalent:? System. Exception**–_identifikátor_</span><span class="sxs-lookup"><span data-stu-id="ef59e-133">Equivalent to **:? System.Exception as**_identifier_</span></span>|
|<span data-ttu-id="ef59e-134">*identifikátor* za *podmínkou*</span><span class="sxs-lookup"><span data-stu-id="ef59e-134">*identifier* when *condition*</span></span>|<span data-ttu-id="ef59e-135">Odpovídá jakékoli výjimce, pokud je podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="ef59e-135">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="ef59e-136">Příklady</span><span class="sxs-lookup"><span data-stu-id="ef59e-136">Examples</span></span>

<span data-ttu-id="ef59e-137">Následující příklady kódu ilustrují použití různých vzorů obslužných rutin výjimek.</span><span class="sxs-lookup"><span data-stu-id="ef59e-137">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]

> [!NOTE]
> <span data-ttu-id="ef59e-138">Konstrukce je samostatný výraz `try...finally` z výrazu. `try...with`</span><span class="sxs-lookup"><span data-stu-id="ef59e-138">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="ef59e-139">Proto pokud váš kód vyžaduje `with` blok `finally` i blok, bude nutné vnořené dva výrazy vnořit.</span><span class="sxs-lookup"><span data-stu-id="ef59e-139">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="ef59e-140">Můžete použít `try...with` v asynchronních pracovních postupech a jiných výrazech výpočtu. v takovém případě se používá `try...with` přizpůsobená verze výrazu.</span><span class="sxs-lookup"><span data-stu-id="ef59e-140">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="ef59e-141">Další informace najdete v tématu [asynchronní pracovní postupy](../asynchronous-workflows.md)a [výpočetní výrazy](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ef59e-141">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef59e-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef59e-142">See also</span></span>

- [<span data-ttu-id="ef59e-143">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="ef59e-143">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="ef59e-144">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="ef59e-144">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="ef59e-145">Výjimky: `try...finally` Výraz</span><span class="sxs-lookup"><span data-stu-id="ef59e-145">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
