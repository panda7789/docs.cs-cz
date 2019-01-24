---
title: V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 7dffc5233656257cd892f573a2f8b9f91d781c21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611888"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
Hodnotové typy a struktury mohou být deklarovány s možnou hodnotou Null.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Však nelze použít deklaraci s možnou hodnotou Null v kombinaci s odvození typu proměnné. Následující příklady příčinou této chyby.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **ID chyby:** BC36629  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použití `As` klauzule deklarovat proměnnou jako s možnou hodnotou Null.  
  
## <a name="see-also"></a>Viz také:
- [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
