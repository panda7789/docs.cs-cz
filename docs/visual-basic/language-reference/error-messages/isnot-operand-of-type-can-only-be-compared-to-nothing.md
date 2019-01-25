---
title: '&#39;IsNot&#39; operand typu &#39;typename&#39; lze porovnat pouze s &#39;nic&#39;, protože &#39;typename&#39; je typ připouštějící hodnotu Null'
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 65b04c85bccd169bbb2eea847d7b8af96c1a292f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505715"
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a><span data-ttu-id="8a0db-102">&#39;IsNot&#39; operand typu &#39;typename&#39; lze porovnat pouze s &#39;nic&#39;, protože &#39;typename&#39; je typ připouštějící hodnotu Null</span><span class="sxs-lookup"><span data-stu-id="8a0db-102">&#39;IsNot&#39; operand of type &#39;typename&#39; can only be compared to &#39;Nothing&#39;, because &#39;typename&#39; is a nullable type</span></span>
<span data-ttu-id="8a0db-103">Proměnná deklarovaná jako s možnou hodnotou NULL byl porovnání na výraz, jiné než `Nothing` pomocí `IsNot` operátor.</span><span class="sxs-lookup"><span data-stu-id="8a0db-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="8a0db-104">**ID chyby:** BC32128</span><span class="sxs-lookup"><span data-stu-id="8a0db-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8a0db-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8a0db-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="8a0db-106">K porovnání s možnou hodnotou Null typu ve výrazu jiné než `Nothing` pomocí `IsNot` operátora, volání `GetType` metodu na typ připouštějící hodnotu Null a porovnání výsledků výrazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8a0db-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a0db-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a0db-107">See also</span></span>
- [<span data-ttu-id="8a0db-108">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="8a0db-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="8a0db-109">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="8a0db-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
