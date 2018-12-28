---
title: 'Podmíněné výrazy: if... then... else'
description: Další informace o zápisu podmíněné výrazy F# provést různými větvemi kódu.
ms.date: 05/16/2016
ms.openlocfilehash: eade8c20c1b62a2e9a54700550d832798308f368
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614043"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="2fb94-103">Podmíněné výrazy: `if...then...else`</span><span class="sxs-lookup"><span data-stu-id="2fb94-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="2fb94-104">`if...then...else` Výraz spouští různými větvemi kódu a také vyhodnotí na jinou hodnotu v závislosti na logický výraz zadaný.</span><span class="sxs-lookup"><span data-stu-id="2fb94-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="2fb94-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fb94-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="2fb94-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fb94-106">Remarks</span></span>

<span data-ttu-id="2fb94-107">V předchozí syntaxi *expression1* spustí, když logický výraz je vyhodnocen jako `true`; v opačném případě *expression2* běží.</span><span class="sxs-lookup"><span data-stu-id="2fb94-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="2fb94-108">Na rozdíl od v jiných jazycích `if...then...else` konstruktor je výraz, ne příkaz.</span><span class="sxs-lookup"><span data-stu-id="2fb94-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="2fb94-109">To znamená, že vytvoří hodnotu, což je hodnota posledního výrazu ve větvi, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="2fb94-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="2fb94-110">Typy hodnot v jednotlivých větví se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="2fb94-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="2fb94-111">Pokud neexistuje žádné explicitní `else` větev, jeho typ je `unit`.</span><span class="sxs-lookup"><span data-stu-id="2fb94-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="2fb94-112">Proto pokud typ `then` větev je libovolného typu jiného než `unit`, musí existovat `else` větev s vracet hodnotu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="2fb94-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="2fb94-113">Při zřetězení `if...then...else` výrazů společně, můžete použít klíčové slovo `elif` místo `else if`; jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="2fb94-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="2fb94-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="2fb94-114">Example</span></span>

<span data-ttu-id="2fb94-115">Následující příklad ukazuje způsob použití `if...then...else` výrazu.</span><span class="sxs-lookup"><span data-stu-id="2fb94-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="2fb94-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fb94-116">See also</span></span>

- [<span data-ttu-id="2fb94-117">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="2fb94-117">F# Language Reference</span></span>](index.md)