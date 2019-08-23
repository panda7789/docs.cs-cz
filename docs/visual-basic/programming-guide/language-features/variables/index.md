---
title: Proměnné v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: 30baab24c54b5158da53f1ba88206d8f1564ebaf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953339"
---
# <a name="variables-in-visual-basic"></a>Proměnné v jazyce Visual Basic
Při provádění výpočtů s Visual Basic často potřebujete ukládat hodnoty. Můžete například chtít vypočítat několik hodnot, porovnat je a provádět na nich různé operace v závislosti na výsledku porovnání. Hodnoty je třeba zachovat, pokud je chcete porovnat.  
  
## <a name="usage"></a>Použití  
 Visual Basic, stejně jako většina programovacích jazyků, používá proměnné pro ukládání hodnot. *Proměnná* má název (slovo, které použijete k odkazování na hodnotu, kterou proměnná obsahuje). Proměnná má také datový typ (který určuje druh dat, která proměnná může uložit). Proměnná může představovat pole, pokud má uložit indexovanou sadu úzce souvisejících datových položek.  
  
 Odvození místního typu umožňuje deklarovat proměnné bez explicitního oznámení datového typu. Místo toho kompilátor odvodí typ proměnné z typu inicializačního výrazu. Další informace naleznete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) a [příkaz k odvození možnosti](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Přiřazení hodnot  
 Příkazy přiřazení slouží k provádění výpočtů a přiřazení výsledku proměnné, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> Symbol rovná se (`=`) v tomto příkladu je operátor přiřazení, nikoli operátor rovnosti. Hodnota je přiřazena proměnné `applesSold`.  
  
 Další informace najdete v tématu [jak: Přesun dat do proměnné](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)a z ní.  
  
## <a name="variables-and-properties"></a>Proměnné a vlastnosti  
 Podobně jako proměnná *vlastnost* představuje hodnotu, ke které máte přístup. Je však složitější než proměnná. Vlastnost používá bloky kódu, které řídí, jak nastavit a načíst jeho hodnotu. Další informace naleznete v tématu [rozdíly mezi vlastnostmi a proměnnými v Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Viz také:

- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Řešení potíží s proměnnými](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
- [Postupy: Přesun dat do proměnné a z ní](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [Rozdíly mezi vlastnostmi a proměnnými v Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
