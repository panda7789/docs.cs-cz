---
title: '&#39;IsNot&#39; operand typu &#39;typename&#39; lze porovnat pouze k &#39;nic&#39;, protože &#39;typename&#39; je typ s možnou hodnotou Null'
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 44cc17c73b476e5e322b9b58b021bc7bcd63167f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587593"
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a>&#39;IsNot&#39; operand typu &#39;typename&#39; lze porovnat pouze k &#39;nic&#39;, protože &#39;typename&#39; je typ s možnou hodnotou Null
Proměnná definovaná jako s možnou hodnotou NULL byl porovnání s výrazem jiným než `Nothing` pomocí `IsNot` operátor.  
  
 **ID chyby:** BC32128  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  K porovnání typu s povolenou hodnotou Null pro výraz jiné než `Nothing` pomocí `IsNot` operátor, volání `GetType` metodu na typ s možnou hodnotou Null a porovnání výsledek výrazu, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a>Viz také  
 [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
