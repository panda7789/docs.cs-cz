---
title: '&#39;Vlastní&#39; modifikátor není platný pro události deklarované bez explicitních typů delegátů.'
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 3f08bbbbbac4a01dfbac8d15cf9285c01262618a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>&#39;Vlastní&#39; modifikátor není platný pro události deklarované bez explicitních typů delegátů.
Na rozdíl od jiných vlastní události `Custom Event` deklarace vyžaduje `As` klauzule následující název události, které explicitně určuje typ delegát pro událost.  
  
 Bez vlastní události může být definována buď pomocí `As` klauzule a explicitního delegovat typ, nebo pomocí parametru seznamu okamžitě následující název události.  
  
 **ID chyby:** BC31122  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Definujte delegáta s stejný seznam parametrů jako vlastní události.  
  
     Například pokud `Custom Event` byl definován pomocí `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, pak odpovídající delegát by byl následující.  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  Nahradit seznam parametrů vlastní události s `As` klauzule určení typu delegáta.  
  
     Pokračování příkladu, s `Custom Event` deklarace by takto přepsána.  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad deklaruje `Custom Event` a určuje požadované `As` klauzule s typem delegáta.  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
