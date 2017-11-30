---
title: "Logické operátory (F#)"
description: "Další informace o logické operátory, které jsou k dispozici v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="boolean-operators"></a><span data-ttu-id="dca6d-104">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="dca6d-104">Boolean Operators</span></span>

<span data-ttu-id="dca6d-105">Toto téma popisuje podporu logické operátory v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="dca6d-105">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="dca6d-106">Souhrn logické operátory</span><span class="sxs-lookup"><span data-stu-id="dca6d-106">Summary of Boolean Operators</span></span>
<span data-ttu-id="dca6d-107">Následující tabulka shrnuje logické operátory, které jsou k dispozici v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="dca6d-107">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="dca6d-108">Je jediným typem podporuje tyto operátory `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="dca6d-108">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="dca6d-109">Operátor</span><span class="sxs-lookup"><span data-stu-id="dca6d-109">Operator</span></span>|<span data-ttu-id="dca6d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="dca6d-110">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="dca6d-111">Logická negace</span><span class="sxs-lookup"><span data-stu-id="dca6d-111">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="dca6d-112">Logická hodnota nebo</span><span class="sxs-lookup"><span data-stu-id="dca6d-112">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="dca6d-113">Logická hodnota a</span><span class="sxs-lookup"><span data-stu-id="dca6d-113">Boolean AND</span></span>|

<span data-ttu-id="dca6d-114">Logická hodnota a a nebo operátory provést *krátká smyčka – vyhodnocení*, to znamená, že vyhodnocování výrazu na pravé straně operátoru jenom v případě, že je nutné určit celkový výsledek výrazu.</span><span class="sxs-lookup"><span data-stu-id="dca6d-114">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="dca6d-115">Druhý výraz `&&` operátor vyhodnotí pouze v případě, že první vyhodnocen jako `true`; druhý výraz `||` operátor vyhodnotí pouze v případě, že první vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="dca6d-115">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="dca6d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="dca6d-116">See Also</span></span>
[<span data-ttu-id="dca6d-117">Bitové operátory</span><span class="sxs-lookup"><span data-stu-id="dca6d-117">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="dca6d-118">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="dca6d-118">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="dca6d-119">Operátor referenční dokumentace symbolů a</span><span class="sxs-lookup"><span data-stu-id="dca6d-119">Symbol and Operator Reference</span></span>](index.md)
