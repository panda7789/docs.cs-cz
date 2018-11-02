---
title: 'Výjimky: Funkce raise (F#)'
description: 'Zjistěte, jak "vyvolat" funkce jazyka F # používá k označení, že došlo k chybě nebo výjimečné podmínce.'
ms.date: 05/16/2016
ms.openlocfilehash: 537d274659d29404380bfdd56310ac267372bb98
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43778256"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="104ea-103">Výjimky: Funkce raise</span><span class="sxs-lookup"><span data-stu-id="104ea-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="104ea-104">`raise` Funkce se používá k označení, že došlo k chybě nebo výjimečné podmínce.</span><span class="sxs-lookup"><span data-stu-id="104ea-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="104ea-105">Informace o této chybě je zachycena v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="104ea-105">Information about the error is captured in an exception object.</span></span>

## <a name="syntax"></a><span data-ttu-id="104ea-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="104ea-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="104ea-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="104ea-107">Remarks</span></span>

<span data-ttu-id="104ea-108">`raise` Funkce vytvoří objekt výjimky a zahájí proces odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="104ea-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="104ea-109">Procesu odvíjení zásobníku je spravován modulem common language runtime (CLR), takže chování tohoto procesu je stejný, jako je v kterémkoli jazyce platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="104ea-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="104ea-110">Procesu odvíjení zásobníku je hledání pro obslužnou rutinu výjimky, která odpovídá generované výjimky.</span><span class="sxs-lookup"><span data-stu-id="104ea-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="104ea-111">Hledání se spustí v aktuálním `try...with` výrazu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="104ea-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="104ea-112">Každý vzor v `with` bloku je zaškrtnuto, v pořadí.</span><span class="sxs-lookup"><span data-stu-id="104ea-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="104ea-113">Když je nalezena odpovídající obslužná rutina výjimky, bude výjimka považována zpracovat; v opačném případě je zásobník odvinut a `with` bloky řetězem volání jsou kontrolovány, dokud není nalezena odpovídající obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="104ea-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="104ea-114">Žádné `finally` bloky, které se vyskytují v řetězu volání jsou také provést postupně, protože unwinds zásobníku.</span><span class="sxs-lookup"><span data-stu-id="104ea-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="104ea-115">`raise` Funkce je obdobou `throw` v jazyce C# nebo C++.</span><span class="sxs-lookup"><span data-stu-id="104ea-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="104ea-116">Použití `reraise` v rozšíření stejná výjimka řetězem volání obslužné rutiny catch.</span><span class="sxs-lookup"><span data-stu-id="104ea-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="104ea-117">Následující příklady kódu znázorňují použití `raise` funkce generují výjimku.</span><span class="sxs-lookup"><span data-stu-id="104ea-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="104ea-118">`raise` Funkce také umožňuje vyvolávat výjimky .NET, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="104ea-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a><span data-ttu-id="104ea-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="104ea-119">See also</span></span>

- [<span data-ttu-id="104ea-120">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="104ea-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="104ea-121">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="104ea-121">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="104ea-122">Výjimky: `try...with` výraz</span><span class="sxs-lookup"><span data-stu-id="104ea-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
- [<span data-ttu-id="104ea-123">Výjimky: `try...finally` výraz</span><span class="sxs-lookup"><span data-stu-id="104ea-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
- [<span data-ttu-id="104ea-124">Výjimky: `failwith` – funkce</span><span class="sxs-lookup"><span data-stu-id="104ea-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)
- [<span data-ttu-id="104ea-125">Výjimky: `invalidArg` – funkce</span><span class="sxs-lookup"><span data-stu-id="104ea-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
