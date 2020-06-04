---
title: Modifikátor 'Custom' není platný pro události deklarované bez explicitních typů delegátů.
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 0c5a4188fedf9685afdd1cde4c1de93a0b43b919
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409777"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>Modifikátor 'Custom' není platný pro události deklarované bez explicitních typů delegátů.
Na rozdíl od nevlastní události `Custom Event` deklarace vyžaduje `As` klauzuli za názvem události, která explicitně určuje typ delegáta pro událost.  
  
 Nevlastní události lze definovat buď pomocí `As` klauzule, explicitního typu delegáta, nebo se seznamem parametrů hned za názvem události.  
  
 **ID chyby:** BC31122  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Definujte delegáta se stejným seznamem parametrů jako vlastní událost.  
  
     Například, pokud `Custom Event` byla definována uživatelem `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` , pak odpovídající delegát bude následující.  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. Nahraďte seznam parametrů vlastní události `As` klauzulí určující typ delegáta.  
  
     Pokračování v příkladu `Custom Event` deklarace by se přepsala takto.  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a>Příklad  
 Tento příklad deklaruje `Custom Event` a Určuje požadovanou `As` klauzuli s typem delegáta.  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Event – příkaz](../statements/event-statement.md)
- [Delegate – příkaz](../statements/delegate-statement.md)
- [Události](../../programming-guide/language-features/events/index.md)
