---
title: Logické operátory (F#)
description: 'Další informace o logické operátory, které jsou k dispozici v programovací jazyk F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0b11b5133b02b6f507c7886b2fbaebf30abf46cb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="boolean-operators"></a><span data-ttu-id="9c101-103">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="9c101-103">Boolean Operators</span></span>

<span data-ttu-id="9c101-104">Toto téma popisuje podporu logické operátory v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="9c101-104">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="9c101-105">Souhrn logické operátory</span><span class="sxs-lookup"><span data-stu-id="9c101-105">Summary of Boolean Operators</span></span>
<span data-ttu-id="9c101-106">Následující tabulka shrnuje logické operátory, které jsou k dispozici v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="9c101-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="9c101-107">Je jediným typem podporuje tyto operátory `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="9c101-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="9c101-108">Operátor</span><span class="sxs-lookup"><span data-stu-id="9c101-108">Operator</span></span>|<span data-ttu-id="9c101-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9c101-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="9c101-110">Logická negace</span><span class="sxs-lookup"><span data-stu-id="9c101-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="9c101-111">Logická hodnota nebo</span><span class="sxs-lookup"><span data-stu-id="9c101-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="9c101-112">Logická hodnota a</span><span class="sxs-lookup"><span data-stu-id="9c101-112">Boolean AND</span></span>|

<span data-ttu-id="9c101-113">Logická hodnota a a nebo operátory provést *krátká smyčka – vyhodnocení*, to znamená, že vyhodnocování výrazu na pravé straně operátoru jenom v případě, že je nutné určit celkový výsledek výrazu.</span><span class="sxs-lookup"><span data-stu-id="9c101-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="9c101-114">Druhý výraz `&&` operátor vyhodnotí pouze v případě, že první vyhodnocen jako `true`; druhý výraz `||` operátor vyhodnotí pouze v případě, že první vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="9c101-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c101-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c101-115">See Also</span></span>
[<span data-ttu-id="9c101-116">Bitové operátory</span><span class="sxs-lookup"><span data-stu-id="9c101-116">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="9c101-117">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="9c101-117">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="9c101-118">Referenční dokumentace symbolů a operátorů</span><span class="sxs-lookup"><span data-stu-id="9c101-118">Symbol and Operator Reference</span></span>](index.md)
