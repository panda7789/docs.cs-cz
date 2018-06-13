---
title: Logické operátory (F#)
description: 'Další informace o logické operátory, které jsou k dispozici v programovací jazyk F #.'
ms.date: 05/16/2016
ms.openlocfilehash: f8516ceb531907400f98dc4226d2985d3119e9e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563425"
---
# <a name="boolean-operators"></a><span data-ttu-id="31151-103">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="31151-103">Boolean Operators</span></span>

<span data-ttu-id="31151-104">Toto téma popisuje podporu logické operátory v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="31151-104">This topic describes the support for Boolean operators in the F# language.</span></span>


## <a name="summary-of-boolean-operators"></a><span data-ttu-id="31151-105">Souhrn logické operátory</span><span class="sxs-lookup"><span data-stu-id="31151-105">Summary of Boolean Operators</span></span>
<span data-ttu-id="31151-106">Následující tabulka shrnuje logické operátory, které jsou k dispozici v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="31151-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="31151-107">Je jediným typem podporuje tyto operátory `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="31151-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="31151-108">Operátor</span><span class="sxs-lookup"><span data-stu-id="31151-108">Operator</span></span>|<span data-ttu-id="31151-109">Popis</span><span class="sxs-lookup"><span data-stu-id="31151-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="31151-110">Logická negace</span><span class="sxs-lookup"><span data-stu-id="31151-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="31151-111">Logická hodnota nebo</span><span class="sxs-lookup"><span data-stu-id="31151-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="31151-112">Logická hodnota a</span><span class="sxs-lookup"><span data-stu-id="31151-112">Boolean AND</span></span>|

<span data-ttu-id="31151-113">Logická hodnota a a nebo operátory provést *krátká smyčka – vyhodnocení*, to znamená, že vyhodnocování výrazu na pravé straně operátoru jenom v případě, že je nutné určit celkový výsledek výrazu.</span><span class="sxs-lookup"><span data-stu-id="31151-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="31151-114">Druhý výraz `&&` operátor vyhodnotí pouze v případě, že první vyhodnocen jako `true`; druhý výraz `||` operátor vyhodnotí pouze v případě, že první vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="31151-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="31151-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="31151-115">See Also</span></span>
[<span data-ttu-id="31151-116">Bitové operátory</span><span class="sxs-lookup"><span data-stu-id="31151-116">Bitwise Operators</span></span>](bitwise-operators.md)

[<span data-ttu-id="31151-117">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="31151-117">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="31151-118">Referenční dokumentace symbolů a operátorů</span><span class="sxs-lookup"><span data-stu-id="31151-118">Symbol and Operator Reference</span></span>](index.md)
