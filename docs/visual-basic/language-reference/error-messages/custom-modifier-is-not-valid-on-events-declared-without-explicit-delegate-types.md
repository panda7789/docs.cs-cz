---
title: Modifikátor 'Custom' není platný pro události deklarované bez explicitních typů delegátů.
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 169cb49cc5abc76b7c52785392d0083b81a99450
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803880"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>Modifikátor 'Custom' není platný pro události deklarované bez explicitních typů delegátů.
Na rozdíl od jiných vlastních událostí `Custom Event` deklarace vyžaduje `As` klauzule podle název události, které explicitně určuje typ delegáta pro událost.  
  
 Non vlastní události může být definována buď pomocí `As` klauzule a explicitní typ delegáta nebo s parametrem seznamu bezprostředně za název události.  
  
 **ID chyby:** BC31122  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Definujte delegáta se stejným seznamem parametrů jako vlastní událost.  
  
     Například pokud `Custom Event` byl definovaný souborem `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, pak odpovídající delegáta by byl následující.  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. Nahraďte parametr seznam vlastních událostí pomocí `As` klauzule určující typ delegáta.  
  
     Pokračujte v tomto příkladu `Custom Event` deklarace by být přepsán následujícím způsobem.  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu deklaruje `Custom Event` a určuje požadované `As` klauzule s typem delegáta.  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
