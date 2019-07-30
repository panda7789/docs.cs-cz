---
title: 'Výjimky: Funkce raise'
description: Přečtěte si F# , jak se používá funkce ' vyvolání ' k indikaci, že došlo k chybě nebo mimořádné podmínce.
ms.date: 05/16/2016
ms.openlocfilehash: e0cc8da8310203c537b8081af8a225671bd8c6a3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630285"
---
# <a name="exceptions-the-raise-function"></a><span data-ttu-id="cddcd-103">Výjimky: Funkce raise</span><span class="sxs-lookup"><span data-stu-id="cddcd-103">Exceptions: the raise Function</span></span>

<span data-ttu-id="cddcd-104">`raise` Funkce slouží k označení, že došlo k chybě nebo mimořádné podmínce.</span><span class="sxs-lookup"><span data-stu-id="cddcd-104">The `raise` function is used to indicate that an error or exceptional condition has occurred.</span></span> <span data-ttu-id="cddcd-105">Informace o chybě jsou zachyceny v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="cddcd-105">Information about the error is captured in an exception object.</span></span>

## <a name="syntax"></a><span data-ttu-id="cddcd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cddcd-106">Syntax</span></span>

```fsharp
raise (expression)
```

## <a name="remarks"></a><span data-ttu-id="cddcd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cddcd-107">Remarks</span></span>

<span data-ttu-id="cddcd-108">`raise` Funkce vygeneruje objekt výjimky a zahájí proces odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cddcd-108">The `raise` function generates an exception object and initiates a stack unwinding process.</span></span> <span data-ttu-id="cddcd-109">Proces odvíjení zásobníku je spravován modulem CLR (Common Language Runtime), takže chování tohoto procesu je stejné jako v jakémkoli jiném jazyce .NET.</span><span class="sxs-lookup"><span data-stu-id="cddcd-109">The stack unwinding process is managed by the common language runtime (CLR), so the behavior of this process is the same as it is in any other .NET language.</span></span> <span data-ttu-id="cddcd-110">Proces odvíjení zásobníku je hledání obslužné rutiny výjimky, která odpovídá vygenerované výjimce.</span><span class="sxs-lookup"><span data-stu-id="cddcd-110">The stack unwinding process is a search for an exception handler that matches the generated exception.</span></span> <span data-ttu-id="cddcd-111">Hledání se spustí v aktuálním `try...with` výrazu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="cddcd-111">The search starts in the current `try...with` expression, if there is one.</span></span> <span data-ttu-id="cddcd-112">Každý vzor `with` bloku je zkontrolován v pořadí.</span><span class="sxs-lookup"><span data-stu-id="cddcd-112">Each pattern in the `with` block is checked, in order.</span></span> <span data-ttu-id="cddcd-113">Pokud je nalezena vyhovující obslužná rutina výjimky, je výjimka považována za zpracovanou; v opačném případě je zásobník rozpadl `with` a zablokuje řetěz volání, dokud není nalezena vyhovující obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="cddcd-113">When a matching exception handler is found, the exception is considered handled; otherwise, the stack is unwound and `with` blocks up the call chain are checked until a matching handler is found.</span></span> <span data-ttu-id="cddcd-114">Všechny `finally` bloky, které se vyskytují v řetězu volání, jsou také spuštěny v sekvenci jako odvinutí zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cddcd-114">Any `finally` blocks that are encountered in the call chain are also executed in sequence as the stack unwinds.</span></span>

<span data-ttu-id="cddcd-115">Funkce je ekvivalentem C# v nebo C++ `throw` `raise`</span><span class="sxs-lookup"><span data-stu-id="cddcd-115">The `raise` function is the equivalent of `throw` in C# or C++.</span></span> <span data-ttu-id="cddcd-116">Použijte `reraise` v obslužné rutině catch k šíření stejné výjimky v řetězu volání.</span><span class="sxs-lookup"><span data-stu-id="cddcd-116">Use `reraise` in a catch handler to propagate the same exception up the call chain.</span></span>

<span data-ttu-id="cddcd-117">Následující příklady kódu ilustrují použití `raise` funkce pro vygenerování výjimky.</span><span class="sxs-lookup"><span data-stu-id="cddcd-117">The following code examples illustrate the use of the `raise` function to generate an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5801.fs)]

<span data-ttu-id="cddcd-118">`raise` Funkci lze také použít k vyvolání výjimek rozhraní .NET, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cddcd-118">The `raise` function can also be used to raise .NET exceptions, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5802.fs)]

## <a name="see-also"></a><span data-ttu-id="cddcd-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cddcd-119">See also</span></span>

- [<span data-ttu-id="cddcd-120">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="cddcd-120">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="cddcd-121">Typy výjimek</span><span class="sxs-lookup"><span data-stu-id="cddcd-121">Exception Types</span></span>](exception-types.md)
- [<span data-ttu-id="cddcd-122">Výjimky: `try...with` Výraz</span><span class="sxs-lookup"><span data-stu-id="cddcd-122">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)
- [<span data-ttu-id="cddcd-123">Výjimky: `try...finally` Výraz</span><span class="sxs-lookup"><span data-stu-id="cddcd-123">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
- [<span data-ttu-id="cddcd-124">Výjimky: `failwith` Funkce</span><span class="sxs-lookup"><span data-stu-id="cddcd-124">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)
- [<span data-ttu-id="cddcd-125">Výjimky: `invalidArg` Funkce</span><span class="sxs-lookup"><span data-stu-id="cddcd-125">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)
