---
title: "& č. 39; IsNot & č. 39; operand typu & č. 39; typename & č. 39; lze porovnat pouze do & č. 39; Nic & č. 39; protože & č. 39; typename & č. 39; je typ s možnou hodnotou Null"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords: BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec0ae1561bfbee998e7c65f6023012c0f982a8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a><span data-ttu-id="a0e53-102">& č. 39; IsNot & č. 39; operand typu & č. 39; typename & č. 39; lze porovnat pouze do & č. 39; Nic & č. 39; protože & č. 39; typename & č. 39; je typ s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="a0e53-102">&#39;IsNot&#39; operand of type &#39;typename&#39; can only be compared to &#39;Nothing&#39;, because &#39;typename&#39; is a nullable type</span></span>
<span data-ttu-id="a0e53-103">Proměnná definovaná jako s možnou hodnotou NULL byl porovnání s výrazem jiným než `Nothing` pomocí `IsNot` operátor.</span><span class="sxs-lookup"><span data-stu-id="a0e53-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="a0e53-104">**ID chyby:** BC32128</span><span class="sxs-lookup"><span data-stu-id="a0e53-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a0e53-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a0e53-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="a0e53-106">K porovnání typu s povolenou hodnotou Null pro výraz jiné než `Nothing` pomocí `IsNot` operátor, volání `GetType` metodu na typ s možnou hodnotou Null a porovnání výsledek výrazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a0e53-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0e53-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0e53-107">See Also</span></span>  
 [<span data-ttu-id="a0e53-108">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="a0e53-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="a0e53-109">IsNot – operátor</span><span class="sxs-lookup"><span data-stu-id="a0e53-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
