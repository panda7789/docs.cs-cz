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
ms.openlocfilehash: 8ea7741c943ea563fbd0c7649ac0ff85b2f9ebba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="recursive-procedures-visual-basic"></a>Rekurzivní procedury (Visual Basic)
A *rekurzivní* postup je ten, který volá sám sebe. Obecně platí tento není co nejúčinnější způsob, jak napsat kód jazyka Visual Basic.  
  
 Následující postup používá rekurze vypočítat faktoriál jeho původní argumentem.  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a>Informace o rekurzivní procedury  
 **Omezení podmínky**. Je třeba navrhnout rekurzivní postup testování pro alespoň jednu podmínku, která může obsluhovat rekurze a také musí zpracovávat tento případ, kde je splněna žádná taková podmínka během přiměřené počtu volání rekurzivní. Bez nejméně jedné podmínky, které nelze splnit bez selže spustí procedura vysoce rizikové provedení v nekonečné smyčce.  
  
 **Využití paměti**. Aplikace má omezené množství místa pro místní proměnné. Pokaždé, když proceduru volá samostatně, používá více toto místo pro další kopie jeho místní proměnné. Pokud tento proces pokračuje bez omezení, se může způsobit, že <xref:System.StackOverflowException> chyby.  
  
 **Efektivita**. Můžete nahradit téměř vždy smyčku pro rekurze. Smyčka nemá režii předávání argumentů, inicializace další úložiště a vrácení hodnot. Výkon může být mnohem lepší bez rekurzivní volání.  
  
 **Vzájemná rekurze**. Si můžete všimnout velmi nízký výkon nebo i nekonečnou smyčku, pokud dva postupy volání sebe navzájem. Takový návrh přináší stejné problémy jako jeden rekurzivní postup, ale může být těžší ke zjišťování a ladění.  
  
 **Volání metody s závorkách**. Když `Function` postup volá rekurzivně sama sebe, je třeba provést název procedury v závorkách, i když neprobíhá žádná seznam argumentů. Jinak název funkce je převzat jako představující vrácenou hodnotu funkce.  
  
 **Testování**. Pokud píšete rekurzivní procedury, měli byste otestovat se velmi pečlivě a ujistěte se, že splňuje vždy nějaká omezení podmínka. Také se ujistěte, že nelze spustit nedostatek paměti z důvodu s příliš mnoha volání rekurzivní.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.StackOverflowException>  
 [Procedury](./index.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Procedury funkce](./function-procedures.md)  
 [Procedury vlastnosti](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Řešení potíží s procedurami](./troubleshooting-procedures.md)  
 [Struktury smyčky](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Řešení potíží s výjimkami: System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
