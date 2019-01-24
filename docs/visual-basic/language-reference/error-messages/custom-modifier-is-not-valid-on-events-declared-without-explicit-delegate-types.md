---
title: '&#39;Vlastní&#39; modifikátor není platný pro události deklarované bez explicitních typů delegátů.'
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: c909973ef1c00cb01179b0e5527dfecd6f41e577
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574778"
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>&#39;Vlastní&#39; modifikátor není platný pro události deklarované bez explicitních typů delegátů.
Na rozdíl od jiných vlastních událostí `Custom Event` deklarace vyžaduje `As` klauzule podle název události, které explicitně určuje typ delegáta pro událost.  
  
 Non vlastní události může být definována buď pomocí `As` klauzule a explicitní typ delegáta nebo s parametrem seznamu bezprostředně za název události.  
  
 **ID chyby:** BC31122  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Definujte delegáta se stejným seznamem parametrů jako vlastní událost.  
  
     Například pokud `Custom Event` byl definovaný souborem `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, pak odpovídající delegáta by byl následující.  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  Nahraďte parametr seznam vlastních událostí pomocí `As` klauzule určující typ delegáta.  
  
     Pokračujte v tomto příkladu `Custom Event` deklarace by být přepsán následujícím způsobem.  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu deklaruje `Custom Event` a určuje požadované `As` klauzule s typem delegáta.  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
