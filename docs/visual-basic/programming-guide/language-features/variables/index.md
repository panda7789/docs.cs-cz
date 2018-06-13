---
title: Proměnné v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: 79cd5629d4de6279eb370c18db617a5ad532108d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654470"
---
# <a name="variables-in-visual-basic"></a>Proměnné v jazyce Visual Basic
Často je nutné uložit hodnoty při provádění výpočtů v jazyce Visual Basic. Můžete například chtít výpočet několik hodnot, porovnat a provádět různé operace na nich, v závislosti na výsledku porovnání. Budete muset zachovat hodnoty, pokud chcete porovnat.  
  
## <a name="usage"></a>Použití  
 Visual Basic, stejně jako většinu programovacích jazyků, používá pro ukládání hodnoty proměnné. A *proměnné* má název (word, který používáte k odkazování na hodnotu, která obsahuje proměnnou). Proměnné také má datový typ (který určuje typ dat, které můžete ukládat proměnné). Pokud má k uložení indexované sadu úzce související datových položek, může představovat proměnné pole.  
  
 Odvození místního typu umožňuje deklarujte proměnné bez explicitně s informacemi o tom datovým typem. Místo toho kompilátor odvodí typ proměnné z typu inicializace výrazu. Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) a [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Přidělování hodnot  
 Příkazy přiřazení slouží k provádění výpočtů a přiřadit výsledek proměnné, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  Znaménkem rovnosti (`=`) v tomto příkladu je operátor přiřazení, není operátor rovnosti. Hodnota je právě přiřazován proměnnou `applesSold`.  
  
 Další informace najdete v tématu [postupy: Přesun dat do a z proměnné](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).  
  
## <a name="variables-and-properties"></a>Proměnné a vlastnosti  
 Jako proměnnou, *vlastnost* představuje hodnotu, která se zobrazí. Je však mnohem složitější než proměnné. Vlastnost používá bloky kódu, které řídí nastavení a načtení jeho hodnotu. Další informace najdete v tématu [rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Viz také  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Řešení potíží s proměnnými](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)  
 [Postupy: Přesun dat do proměnné a z proměnné](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
