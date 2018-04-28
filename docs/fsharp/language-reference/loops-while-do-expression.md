---
title: 'Smyčky: Výraz while...do (F#)'
description: V tématu jak při... provést výraz se používá k provádění iterativní provádění (opakování ve smyčce) zadaný testovací podmínku hodnotu true.
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 847f99faab42c8805bd788e42e3f24ad6369ba52
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="d6d28-103">Smyčky: Výraz while...do</span><span class="sxs-lookup"><span data-stu-id="d6d28-103">Loops: while...do Expression</span></span>

<span data-ttu-id="d6d28-104">`while...do` Výraz se používá k provádění iterativní provádění (opakování ve smyčce) zadaný testovací podmínku hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="d6d28-104">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="d6d28-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6d28-105">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="d6d28-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6d28-106">Remarks</span></span>
<span data-ttu-id="d6d28-107">*Testovací výraz* vyhodnotí; Pokud je `true`, *textu výraz* se spustí a testovací výraz vyhodnocen znovu.</span><span class="sxs-lookup"><span data-stu-id="d6d28-107">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="d6d28-108">*Textu výraz* musí mít typ `unit`.</span><span class="sxs-lookup"><span data-stu-id="d6d28-108">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="d6d28-109">Pokud je test výraz `false`, skončení iterací.</span><span class="sxs-lookup"><span data-stu-id="d6d28-109">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="d6d28-110">Následující příklad ukazuje použití `while...do` výraz.</span><span class="sxs-lookup"><span data-stu-id="d6d28-110">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="d6d28-111">Výstup jako předchozí kód je proud náhodná čísla 1 až 20, poslední z nich je 10.</span><span class="sxs-lookup"><span data-stu-id="d6d28-111">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="d6d28-112">Můžete použít `while...do` v pořadí výrazy a další výpočetní výrazy v takovém případě přizpůsobená verze `while...do` použit výraz.</span><span class="sxs-lookup"><span data-stu-id="d6d28-112">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="d6d28-113">Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výpočetní výrazy](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d6d28-113">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="d6d28-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6d28-114">See Also</span></span>
[<span data-ttu-id="d6d28-115">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="d6d28-115">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="d6d28-116">Smyčky: `for...in` výraz</span><span class="sxs-lookup"><span data-stu-id="d6d28-116">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="d6d28-117">Smyčky: `for...to` výraz</span><span class="sxs-lookup"><span data-stu-id="d6d28-117">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
