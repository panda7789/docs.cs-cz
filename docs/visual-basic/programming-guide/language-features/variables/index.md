---
title: Proměnné
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: 26433acea2b98ad0e67b9c35bec4eb8e88f7b7b6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352411"
---
# <a name="variables-in-visual-basic"></a>Proměnné v jazyce Visual Basic
Při provádění výpočtů s Visual Basic často potřebujete ukládat hodnoty. Můžete například chtít vypočítat několik hodnot, porovnat je a provádět na nich různé operace v závislosti na výsledku porovnání. Hodnoty je třeba zachovat, pokud je chcete porovnat.  
  
## <a name="usage"></a>Využití  
 Visual Basic, stejně jako většina programovacích jazyků, používá proměnné pro ukládání hodnot. *Proměnná* má název (slovo, které použijete k odkazování na hodnotu, kterou proměnná obsahuje). Proměnná má také datový typ (který určuje druh dat, která proměnná může uložit). Proměnná může představovat pole, pokud má uložit indexovanou sadu úzce souvisejících datových položek.  
  
 Odvození místního typu umožňuje deklarovat proměnné bez explicitního oznámení datového typu. Místo toho kompilátor odvodí typ proměnné z typu inicializačního výrazu. Další informace naleznete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) a [příkaz k odvození možnosti](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Přiřazení hodnot  
 Příkazy přiřazení slouží k provádění výpočtů a přiřazení výsledku proměnné, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> Rovnítko (`=`) v tomto příkladu je operátor přiřazení, nikoli operátor rovnosti. Hodnota je přiřazena k proměnné `applesSold`.  
  
 Další informace najdete v tématu [Postup: přesun dat do proměnné a z ní](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).  
  
## <a name="variables-and-properties"></a>Proměnné a vlastnosti  
 Podobně jako proměnná *vlastnost* představuje hodnotu, ke které máte přístup. Je však složitější než proměnná. Vlastnost používá bloky kódu, které řídí, jak nastavit a načíst jeho hodnotu. Další informace naleznete v tématu [rozdíly mezi vlastnostmi a proměnnými v Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Viz také:

- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Řešení potíží s proměnnými](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
- [Postupy: Přesun dat do proměnné a z proměnné](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [Rozdíly mezi vlastnostmi a proměnnými v Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
