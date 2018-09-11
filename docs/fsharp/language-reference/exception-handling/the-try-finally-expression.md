---
title: 'Výjimky: Výraz try...finally (F#)'
description: "Zjistěte, jak F # ' try... finally \"výraz umožňuje spuštění kódu čištění i v případě, že blok kódu vyvolá výjimku."
ms.date: 05/16/2016
ms.openlocfilehash: 546a6b0619de6f51044600dc1ead73c6d5211299
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275142"
---
# <a name="exceptions-the-tryfinally-expression"></a><span data-ttu-id="09bd2-103">Výjimky: Výraz try...finally</span><span class="sxs-lookup"><span data-stu-id="09bd2-103">Exceptions: The try...finally Expression</span></span>

<span data-ttu-id="09bd2-104">`try...finally` Výraz umožňuje spuštění kódu čištění i v případě, že blok kódu vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="09bd2-104">The `try...finally` expression enables you to execute clean-up code even if a block of code throws an exception.</span></span>

## <a name="syntax"></a><span data-ttu-id="09bd2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09bd2-105">Syntax</span></span>

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a><span data-ttu-id="09bd2-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09bd2-106">Remarks</span></span>

<span data-ttu-id="09bd2-107">`try...finally` Výraz lze použít ke spouštění kódu vytvořeného v *expression2* v předchozí syntaxi bez ohledu na to, zda je vygenerována výjimka při provádění *expression1*.</span><span class="sxs-lookup"><span data-stu-id="09bd2-107">The `try...finally` expression can be used to execute the code in *expression2* in the preceding syntax regardless of whether an exception is generated during the execution of *expression1*.</span></span>

<span data-ttu-id="09bd2-108">Typ *expression2* není přispívat k hodnotě celý výraz; typ vrácený při výjimce nedochází je poslední hodnotu v *expression1*.</span><span class="sxs-lookup"><span data-stu-id="09bd2-108">The type of *expression2* does not contribute to the value of the whole expression; the type returned when an exception does not occur is the last value in *expression1*.</span></span> <span data-ttu-id="09bd2-109">Pokud dojde k výjimce, není vrácena žádná hodnota a tok řízení přenosů na další odpovídající obslužnou rutinu výjimky v zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="09bd2-109">When an exception does occur, no value is returned and the flow of control transfers to the next matching exception handler up the call stack.</span></span> <span data-ttu-id="09bd2-110">Pokud se nenajde žádná obslužná rutina výjimky, program se ukončí.</span><span class="sxs-lookup"><span data-stu-id="09bd2-110">If no exception handler is found, the program terminates.</span></span> <span data-ttu-id="09bd2-111">Předtím, než kód v odpovídající obslužná rutina se spustí nebo ukončí program, kód `finally` větev provést.</span><span class="sxs-lookup"><span data-stu-id="09bd2-111">Before the code in a matching handler is executed or the program terminates, the code in the `finally` branch is executed.</span></span>

<span data-ttu-id="09bd2-112">Následující kód demonstruje použití `try...finally` výrazu.</span><span class="sxs-lookup"><span data-stu-id="09bd2-112">The following code demonstrates the use of the `try...finally` expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

<span data-ttu-id="09bd2-113">Výstup do konzoly nástroje je následující.</span><span class="sxs-lookup"><span data-stu-id="09bd2-113">The output to the console is as follows.</span></span>

```
Closing stream
Exception handled.
```

<span data-ttu-id="09bd2-114">Jak je vidět z výstupu datového proudu se zavřel před vnější výjimka byla zpracována a soubor `test.txt` obsahuje text `test1`, která označuje, že byly vyrovnávací paměti vyprázdněných a zapíšou na disk i v případě, že přenést výjimku řízení na obslužnou rutinu vnější výjimky.</span><span class="sxs-lookup"><span data-stu-id="09bd2-114">As you can see from the output, the stream was closed before the outer exception was handled, and the file `test.txt` contains the text `test1`, which indicates that the buffers were flushed and written to disk even though the exception transferred control to the outer exception handler.</span></span>

<span data-ttu-id="09bd2-115">Všimněte si, že `try...with` konstruktor je samostatnou konstrukci z `try...finally` vytvořit.</span><span class="sxs-lookup"><span data-stu-id="09bd2-115">Note that the `try...with` construct is a separate construct from the `try...finally` construct.</span></span> <span data-ttu-id="09bd2-116">Proto pokud váš kód vyžaduje obě `with` bloku a `finally` bloku, budete muset vnořit dvě konstrukce, jako v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="09bd2-116">Therefore, if your code requires both a `with` block and a `finally` block, you have to nest the two constructs, as in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

<span data-ttu-id="09bd2-117">V rámci výrazech výpočtu, včetně výrazech pořadí a asynchronní pracovní postupy **try... finally** výrazy mohou mít vlastní implementaci.</span><span class="sxs-lookup"><span data-stu-id="09bd2-117">In the context of computation expressions, including sequence expressions and asynchronous workflows, **try...finally** expressions can have a custom implementation.</span></span> <span data-ttu-id="09bd2-118">Další informace najdete v tématu [výrazech výpočtu](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="09bd2-118">For more information, see [Computation Expressions](../computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="09bd2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09bd2-119">See also</span></span>

- [<span data-ttu-id="09bd2-120">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="09bd2-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="09bd2-121">Výjimky: `try...with` výraz</span><span class="sxs-lookup"><span data-stu-id="09bd2-121">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
