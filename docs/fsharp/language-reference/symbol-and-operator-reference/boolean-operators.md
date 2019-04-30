---
title: Logické operátory
description: Další informace o logické operátory, které jsou k dispozici v F# programovací jazyk.
ms.date: 05/16/2016
ms.openlocfilehash: 5353b6ec6a0bd610f3446761a1d28f01f0403302
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925811"
---
# <a name="boolean-operators"></a><span data-ttu-id="780fc-103">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="780fc-103">Boolean Operators</span></span>

<span data-ttu-id="780fc-104">Toto téma popisuje podporu pro logické operátory ve F# jazyka.</span><span class="sxs-lookup"><span data-stu-id="780fc-104">This topic describes the support for Boolean operators in the F# language.</span></span>

## <a name="summary-of-boolean-operators"></a><span data-ttu-id="780fc-105">Souhrnné informace o logické operátory</span><span class="sxs-lookup"><span data-stu-id="780fc-105">Summary of Boolean Operators</span></span>

<span data-ttu-id="780fc-106">Následující tabulka shrnuje logické operátory, které jsou k dispozici v F# jazyka.</span><span class="sxs-lookup"><span data-stu-id="780fc-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="780fc-107">Je jediným typem podporuje tyto operátory `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="780fc-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="780fc-108">Operátor</span><span class="sxs-lookup"><span data-stu-id="780fc-108">Operator</span></span>|<span data-ttu-id="780fc-109">Popis</span><span class="sxs-lookup"><span data-stu-id="780fc-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="780fc-110">Logická negace</span><span class="sxs-lookup"><span data-stu-id="780fc-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="780fc-111">Logický OR</span><span class="sxs-lookup"><span data-stu-id="780fc-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="780fc-112">Logická a</span><span class="sxs-lookup"><span data-stu-id="780fc-112">Boolean AND</span></span>|

<span data-ttu-id="780fc-113">Logické a a operátory provádějí nebo *krátká smyčka – vyhodnocení*, to znamená, že vyhodnocení výrazu na pravé straně operátoru pouze v případě, že je potřeba určit celkový výsledek výrazu.</span><span class="sxs-lookup"><span data-stu-id="780fc-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="780fc-114">Druhý výraz `&&` operátor je vyhodnocen pouze v případě, že první výraz je vyhodnocen jako `true`; druhý výraz `||` operátor je vyhodnocen pouze v případě, že první výraz je vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="780fc-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="780fc-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="780fc-115">See also</span></span>

- [<span data-ttu-id="780fc-116">Bitové operátory</span><span class="sxs-lookup"><span data-stu-id="780fc-116">Bitwise Operators</span></span>](bitwise-operators.md)
- [<span data-ttu-id="780fc-117">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="780fc-117">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="780fc-118">Referenční dokumentace symbolů a operátorů</span><span class="sxs-lookup"><span data-stu-id="780fc-118">Symbol and Operator Reference</span></span>](index.md)