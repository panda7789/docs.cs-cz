---
title: Klíčové slovo 'Is' vyžaduje operandy typu odkaz, ale tento operand má typ hodnoty '<typename>'.
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: e5acc94a3738fca3a43740bdba727fc843132aa1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402808"
---
# <a name="is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="10581-102">Klíčové slovo 'Is' vyžaduje operandy typu odkaz, ale tento operand má typ hodnoty '\<typename>'.</span><span class="sxs-lookup"><span data-stu-id="10581-102">'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>
<span data-ttu-id="10581-103">`Is`Operátor porovnání Určuje, zda dvě proměnné objektu odkazují na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="10581-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="10581-104">Toto porovnání není definováno pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="10581-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="10581-105">**ID chyby:** BC30020</span><span class="sxs-lookup"><span data-stu-id="10581-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10581-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="10581-106">To correct this error</span></span>  
  
- <span data-ttu-id="10581-107">K porovnání dvou typů hodnot použijte příslušný operátor aritmetického porovnání nebo `Like` operátor.</span><span class="sxs-lookup"><span data-stu-id="10581-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10581-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="10581-108">See also</span></span>

- [<span data-ttu-id="10581-109">Is – operátor</span><span class="sxs-lookup"><span data-stu-id="10581-109">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="10581-110">Like – operátor</span><span class="sxs-lookup"><span data-stu-id="10581-110">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="10581-111">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="10581-111">Comparison Operators</span></span>](../operators/comparison-operators.md)
