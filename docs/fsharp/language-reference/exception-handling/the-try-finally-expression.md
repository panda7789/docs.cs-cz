---
title: "Výjimky: Výraz try...finally (F#)"
description: "Zjistěte, jak F # ' try... finally' výrazu umožňuje spuštění kódu čištění i v případě, že blok kódu vyvolá výjimku."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: af06b20c-8d87-4496-a0aa-6fdfe8b3a786
ms.openlocfilehash: 2e2445c42bf8129ea81beef56cb725ac0e37d202
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="5b18d-104">Výjimky: Výraz try...finally</span><span class="sxs-lookup"><span data-stu-id="5b18d-104">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="5b18d-105">`try...finally` Výrazu umožňuje spuštění kódu čištění i v případě, že blok kódu vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="5b18d-105">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>


## <a name="syntax"></a><span data-ttu-id="5b18d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b18d-106">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="5b18d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b18d-107">Remarks</span></span>
<span data-ttu-id="5b18d-108">`try...finally` Výraz můžete použít ke spouštění kódu vytvořeného v *Výraz2* v předchozí syntaxi bez ohledu na to, jestli se vygeneruje výjimku během provádění *expression1*.</span><span class="sxs-lookup"><span data-stu-id="5b18d-108">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="5b18d-109">Typ *Výraz2* není podílet se na hodnotu celého výrazu; typ vrácený při výjimku nedojde je poslední hodnotu v *expression1*.</span><span class="sxs-lookup"><span data-stu-id="5b18d-109">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="5b18d-110">Pokud dojde k výjimce, je vrácena žádná hodnota a toku řízení přenese na další obslužná rutina odpovídající výjimky zásobníkem volání.</span><span class="sxs-lookup"><span data-stu-id="5b18d-110">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="5b18d-111">Pokud je nalezena žádná obslužná rutina výjimky, program se ukončí.</span><span class="sxs-lookup"><span data-stu-id="5b18d-111">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="5b18d-112">Před kód v odpovídající obslužná rutina se spustí nebo ukončí program, kód `finally` větev se spustí.</span><span class="sxs-lookup"><span data-stu-id="5b18d-112">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="5b18d-113">Následující kód ukazuje použití `try...finally` výraz.</span><span class="sxs-lookup"><span data-stu-id="5b18d-113">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="5b18d-114">Výstup do konzoly nástroje je následující.</span><span class="sxs-lookup"><span data-stu-id="5b18d-114">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="5b18d-115">Jak je vidět z výstupu datového proudu se zavřel před vnější výjimka bylo zpracováno a soubor `test.txt` obsahuje text `test1`, která označuje, že vyrovnávací paměti byly vyprázdněny a zapsat na disk, i když přenést výjimka řízení na obslužnou rutinu vnější výjimka.</span><span class="sxs-lookup"><span data-stu-id="5b18d-115">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="5b18d-116">Všimněte si, že `try...with` konstrukce je samostatný konstrukce z `try...finally` vytvořit.</span><span class="sxs-lookup"><span data-stu-id="5b18d-116">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="5b18d-117">Proto pokud kódu vyžaduje, aby obě `with` bloku a `finally` bloku, budete muset vnořit dvě konstrukce, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="5b18d-117">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="5b18d-118">V kontextu výpočetní výrazy, včetně sekvenční výrazy a asynchronní pracovní postupy, **try... finally** výrazy může mít vlastní implementaci.</span><span class="sxs-lookup"><span data-stu-id="5b18d-118">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="5b18d-119">Další informace najdete v tématu [výpočetní výrazy](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="5b18d-119">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="5b18d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b18d-120">See Also</span></span>
[<span data-ttu-id="5b18d-121">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="5b18d-121">Exception Handling</span></span>](index.md)

[<span data-ttu-id="5b18d-122">Výjimky: `try...with` výraz</span><span class="sxs-lookup"><span data-stu-id="5b18d-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
