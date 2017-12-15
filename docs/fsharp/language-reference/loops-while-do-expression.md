---
title: "Smyčky: Výraz while...do (F#)"
description: "V tématu jak při... provést výraz se používá k provádění iterativní provádění (opakování ve smyčce) zadaný testovací podmínku hodnotu true."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 5f10fda84a5e748856eb7b2c63ad46cc1fba44bb
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="loops-whiledo-expression"></a><span data-ttu-id="e7459-104">Smyčky: Výraz while...do</span><span class="sxs-lookup"><span data-stu-id="e7459-104">Loops: while...do Expression</span></span>

<span data-ttu-id="e7459-105">`while...do` Výraz se používá k provádění iterativní provádění (opakování ve smyčce) zadaný testovací podmínku hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="e7459-105">The `while...do` expression is used to perform iterative execution (looping) while a specified test condition is true.</span></span>


## <a name="syntax"></a><span data-ttu-id="e7459-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7459-106">Syntax</span></span>

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="e7459-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7459-107">Remarks</span></span>
<span data-ttu-id="e7459-108">*Testovací výraz* vyhodnotí; Pokud je `true`, *textu výraz* se spustí a testovací výraz vyhodnocen znovu.</span><span class="sxs-lookup"><span data-stu-id="e7459-108">The *test-expression* is evaluated; if it is `true`, the *body-expression* is executed and the test expression is evaluated again.</span></span> <span data-ttu-id="e7459-109">*Textu výraz* musí mít typ `unit`.</span><span class="sxs-lookup"><span data-stu-id="e7459-109">The *body-expression* must have type `unit`.</span></span> <span data-ttu-id="e7459-110">Pokud je test výraz `false`, skončení iterací.</span><span class="sxs-lookup"><span data-stu-id="e7459-110">If the test expression is `false`, the iteration ends.</span></span>

<span data-ttu-id="e7459-111">Následující příklad ukazuje použití `while...do` výraz.</span><span class="sxs-lookup"><span data-stu-id="e7459-111">The following example illustrates the use of the `while...do` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

<span data-ttu-id="e7459-112">Výstup jako předchozí kód je proud náhodná čísla 1 až 20, poslední z nich je 10.</span><span class="sxs-lookup"><span data-stu-id="e7459-112">The output of the previous code is a stream of random numbers between 1 and 20, the last of which is 10.</span></span>

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
<span data-ttu-id="e7459-113">Můžete použít `while...do` v pořadí výrazy a další výpočetní výrazy v takovém případě přizpůsobená verze `while...do` použit výraz.</span><span class="sxs-lookup"><span data-stu-id="e7459-113">You can use `while...do` in sequence expressions and other computation expressions, in which case a customized version of the `while...do` expression is used.</span></span> <span data-ttu-id="e7459-114">Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výpočetní výrazy](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e7459-114">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="e7459-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7459-115">See Also</span></span>
[<span data-ttu-id="e7459-116">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="e7459-116">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="e7459-117">Smyčky: `for...in` výraz</span><span class="sxs-lookup"><span data-stu-id="e7459-117">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)

[<span data-ttu-id="e7459-118">Smyčky: `for...to` výraz</span><span class="sxs-lookup"><span data-stu-id="e7459-118">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
