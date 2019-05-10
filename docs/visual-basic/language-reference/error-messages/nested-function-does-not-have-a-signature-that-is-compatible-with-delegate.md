---
title: Vnořená funkce nemá stejný podpis kompatibilní s delegátem '<delegatename>'.
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 912962e2ab39c4811294ccc225814b230100e12a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591998"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>Vnořená funkce nemá stejný podpis kompatibilní s delegátem '\<vlastnost delegatename > "
Výraz lambda se přiřadila do delegáta, který má nekompatibilní podpis. Například v následujícím kódu, delegátu `Del` má dva celočíselné parametry.  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 Chyba se vyvolá, pokud výraz lambda s jedním argumentem je deklarovaný jako typ `Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **ID chyby:** BC36532  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Úprava definice delegáta nebo přiřazené lambda výraz tak, aby podpisy jsou kompatibilní.  
  
## <a name="see-also"></a>Viz také:

- [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
