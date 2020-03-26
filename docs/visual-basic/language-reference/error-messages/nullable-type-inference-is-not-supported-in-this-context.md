---
title: V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249497"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
Typy hodnot a struktury lze deklarovat s platností.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Však nelze použít deklaraci s možnou hodnotou null v kombinaci s odvozením typu. Následující příklady způsobit tuto chybu.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **ID chyby:** BC36629  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pomocí `As` klauzule deklarujte proměnnou jako typ hodnoty s možnou hodnotou s hodnotou, kterou lze použít.  
  
## <a name="see-also"></a>Viz také

- [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
