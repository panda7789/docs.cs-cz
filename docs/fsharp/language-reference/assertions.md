---
title: Kontrolní výrazy
description: Naučte se používat výraz Assert jako funkci ladění pro testování výrazů v F# programovacím jazyce.
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799071"
---
# <a name="assertions"></a><span data-ttu-id="f3f54-103">Kontrolní výrazy</span><span class="sxs-lookup"><span data-stu-id="f3f54-103">Assertions</span></span>

<span data-ttu-id="f3f54-104">Výraz `assert` je funkce ladění, kterou můžete použít k otestování výrazu.</span><span class="sxs-lookup"><span data-stu-id="f3f54-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="f3f54-105">Po selhání v režimu ladění vygeneruje kontrolní výraz dialogové okno systémové chyby.</span><span class="sxs-lookup"><span data-stu-id="f3f54-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3f54-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3f54-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="f3f54-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3f54-107">Remarks</span></span>

<span data-ttu-id="f3f54-108">Výraz `assert` je typu `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="f3f54-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="f3f54-109">Funkce `assert` překládá na <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3f54-109">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3f54-110">To znamená, že jeho chování je stejné jako volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> přímo.</span><span class="sxs-lookup"><span data-stu-id="f3f54-110">This means its behavior is identical to having called <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="f3f54-111">Kontrola kontrolního výrazu je povolena pouze při kompilaci v režimu ladění; To znamená, pokud je definována konstanta `DEBUG`.</span><span class="sxs-lookup"><span data-stu-id="f3f54-111">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="f3f54-112">V systém projektu je ve výchozím nastavení konstanta `DEBUG` definována v konfiguraci ladění, ale ne v konfiguraci vydané verze.</span><span class="sxs-lookup"><span data-stu-id="f3f54-112">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="f3f54-113">Chyba při selhání kontrolního výrazu nemůže být zachycena pomocí F# zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="f3f54-113">The assertion failure error cannot be caught by using F# exception handling.</span></span>

## <a name="example"></a><span data-ttu-id="f3f54-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3f54-114">Example</span></span>

<span data-ttu-id="f3f54-115">Následující příklad kódu ukazuje použití výrazu `assert`.</span><span class="sxs-lookup"><span data-stu-id="f3f54-115">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="f3f54-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3f54-116">See also</span></span>

- [<span data-ttu-id="f3f54-117">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="f3f54-117">F# Language Reference</span></span>](index.md)
