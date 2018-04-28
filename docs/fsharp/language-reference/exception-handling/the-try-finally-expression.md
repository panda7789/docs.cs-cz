---
title: 'Výjimky: Výraz try...finally (F#)'
description: "Zjistěte, jak F # ' try... finally' výrazu umožňuje spuštění kódu čištění i v případě, že blok kódu vyvolá výjimku."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 588e4edb4d25c6d25ef103ba724613db997f68d7
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="4d98b-103">Výjimky: Výraz try...finally</span><span class="sxs-lookup"><span data-stu-id="4d98b-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="4d98b-104">`try...finally` Výrazu umožňuje spuštění kódu čištění i v případě, že blok kódu vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="4d98b-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>


## <a name="syntax"></a><span data-ttu-id="4d98b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d98b-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="4d98b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d98b-106">Remarks</span></span>
<span data-ttu-id="4d98b-107">`try...finally` Výraz můžete použít ke spouštění kódu vytvořeného v *Výraz2* v předchozí syntaxi bez ohledu na to, jestli se vygeneruje výjimku během provádění *expression1*.</span><span class="sxs-lookup"><span data-stu-id="4d98b-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="4d98b-108">Typ *Výraz2* není podílet se na hodnotu celého výrazu; typ vrácený při výjimku nedojde je poslední hodnotu v *expression1*.</span><span class="sxs-lookup"><span data-stu-id="4d98b-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="4d98b-109">Pokud dojde k výjimce, je vrácena žádná hodnota a toku řízení přenese na další obslužná rutina odpovídající výjimky zásobníkem volání.</span><span class="sxs-lookup"><span data-stu-id="4d98b-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="4d98b-110">Pokud je nalezena žádná obslužná rutina výjimky, program se ukončí.</span><span class="sxs-lookup"><span data-stu-id="4d98b-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="4d98b-111">Před kód v odpovídající obslužná rutina se spustí nebo ukončí program, kód `finally` větev se spustí.</span><span class="sxs-lookup"><span data-stu-id="4d98b-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="4d98b-112">Následující kód ukazuje použití `try...finally` výraz.</span><span class="sxs-lookup"><span data-stu-id="4d98b-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="4d98b-113">Výstup do konzoly nástroje je následující.</span><span class="sxs-lookup"><span data-stu-id="4d98b-113">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="4d98b-114">Jak je vidět z výstupu datového proudu se zavřel před vnější výjimka bylo zpracováno a soubor `test.txt` obsahuje text `test1`, která označuje, že vyrovnávací paměti byly vyprázdněny a zapsat na disk, i když přenést výjimka řízení na obslužnou rutinu vnější výjimka.</span><span class="sxs-lookup"><span data-stu-id="4d98b-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="4d98b-115">Všimněte si, že `try...with` konstrukce je samostatný konstrukce z `try...finally` vytvořit.</span><span class="sxs-lookup"><span data-stu-id="4d98b-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="4d98b-116">Proto pokud kódu vyžaduje, aby obě `with` bloku a `finally` bloku, budete muset vnořit dvě konstrukce, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="4d98b-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="4d98b-117">V kontextu výpočetní výrazy, včetně sekvenční výrazy a asynchronní pracovní postupy, **try... finally** výrazy může mít vlastní implementaci.</span><span class="sxs-lookup"><span data-stu-id="4d98b-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="4d98b-118">Další informace najdete v tématu [výpočetní výrazy](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4d98b-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="4d98b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d98b-119">See Also</span></span>
[<span data-ttu-id="4d98b-120">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="4d98b-120">Exception Handling</span></span>](index.md)

[<span data-ttu-id="4d98b-121">Výjimky: `try...with` výraz</span><span class="sxs-lookup"><span data-stu-id="4d98b-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
