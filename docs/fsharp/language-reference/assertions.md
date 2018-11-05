---
title: Kontrolní výrazy (F#)
description: Zjistěte, jak použít výraz "výraz" jako funkce ladění pro testování výrazů v programovacím jazyce F#.
ms.date: 05/16/2016
ms.openlocfilehash: 85b1e839bfd19bada48b7f1821d15ddd8fa77754
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "48842473"
---
# <a name="assertions"></a><span data-ttu-id="125bf-103">Kontrolní výrazy</span><span class="sxs-lookup"><span data-stu-id="125bf-103">Assertions</span></span>

<span data-ttu-id="125bf-104">`assert` Výrazu je funkce, ladění, která slouží k otestování výrazu.</span><span class="sxs-lookup"><span data-stu-id="125bf-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="125bf-105">Po selhání v režimu ladění generuje kontrolní výraz dialogové okno chyby systému.</span><span class="sxs-lookup"><span data-stu-id="125bf-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="125bf-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="125bf-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="125bf-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="125bf-107">Remarks</span></span>

<span data-ttu-id="125bf-108">`assert` Výraz má typ `bool -> unit`.</span><span class="sxs-lookup"><span data-stu-id="125bf-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="125bf-109">V předchozí syntaxi *podmínku* představuje logický výraz, který se má testovat.</span><span class="sxs-lookup"><span data-stu-id="125bf-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="125bf-110">Pokud je výraz vyhodnocen `true`, provádění pokračuje to neovlivní.</span><span class="sxs-lookup"><span data-stu-id="125bf-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="125bf-111">Pokud je vyhodnocen jako `false`, je vygenerována chyba dialogové okno systému.</span><span class="sxs-lookup"><span data-stu-id="125bf-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="125bf-112">Dialog s chybou má popisek, který obsahuje řetězec **chyba kontrolního výrazu**.</span><span class="sxs-lookup"><span data-stu-id="125bf-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="125bf-113">Dialogové okno obsahuje trasování zásobníku, která určuje, kde došlo k selhání kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="125bf-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="125bf-114">Kontrolní výraz je povolená kontrola jenom při kompilaci v režimu ladění. To znamená pokud konstanty `DEBUG` je definována.</span><span class="sxs-lookup"><span data-stu-id="125bf-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="125bf-115">V systému projektu, ve výchozím nastavení `DEBUG` – konstanta je definován v konfiguraci ladění, ale ne v konfiguraci vydané verze.</span><span class="sxs-lookup"><span data-stu-id="125bf-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="125bf-116">Chyba kontrolního výrazu nejde zachytit pomocí zpracování výjimek v F#.</span><span class="sxs-lookup"><span data-stu-id="125bf-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

>[!NOTE]
<span data-ttu-id="125bf-117">`assert` Funkce se překládá na <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="125bf-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="125bf-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="125bf-118">Example</span></span>

<span data-ttu-id="125bf-119">Následující příklad kódu ukazuje použití `assert` výrazu.</span><span class="sxs-lookup"><span data-stu-id="125bf-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="125bf-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="125bf-120">See also</span></span>

- [<span data-ttu-id="125bf-121">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="125bf-121">F# Language Reference</span></span>](index.md)
