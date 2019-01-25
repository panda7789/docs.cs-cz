---
title: Proměnné v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: 50b82285d31d40adfce07a61cd7902cdb2809a52
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672224"
---
# <a name="variables-in-visual-basic"></a>Proměnné v jazyce Visual Basic
Často nutné pro ukládání hodnot při provádění výpočtů s jazykem Visual Basic. Můžete například výpočet několik hodnot, jejich porovnání a provádět s nimi, různé operace na základě výsledku porovnání. Je nutné zachovat hodnoty, pokud chcete porovnat.  
  
## <a name="usage"></a>Použití  
 Visual Basic, stejně jako většinu programovacích jazyků, používá pro ukládání hodnot proměnné. A *proměnnou* má název (word, který používáte k odkazování na hodnotu, která obsahuje proměnné). Proměnné také má datový typ (který určuje, jaká data, která může proměnná ukládat). Proměnná může představovat pole, pokud je ukládání indexovaných sadu položek úzce související data.  
  
 Odvození místního typu umožňuje deklarovat proměnné bez explicitní uvedení datového typu. Místo toho kompilátor odvodí typ proměnné z typu výrazu inicializace. Další informace najdete v tématu [odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) a [Option Infer – příkaz](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Přidělování hodnot  
 Přiřazovací příkazy slouží k provádění výpočtů a výsledek přiřaďte proměnné, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  Znaménko rovná se (`=`) v tomto příkladu je operátor přiřazení, ne operátor rovnosti. Hodnota je přiřazen do proměnné `applesSold`.  
  
 Další informace najdete v tématu [jak: Přesun dat do a z proměnné](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).  
  
## <a name="variables-and-properties"></a>Proměnné a vlastnosti  
 Jako proměnnou, *vlastnost* představuje hodnotu, která můžete přistupovat. Je však mnohem složitější než proměnné. Vlastnost používá bloky kódu, které řídí nastavení a načtení jeho hodnotu. Další informace najdete v tématu [rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Viz také:
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Řešení potíží s proměnnými](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
- [Postupy: Přesun dat do a z proměnné](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
