---
title: V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409384"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>V tomto kontextu není podporováno odvození typu s povolenou hodnotu Null.
Typy hodnot a struktury lze deklarovat s možnou hodnotou null.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Nemůžete však použít deklaraci Nullable v kombinaci s odvozením typu. Následující příklady způsobují tuto chybu.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **ID chyby:** BC36629  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Použijte `As` klauzuli pro deklaraci proměnné jako typ hodnoty s možnou hodnotou null.  
  
## <a name="see-also"></a>Viz také

- [Typy hodnot s možnou hodnotou null](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Odvození místního typu](../../programming-guide/language-features/variables/local-type-inference.md)
