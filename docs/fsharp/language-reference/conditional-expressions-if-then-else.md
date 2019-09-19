---
title: 'Podmíněné výrazy: if... pak... ostatních'
description: Naučte se psát podmíněné výrazy v F# pro spouštění různých větví kódu.
ms.date: 05/16/2016
ms.openlocfilehash: d9763f37cd9170c42e968282b54a3ce925e92591
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083023"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="dd86f-103">Podmíněné výrazy:`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="dd86f-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="dd86f-104">`if...then...else` Výraz spustí různé větve kódu a také se vyhodnotí na jinou hodnotu v závislosti na daném logickém výrazu.</span><span class="sxs-lookup"><span data-stu-id="dd86f-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="dd86f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd86f-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="dd86f-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd86f-106">Remarks</span></span>

<span data-ttu-id="dd86f-107">V předchozí syntaxi je *Výraz1* spuštěna při vyhodnocování logického výrazu. v `true`opačném případě je možné spustit *Výraz2* .</span><span class="sxs-lookup"><span data-stu-id="dd86f-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="dd86f-108">Na `if...then...else` rozdíl od jiných jazyků konstrukce je výraz, nikoli příkaz.</span><span class="sxs-lookup"><span data-stu-id="dd86f-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="dd86f-109">To znamená, že vytvoří hodnotu, což je hodnota posledního výrazu ve větvi, která se spustí.</span><span class="sxs-lookup"><span data-stu-id="dd86f-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="dd86f-110">Typy hodnot vytvořených v každé větvi se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="dd86f-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="dd86f-111">Pokud není k dispozici `else` žádná explicitní větev, je `unit`její typ.</span><span class="sxs-lookup"><span data-stu-id="dd86f-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="dd86f-112">Proto pokud je typ `then` větve libovolný typ jiný než `unit` `else` , musí existovat větev se stejným návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="dd86f-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="dd86f-113">Při zřetězení `if...then...else` výrazů můžete místo `else if`použít klíčové slovo `elif` , které je ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="dd86f-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="dd86f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd86f-114">Example</span></span>

<span data-ttu-id="dd86f-115">Následující příklad ukazuje, jak použít `if...then...else` výraz.</span><span class="sxs-lookup"><span data-stu-id="dd86f-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```console
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="dd86f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd86f-116">See also</span></span>

- [<span data-ttu-id="dd86f-117">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="dd86f-117">F# Language Reference</span></span>](index.md)
