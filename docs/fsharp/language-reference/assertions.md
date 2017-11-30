---
title: "Kontrolní výrazy (F#)"
description: "Další informace o použití výrazu 'assert' jako ladění funkci pro testování výrazy v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2badaad7-f086-47e7-99c1-91f35117da83
ms.openlocfilehash: 56891769602afaa765ebfe7e7822a179c7a22968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="assertions"></a><span data-ttu-id="3bcf5-104">Kontrolní výrazy</span><span class="sxs-lookup"><span data-stu-id="3bcf5-104">Assertions</span></span>

<span data-ttu-id="3bcf5-105">`assert` Výrazu je ladění funkce, která můžete použít k otestování výrazu.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-105">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="3bcf5-106">Kontrolní výrazy při selhání v režimu ladění, generuje dialogové okno chyby systému.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-106">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="3bcf5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bcf5-107">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="3bcf5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3bcf5-108">Remarks</span></span>

<span data-ttu-id="3bcf5-109">`assert` Výraz má typ `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-109">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="3bcf5-110">V předchozích syntaxi *podmínku* představuje logický výraz, který má být testována.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-110">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="3bcf5-111">Pokud je výsledkem výrazu `true`, pokračuje v provádění neovlivní.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-111">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="3bcf5-112">Pokud je vyhodnocen jako `false`, generuje se dialogové okno chyby systému.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-112">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="3bcf5-113">Dialogové okno chyby má popisek, který obsahuje řetězec **kontrolní výraz**.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-113">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="3bcf5-114">Dialogové okno obsahuje trasování zásobníku, která určuje, kde došlo k selhání kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-114">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="3bcf5-115">Kontrola kontrolní výraz je povoleno pouze v případě, že při kompilaci v režimu ladění; To znamená pokud konstanta `DEBUG` je definována.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-115">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="3bcf5-116">V systému projektu, ve výchozím nastavení `DEBUG` konstanta je definována v konfiguraci ladění ale není v rámci konfigurace verze.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-116">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="3bcf5-117">Chyba předpokladu selhání nemůže být zachycena pomocí zpracování výjimek F #.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-117">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="3bcf5-118">`assert` Funkce přeloží na <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-118">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="3bcf5-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bcf5-119">Example</span></span>

<span data-ttu-id="3bcf5-120">Následující příklad kódu ukazuje použití `assert` výraz.</span><span class="sxs-lookup"><span data-stu-id="3bcf5-120">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]
    
## <a name="see-also"></a><span data-ttu-id="3bcf5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bcf5-121">See Also</span></span>

[<span data-ttu-id="3bcf5-122">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="3bcf5-122">F# Language Reference</span></span>](index.md)
