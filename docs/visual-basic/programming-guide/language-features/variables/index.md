---
title: Proměnné v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e4397fb90e4fa5a3e68390137b84a375cf35956
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
