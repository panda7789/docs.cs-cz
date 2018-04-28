---
title: Kontrolní výrazy (F#)
description: "Další informace o použití výrazu 'assert' jako ladění funkci pro testování výrazy v programovací jazyk F #."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 195b4a34977a63d92559003b5cd0bb89490a1e7a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="assertions"></a><span data-ttu-id="78477-103">Kontrolní výrazy</span><span class="sxs-lookup"><span data-stu-id="78477-103">Assertions</span></span>

<span data-ttu-id="78477-104">`assert` Výrazu je ladění funkce, která můžete použít k otestování výrazu.</span><span class="sxs-lookup"><span data-stu-id="78477-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="78477-105">Kontrolní výrazy při selhání v režimu ladění, generuje dialogové okno chyby systému.</span><span class="sxs-lookup"><span data-stu-id="78477-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="78477-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78477-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="78477-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78477-107">Remarks</span></span>

<span data-ttu-id="78477-108">`assert` Výraz má typ `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="78477-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="78477-109">V předchozích syntaxi *podmínku* představuje logický výraz, který má být testována.</span><span class="sxs-lookup"><span data-stu-id="78477-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="78477-110">Pokud je výsledkem výrazu `true`, pokračuje v provádění neovlivní.</span><span class="sxs-lookup"><span data-stu-id="78477-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="78477-111">Pokud je vyhodnocen jako `false`, generuje se dialogové okno chyby systému.</span><span class="sxs-lookup"><span data-stu-id="78477-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="78477-112">Dialogové okno chyby má popisek, který obsahuje řetězec **kontrolní výraz**.</span><span class="sxs-lookup"><span data-stu-id="78477-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="78477-113">Dialogové okno obsahuje trasování zásobníku, která určuje, kde došlo k selhání kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="78477-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="78477-114">Kontrola kontrolní výraz je povoleno pouze v případě, že při kompilaci v režimu ladění; To znamená pokud konstanta `DEBUG` je definována.</span><span class="sxs-lookup"><span data-stu-id="78477-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="78477-115">V systému projektu, ve výchozím nastavení `DEBUG` konstanta je definována v konfiguraci ladění ale není v rámci konfigurace verze.</span><span class="sxs-lookup"><span data-stu-id="78477-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="78477-116">Chyba předpokladu selhání nemůže být zachycena pomocí zpracování výjimek F #.</span><span class="sxs-lookup"><span data-stu-id="78477-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="78477-117">`assert` Funkce přeloží na <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="78477-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="78477-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="78477-118">Example</span></span>

<span data-ttu-id="78477-119">Následující příklad kódu ukazuje použití `assert` výraz.</span><span class="sxs-lookup"><span data-stu-id="78477-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a><span data-ttu-id="78477-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="78477-120">See Also</span></span>

[<span data-ttu-id="78477-121">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="78477-121">F# Language Reference</span></span>](index.md)
