---
title: '&#39;&lt;TypeName&gt; &#39; je typem delegáta'
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: c6d4244ce72dedee50b65ba19978149ce86b9e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>&#39;&lt;TypeName&gt; &#39; je typem delegáta
'\<typename >' je typ delegáta. Delegát konstrukce umožňuje jenom jeden výraz AddressOf jako seznam argumentů. Často Výraz AddressOf lze namísto vytváření delegáta.  
  
 A `New` klauzule vytvoření instance třídy delegáta poskytuje seznam neplatný argumentů pro konstruktor delegáta.  
  
 Můžete zadat jenom jeden `AddressOf` výraz při vytvoření nové instance delegáta.  
  
 K této chybě může dojít, pokud neproběhne úspěšně všechny argumenty pro konstruktor delegáta, pokud předáte více než jeden argument, nebo Pokud předáte jeden argument, který není platným `AddressOf` výraz.  
  
 **ID chyby:** BC32008  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použití jedné `AddressOf` výraz v seznamu argumentů pro třídu delegáta v `New` klauzule.  
  
## <a name="see-also"></a>Viz také  
 [Operátor New](../../../visual-basic/language-reference/operators/new-operator.md)  
 [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Postupy: Volání metody delegáta](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
