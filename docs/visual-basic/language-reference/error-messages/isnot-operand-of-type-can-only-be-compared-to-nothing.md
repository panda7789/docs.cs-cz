---
title: Operand 'IsNot' typu 'typename' lze porovnat pouze s hodnotou 'Nothing', protože 'typename' je typ s povolenou hodnotou Null.
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: be2a3239b2ca520c4051a1504f91a766b4401a05
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834020"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="46e6e-102">Operand 'IsNot' typu 'typename' lze porovnat pouze s hodnotou 'Nothing', protože 'typename' je typ s povolenou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="46e6e-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>
<span data-ttu-id="46e6e-103">Proměnná deklarovaná jako s možnou hodnotou NULL byl porovnání na výraz, jiné než `Nothing` pomocí `IsNot` operátor.</span><span class="sxs-lookup"><span data-stu-id="46e6e-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="46e6e-104">**ID chyby:** BC32128</span><span class="sxs-lookup"><span data-stu-id="46e6e-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="46e6e-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="46e6e-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="46e6e-106">K porovnání s možnou hodnotou Null typu ve výrazu jiné než `Nothing` pomocí `IsNot` operátora, volání `GetType` metodu na typ připouštějící hodnotu Null a porovnání výsledků výrazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="46e6e-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="46e6e-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46e6e-107">See also</span></span>

- [<span data-ttu-id="46e6e-108">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="46e6e-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="46e6e-109">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="46e6e-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
