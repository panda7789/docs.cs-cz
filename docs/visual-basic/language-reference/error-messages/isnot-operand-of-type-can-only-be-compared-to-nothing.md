---
title: Operand 'IsNot' typu 'typename' lze porovnat pouze s hodnotou 'Nothing', protože 'typename' je typ s povolenou hodnotou Null.
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: f19b8cd5f80ba9fd6d1f5a9162b04ee409e24e28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311887"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>Operand 'IsNot' typu 'typename' lze porovnat pouze s hodnotou 'Nothing', protože 'typename' je typ s povolenou hodnotou Null.
Proměnná deklarovaná jako s možnou hodnotou NULL byl porovnání na výraz, jiné než `Nothing` pomocí `IsNot` operátor.  
  
 **ID chyby:** BC32128  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. K porovnání s možnou hodnotou Null typu ve výrazu jiné než `Nothing` pomocí `IsNot` operátora, volání `GetType` metodu na typ připouštějící hodnotu Null a porovnání výsledků výrazu, jak je znázorněno v následujícím příkladu.  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a>Viz také:

- [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
