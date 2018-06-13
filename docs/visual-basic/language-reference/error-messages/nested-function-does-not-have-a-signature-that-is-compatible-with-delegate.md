---
title: Vnořené funkce neobsahuje podpis, který je kompatibilní s delegáta &#39; &lt;vlastnost delegatename&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 94c53d30ad9aea9386fbb1be3e65fa31719f7a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594468"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>Vnořené funkce neobsahuje podpis, který je kompatibilní s delegáta &#39; &lt;vlastnost delegatename&gt;&#39;
Výraz lambda byl přiřazen delegáta, který má nekompatibilní podpis. Například následující kód, delegovat `Del` má dva parametry celé číslo.  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 Chyba se vyvolá, pokud výraz lambda s jedním argumentem je deklarován jako typ `Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **ID chyby:** BC36532  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Upravte definici delegáta nebo výrazu lambda přiřazené tak, aby byly kompatibilní podpisů.  
  
## <a name="see-also"></a>Viz také  
 [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
