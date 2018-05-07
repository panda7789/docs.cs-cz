---
title: V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: ea531c7be676e940a263b019a66cc80cf280a772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
Typy hodnot a struktury lze deklarovat s možnou hodnotou Null.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 S možnou hodnotou Null deklarace však nelze použít v kombinaci s odvození typu. Následující příklady příčinou této chyby.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **ID chyby:** BC36629  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použijte `As` klauzule deklarovat proměnnou jako s možnou hodnotou Null.  
  
## <a name="see-also"></a>Viz také  
 [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
