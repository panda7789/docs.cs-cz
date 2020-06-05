---
title: Proměnné
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: ff617774d7e93ab4238ebc06617cc03fb6bc675a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410384"
---
# <a name="variables-in-visual-basic"></a>Proměnné v jazyce Visual Basic
Při provádění výpočtů s Visual Basic často potřebujete ukládat hodnoty. Můžete například chtít vypočítat několik hodnot, porovnat je a provádět na nich různé operace v závislosti na výsledku porovnání. Hodnoty je třeba zachovat, pokud je chcete porovnat.  
  
## <a name="usage"></a>Využití  
 Visual Basic, stejně jako většina programovacích jazyků, používá proměnné pro ukládání hodnot. *Proměnná* má název (slovo, které použijete k odkazování na hodnotu, kterou proměnná obsahuje). Proměnná má také datový typ (který určuje druh dat, která proměnná může uložit). Proměnná může představovat pole, pokud má uložit indexovanou sadu úzce souvisejících datových položek.  
  
 Odvození místního typu umožňuje deklarovat proměnné bez explicitního oznámení datového typu. Místo toho kompilátor odvodí typ proměnné z typu inicializačního výrazu. Další informace naleznete v tématu [odvození místního typu](local-type-inference.md) a [příkaz k odvození možnosti](../../../language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Přiřazení hodnot  
 Příkazy přiřazení slouží k provádění výpočtů a přiřazení výsledku proměnné, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> Symbol rovná se ( `=` ) v tomto příkladu je operátor přiřazení, nikoli operátor rovnosti. Hodnota je přiřazena proměnné `applesSold` .  
  
 Další informace najdete v tématu [Postup: přesun dat do proměnné a z ní](how-to-move-data-into-and-out-of-a-variable.md).  
  
## <a name="variables-and-properties"></a>Proměnné a vlastnosti  
 Podobně jako proměnná *vlastnost* představuje hodnotu, ke které máte přístup. Je však složitější než proměnná. Vlastnost používá bloky kódu, které řídí, jak nastavit a načíst jeho hodnotu. Další informace naleznete v tématu [rozdíly mezi vlastnostmi a proměnnými v Visual Basic](../procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Viz také

- [Deklarace proměnné](variable-declaration.md)
- [Proměnné objektu](object-variables.md)
- [Řešení potíží s proměnnými](troubleshooting-variables.md)
- [Postupy: Přesun dat do proměnné a z proměnné](how-to-move-data-into-and-out-of-a-variable.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](../procedures/differences-between-properties-and-variables.md)
- [Odvození místního typu](local-type-inference.md)
