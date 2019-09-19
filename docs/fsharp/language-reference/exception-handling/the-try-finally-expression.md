---
title: 'Výjimky: Výraz try...finally'
description: Podívejte se, F# jak se "Try... finally ' Expression umožňuje spustit čistý kód, i když blok kódu vyvolá výjimku.
ms.date: 05/16/2016
ms.openlocfilehash: 0ddb64ac13b307404864ec5b54f26fd8a7a3d7d8
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082996"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="4db76-103">Výjimky: Výraz try...finally</span><span class="sxs-lookup"><span data-stu-id="4db76-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="4db76-104">`try...finally` Výraz umožňuje spustit čistý kód i v případě, že blok kódu vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="4db76-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="4db76-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4db76-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="4db76-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4db76-106">Remarks</span></span>

<span data-ttu-id="4db76-107">Výraz lze použít ke spuštění kódu v příkazu *Výraz2* v předchozí syntaxi bez ohledu na to, zda je výjimka generována během provádění *Výraz1.* `try...finally`</span><span class="sxs-lookup"><span data-stu-id="4db76-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="4db76-108">Typ *Výraz2* nepřispívá k hodnotě celého výrazu; typ vrácený při výskytu výjimky je poslední hodnota v *Výraz1*.</span><span class="sxs-lookup"><span data-stu-id="4db76-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="4db76-109">Pokud dojde k výjimce, není vrácena žádná hodnota a tok řízení přenáší do další shodné výjimky obslužné rutiny v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="4db76-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="4db76-110">Pokud není nalezena žádná obslužná rutina výjimky, program skončí.</span><span class="sxs-lookup"><span data-stu-id="4db76-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="4db76-111">Předtím, než je proveden kód v rámci vyhovující obslužné rutiny nebo program skončí, je spuštěn kód `finally` ve větvi.</span><span class="sxs-lookup"><span data-stu-id="4db76-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="4db76-112">Následující kód demonstruje použití `try...finally` výrazu.</span><span class="sxs-lookup"><span data-stu-id="4db76-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="4db76-113">Výstup do konzoly je následující.</span><span class="sxs-lookup"><span data-stu-id="4db76-113">The output to the console is as follows.</span></span>

```console
Closing stream
Exception handled.
```

<span data-ttu-id="4db76-114">Jak vidíte z výstupu, datový proud byl ukončen před tím, než byla zpracována vnější výjimka, a soubor `test.txt` obsahuje text `test1`, který označuje, že byly vyrovnávací paměti vyprázdněny a zapsány na disk, i když byla výjimka převedena. řízení vnější obslužné rutiny výjimky.</span><span class="sxs-lookup"><span data-stu-id="4db76-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="4db76-115">Všimněte si, `try...with` že konstrukce je samostatná konstrukce `try...finally` ze konstrukce.</span><span class="sxs-lookup"><span data-stu-id="4db76-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="4db76-116">Proto pokud váš kód vyžaduje `with` blok `finally` i blok, je nutné vnořit dvě konstrukce, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="4db76-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="4db76-117">V kontextu výrazů výpočtu, včetně sekvenčních výrazů a asynchronních pracovních postupů, **zkuste... výrazy finally** mohou mít vlastní implementaci.</span><span class="sxs-lookup"><span data-stu-id="4db76-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="4db76-118">Další informace najdete v tématu [výrazy výpočtu](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4db76-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4db76-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4db76-119">See also</span></span>

- [<span data-ttu-id="4db76-120">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="4db76-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="4db76-121">Výjimky: `try...with` Výraz</span><span class="sxs-lookup"><span data-stu-id="4db76-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
