---
title: "Podmíněné výrazy: if... then...else (F#)"
description: "Další informace o zápisu podmíněné výrazy v jazyce F # k provedení různých pobočkách kódu."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 16e1871c-4d4d-4691-9ab2-bd2c6f65589a
ms.openlocfilehash: 3531a112eb53657d5e9102d5e5f3be988360b76e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="d53d8-104">Podmíněné výrazy:`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="d53d8-104">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="d53d8-105">`if...then...else` Výraz spouští různé větví kódu a také vyhodnocuje na jinou hodnotu, v závislosti na logický výraz zadaný.</span><span class="sxs-lookup"><span data-stu-id="d53d8-105">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>


## <a name="syntax"></a><span data-ttu-id="d53d8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d53d8-106">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="d53d8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d53d8-107">Remarks</span></span>
<span data-ttu-id="d53d8-108">V předchozích syntaxi *expression1* se spustí v případě, že se vyhodnocuje logický výraz `true`, jinak hodnota *Výraz2* běží.</span><span class="sxs-lookup"><span data-stu-id="d53d8-108">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="d53d8-109">Na rozdíl od v dalších jazycích `if...then...else` konstrukce je výraz, nikoli příkaz.</span><span class="sxs-lookup"><span data-stu-id="d53d8-109">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="d53d8-110">To znamená, že vyvolá hodnotu, která je hodnota poslední výrazu v větve, které provádí.</span><span class="sxs-lookup"><span data-stu-id="d53d8-110">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="d53d8-111">Typy hodnot vytvořil v každé větve se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="d53d8-111">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="d53d8-112">Pokud neexistuje žádné explicitní `else` větve, je její typ `unit`.</span><span class="sxs-lookup"><span data-stu-id="d53d8-112">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="d53d8-113">Proto pokud typ `then` větve je žádný typ, než `unit`, musí být `else` firemní pobočky s stejné návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="d53d8-113">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="d53d8-114">Když řetězení `if...then...else` výrazy společně, můžete použít klíčové slovo `elif` místo `else if`; jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="d53d8-114">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="d53d8-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d53d8-115">Example</span></span>
<span data-ttu-id="d53d8-116">Následující příklad ukazuje, jak používat `if...then...else` výraz.</span><span class="sxs-lookup"><span data-stu-id="d53d8-116">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
John
910 is less than 20
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="d53d8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d53d8-117">See Also</span></span>
[<span data-ttu-id="d53d8-118">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="d53d8-118">F# Language Reference</span></span>](index.md)

