---
title: Kontrolní výrazy
description: Naučte se používat výraz Assert jako funkci ladění pro testování výrazů v F# programovacím jazyce.
ms.date: 05/16/2016
ms.openlocfilehash: b8b7e9662143b432d650f87515d4af31cced4149
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630035"
---
# <a name="assertions"></a><span data-ttu-id="14750-103">Kontrolní výrazy</span><span class="sxs-lookup"><span data-stu-id="14750-103">Assertions</span></span>

<span data-ttu-id="14750-104">`assert` Výraz je funkce ladění, kterou můžete použít k otestování výrazu.</span><span class="sxs-lookup"><span data-stu-id="14750-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="14750-105">Po selhání v režimu ladění vygeneruje kontrolní výraz dialogové okno systémové chyby.</span><span class="sxs-lookup"><span data-stu-id="14750-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="14750-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14750-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="14750-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14750-107">Remarks</span></span>

<span data-ttu-id="14750-108">Výraz je typu `bool -> unit`. `assert`</span><span class="sxs-lookup"><span data-stu-id="14750-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="14750-109">V předchozí syntaxi *Podmínka* představuje logický výraz, který má být testován.</span><span class="sxs-lookup"><span data-stu-id="14750-109">In the previous syntax, *condition* represents a Boolean expression that is to be tested.</span></span> <span data-ttu-id="14750-110">Pokud se výraz vyhodnotí `true`jako, provádění pokračuje bez ovlivnění.</span><span class="sxs-lookup"><span data-stu-id="14750-110">If the expression evaluates to `true`, execution continues unaffected.</span></span> <span data-ttu-id="14750-111">Pokud se vyhodnotí `false`jako, vygeneruje se dialogové okno systémová chyba.</span><span class="sxs-lookup"><span data-stu-id="14750-111">If it evaluates to `false`, a system error dialog box is generated.</span></span> <span data-ttu-id="14750-112">Dialogové okno chyby obsahuje titulek, který obsahuje výraz řetězce, který **se nezdařil**.</span><span class="sxs-lookup"><span data-stu-id="14750-112">The error dialog box has a caption that contains the string **Assertion Failed**.</span></span> <span data-ttu-id="14750-113">Dialogové okno obsahuje trasování zásobníku, které indikuje, kde došlo k chybě kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="14750-113">The dialog box contains a stack trace that indicates where the assertion failure occurred.</span></span>

<span data-ttu-id="14750-114">Kontrola kontrolního výrazu je povolena pouze při kompilaci v režimu ladění; To znamená, že pokud je `DEBUG` konstanta definována.</span><span class="sxs-lookup"><span data-stu-id="14750-114">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="14750-115">V systému projektu je `DEBUG` konstanta ve výchozím nastavení definována v konfiguraci ladění, ale ne v konfiguraci vydané verze.</span><span class="sxs-lookup"><span data-stu-id="14750-115">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="14750-116">Chyba při selhání kontrolního výrazu nemůže být zachycena pomocí F# zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="14750-116">The assertion failure error cannot be caught by using F# exception handling.</span></span>

> [!NOTE]
> <span data-ttu-id="14750-117">Funkce překládá na <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>. `assert`</span><span class="sxs-lookup"><span data-stu-id="14750-117">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert*?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="14750-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="14750-118">Example</span></span>

<span data-ttu-id="14750-119">Následující příklad kódu ukazuje použití `assert` výrazu.</span><span class="sxs-lookup"><span data-stu-id="14750-119">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="14750-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14750-120">See also</span></span>

- [<span data-ttu-id="14750-121">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="14750-121">F# Language Reference</span></span>](index.md)
