---
title: 'Podmíněné výrazy: if... then...else (F#)'
description: 'Další informace o zápisu podmíněné výrazy v jazyce F # k provedení různých pobočkách kódu.'
ms.date: 05/16/2016
ms.openlocfilehash: a3ca3c20a659ccf5dc432d0a747ff176ec889e9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563130"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="b729d-103">Podmíněné výrazy: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="b729d-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="b729d-104">`if...then...else` Výraz spouští různé větví kódu a také vyhodnocuje na jinou hodnotu, v závislosti na logický výraz zadaný.</span><span class="sxs-lookup"><span data-stu-id="b729d-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="b729d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b729d-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="b729d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b729d-106">Remarks</span></span>
<span data-ttu-id="b729d-107">V předchozích syntaxi *expression1* se spustí v případě, že se vyhodnocuje logický výraz `true`, jinak hodnota *Výraz2* běží.</span><span class="sxs-lookup"><span data-stu-id="b729d-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="b729d-108">Na rozdíl od v dalších jazycích `if...then...else` konstrukce je výraz, nikoli příkaz.</span><span class="sxs-lookup"><span data-stu-id="b729d-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="b729d-109">To znamená, že vyvolá hodnotu, která je hodnota poslední výrazu v větve, které provádí.</span><span class="sxs-lookup"><span data-stu-id="b729d-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="b729d-110">Typy hodnot vytvořil v každé větve se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="b729d-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="b729d-111">Pokud neexistuje žádné explicitní `else` větve, je její typ `unit`.</span><span class="sxs-lookup"><span data-stu-id="b729d-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="b729d-112">Proto pokud typ `then` větve je žádný typ, než `unit`, musí být `else` firemní pobočky s stejné návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="b729d-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="b729d-113">Když řetězení `if...then...else` výrazy společně, můžete použít klíčové slovo `elif` místo `else if`; jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="b729d-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="b729d-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="b729d-114">Example</span></span>
<span data-ttu-id="b729d-115">Následující příklad ukazuje, jak používat `if...then...else` výraz.</span><span class="sxs-lookup"><span data-stu-id="b729d-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="b729d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b729d-116">See Also</span></span>
[<span data-ttu-id="b729d-117">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="b729d-117">F# Language Reference</span></span>](index.md)

