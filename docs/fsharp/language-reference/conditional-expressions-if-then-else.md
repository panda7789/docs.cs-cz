---
title: 'Podmíněné výrazy: if... then...else (F#)'
description: 'Další informace o zápisu podmíněné výrazy v jazyce F # ke spuštění různými větvemi kódu.'
ms.date: 05/16/2016
ms.openlocfilehash: 10e4224bef772f00520cf5a0fff2f2920147c2fc
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745193"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="5f577-103">Podmíněné výrazy: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="5f577-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="5f577-104">`if...then...else` Výraz spouští různými větvemi kódu a také vyhodnotí na jinou hodnotu v závislosti na logický výraz zadaný.</span><span class="sxs-lookup"><span data-stu-id="5f577-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f577-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f577-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="5f577-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f577-106">Remarks</span></span>

<span data-ttu-id="5f577-107">V předchozí syntaxi *expression1* spustí, když logický výraz je vyhodnocen jako `true`; v opačném případě *expression2* běží.</span><span class="sxs-lookup"><span data-stu-id="5f577-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="5f577-108">Na rozdíl od v jiných jazycích `if...then...else` konstruktor je výraz, ne příkaz.</span><span class="sxs-lookup"><span data-stu-id="5f577-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="5f577-109">To znamená, že vytvoří hodnotu, což je hodnota posledního výrazu ve větvi, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="5f577-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="5f577-110">Typy hodnot v jednotlivých větví se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="5f577-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="5f577-111">Pokud neexistuje žádné explicitní `else` větev, jeho typ je `unit`.</span><span class="sxs-lookup"><span data-stu-id="5f577-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="5f577-112">Proto pokud typ `then` větev je libovolného typu jiného než `unit`, musí existovat `else` větev s vracet hodnotu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="5f577-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="5f577-113">Při zřetězení `if...then...else` výrazů společně, můžete použít klíčové slovo `elif` místo `else if`; jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="5f577-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="5f577-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f577-114">Example</span></span>

<span data-ttu-id="5f577-115">Následující příklad ukazuje způsob použití `if...then...else` výrazu.</span><span class="sxs-lookup"><span data-stu-id="5f577-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="5f577-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f577-116">See also</span></span>

- [<span data-ttu-id="5f577-117">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="5f577-117">F# Language Reference</span></span>](index.md)
