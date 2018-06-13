---
title: '&#39;Je&#39; vyžaduje operandy mají odkazové typy, ale tento operand je typ hodnoty &#39; &lt;typename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 07838e62bd6b180f7dece79355ea7aa1d6c4527a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585577"
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="1b9d7-102">&#39;Je&#39; vyžaduje operandy mají odkazové typy, ale tento operand je typ hodnoty &#39; &lt;typename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="1b9d7-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="1b9d7-103">`Is` Relační operátor určuje, zda dva objektové proměnné odkazují na stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="1b9d7-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="1b9d7-104">Toto porovnání není definován pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="1b9d7-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="1b9d7-105">**ID chyby:** BC30020</span><span class="sxs-lookup"><span data-stu-id="1b9d7-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1b9d7-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1b9d7-106">To correct this error</span></span>  
  
-   <span data-ttu-id="1b9d7-107">Použít příslušné aritmetické relační operátor nebo `Like` operátor k porovnání dvou typů hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1b9d7-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9d7-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b9d7-108">See Also</span></span>  
 [<span data-ttu-id="1b9d7-109">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="1b9d7-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="1b9d7-110">Operátor Like</span><span class="sxs-lookup"><span data-stu-id="1b9d7-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="1b9d7-111">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="1b9d7-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
