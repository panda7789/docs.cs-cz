---
title: Rekurzivní procedury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: b08a06a07f134b7c95251848862d39339e59fe61
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274346"
---
# <a name="recursive-procedures-visual-basic"></a>Rekurzivní procedury (Visual Basic)

*Rekurzivní* procedura je taková, která volá sám sebe. Obecně to není nejúčinnější způsob psaní kódu Visual Basic.  
  
 Následující postup používá rekurzi k výpočtu faktoriál jeho původního argumentu.  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>Otázky s rekurzivními procedurami

 **Omezující podmínky**. Je nutné navrhnout rekurzivní proceduru pro testování alespoň jedné podmínky, která může ukončit rekurzi, a také je třeba zpracovat případ, kdy není taková podmínka splněna v rozumném počtu rekurzivních volání. Bez nejméně jedné podmínky, která může být splněna bez selhání, váš postup bude mít vysoké riziko, že se spouští v nekonečné smyčce.

 **Využití paměti**. Vaše aplikace má omezené množství místa pro místní proměnné. Pokaždé, když procedura zavolá sám sebe, použije více místa pro další kopie místních proměnných. Pokud tento proces pokračuje neomezeně, způsobí <xref:System.StackOverflowException> to chybu.

 **Efektivita**. Je možné, že téměř vždy nahradíte smyčku pro rekurzi. Smyčka nemá režijní náklady na předávání argumentů, inicializaci dalšího úložiště a vrácení hodnot. Výkon může být mnohem lepší bez rekurzivních volání.

 **Vzájemná rekurze**. Můžete sledovat velmi špatný výkon nebo dokonce nekonečnou smyčku, pokud dva postupy navzájem volají. Takový návrh představuje stejné problémy jako jeden rekurzivní postup, ale může být těžší detekovat a ladit.

 **Volání pomocí závorek**. Při rekurzivním volání procedury je nutné použít název procedury s závorkami, a to i v případě, že neexistuje seznam argumentů. `Function` V opačném případě se název funkce povede jako reprezentace návratové hodnoty funkce.

 **Testování**. Pokud zapíšete rekurzivní proceduru, měli byste je pečlivě otestovat, abyste se ujistili, že vždy splňují určitou omezující podmínku. Měli byste taky zajistit, aby nedošlo k nedostatku paměti z důvodu příliš velkého počtu rekurzivních volání.

## <a name="see-also"></a>Viz také:

- <xref:System.StackOverflowException>
- [Procedury](index.md)
- [Procedury Sub](sub-procedures.md)
- [Procedury funkce](function-procedures.md)
- [Procedury vlastnosti](property-procedures.md)
- [Procedury operátoru](operator-procedures.md)
- [Parametry a argumenty procedury](procedure-parameters-and-arguments.md)
- [Přetížení procedury](procedure-overloading.md)
- [Řešení potíží s procedurami](troubleshooting-procedures.md)
- [Struktury smyčky](../control-flow/loop-structures.md)
