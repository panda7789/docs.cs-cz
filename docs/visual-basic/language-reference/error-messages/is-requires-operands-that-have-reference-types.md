---
title: '&#39;Je&#39; vyžaduje operandy, které mají typy odkazů, ale tento operand má typ hodnoty &#39; &lt;typename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 0b3f80e98087e455ec730dea8c57478528e9259c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722917"
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="b4b2b-102">&#39;Je&#39; vyžaduje operandy, které mají typy odkazů, ale tento operand má typ hodnoty &#39; &lt;typename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="b4b2b-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="b4b2b-103">`Is` Operátor porovnání určuje, zda dva objektových proměnných odkazují na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="b4b2b-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="b4b2b-104">Toto porovnání není definován pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="b4b2b-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="b4b2b-105">**ID chyby:** BC30020</span><span class="sxs-lookup"><span data-stu-id="b4b2b-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b4b2b-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b4b2b-106">To correct this error</span></span>  
  
-   <span data-ttu-id="b4b2b-107">Operátor porovnání odpovídající aritmetické nebo `Like` operátor porovnání dvou typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="b4b2b-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b2b-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4b2b-108">See also</span></span>
- [<span data-ttu-id="b4b2b-109">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="b4b2b-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="b4b2b-110">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="b4b2b-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="b4b2b-111">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="b4b2b-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
