---
title: Logické operátory (F#)
description: Další informace o logické operátory, které jsou k dispozici v programovacím jazyce F#.
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "45638477"
---
# <a name="boolean-operators"></a><span data-ttu-id="9414c-103">Logické operátory</span><span class="sxs-lookup"><span data-stu-id="9414c-103">Boolean Operators</span></span>

<span data-ttu-id="9414c-104">Toto téma popisuje podporu pro logické operátory v jazyce F#.</span><span class="sxs-lookup"><span data-stu-id="9414c-104">This topic describes the support for Boolean operators in the F# language.</span></span>

## <a name="summary-of-boolean-operators"></a><span data-ttu-id="9414c-105">Souhrnné informace o logické operátory</span><span class="sxs-lookup"><span data-stu-id="9414c-105">Summary of Boolean Operators</span></span>

<span data-ttu-id="9414c-106">Následující tabulka shrnuje logické operátory, které jsou k dispozici v jazyce F#.</span><span class="sxs-lookup"><span data-stu-id="9414c-106">The following table summarizes the Boolean operators that are available in the F# language.</span></span> <span data-ttu-id="9414c-107">Je jediným typem podporuje tyto operátory `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="9414c-107">The only type supported by these operators is the `bool` type.</span></span>

|<span data-ttu-id="9414c-108">Operátor</span><span class="sxs-lookup"><span data-stu-id="9414c-108">Operator</span></span>|<span data-ttu-id="9414c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9414c-109">Description</span></span>|
|--------|-----------|
|`not`|<span data-ttu-id="9414c-110">Logická negace</span><span class="sxs-lookup"><span data-stu-id="9414c-110">Boolean negation</span></span>|
|<code>&#124;&#124;</code>|<span data-ttu-id="9414c-111">Logický OR</span><span class="sxs-lookup"><span data-stu-id="9414c-111">Boolean OR</span></span>|
|`&&`|<span data-ttu-id="9414c-112">Logická a</span><span class="sxs-lookup"><span data-stu-id="9414c-112">Boolean AND</span></span>|

<span data-ttu-id="9414c-113">Logické a a operátory provádějí nebo *krátká smyčka – vyhodnocení*, to znamená, že vyhodnocení výrazu na pravé straně operátoru pouze v případě, že je potřeba určit celkový výsledek výrazu.</span><span class="sxs-lookup"><span data-stu-id="9414c-113">The Boolean AND and OR operators perform *short-circuit evaluation*, that is, they evaluate the expression on the right of the operator only when it is necessary to determine the overall result of the expression.</span></span> <span data-ttu-id="9414c-114">Druhý výraz `&&` operátor je vyhodnocen pouze v případě, že první výraz je vyhodnocen jako `true`; druhý výraz `||` operátor je vyhodnocen pouze v případě, že první výraz je vyhodnocen jako `false`.</span><span class="sxs-lookup"><span data-stu-id="9414c-114">The second expression of the `&&` operator is evaluated only if the first expression evaluates to `true`; the second expression of the `||` operator is evaluated only if the first expression evaluates to `false`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9414c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9414c-115">See also</span></span>

- [<span data-ttu-id="9414c-116">Bitové operátory</span><span class="sxs-lookup"><span data-stu-id="9414c-116">Bitwise Operators</span></span>](bitwise-operators.md)
- [<span data-ttu-id="9414c-117">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="9414c-117">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="9414c-118">Referenční dokumentace symbolů a operátorů</span><span class="sxs-lookup"><span data-stu-id="9414c-118">Symbol and Operator Reference</span></span>](index.md)
