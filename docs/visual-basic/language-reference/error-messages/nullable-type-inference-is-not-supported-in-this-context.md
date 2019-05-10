---
title: V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 3ab8028062402e33b787a5a8649d93d975918393
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665710"
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
  
- Použití `As` klauzule deklarovat proměnnou jako s možnou hodnotou Null.  
  
## <a name="see-also"></a>Viz také:

- [Typy hodnot s povolenou hodnotou Null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
