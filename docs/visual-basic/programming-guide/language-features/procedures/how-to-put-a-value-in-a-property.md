---
title: 'Postupy: Vložení hodnoty do vlastnosti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: d40ca98f94f410bb20c8df0e7f1a3f216cf53bf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589162"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Postupy: Vložení hodnoty do vlastnosti (Visual Basic)
Uložení hodnoty do vlastnosti tak, že vložíte název vlastnosti na levé straně příkazu přiřazení.  
  
 Vlastnosti `Set` postup uloží hodnotu, ale můžete explicitně ho nevolají podle názvu. Vlastnost se stejným způsobem, jako by proměnná. Visual Basic provede volání do procedury vlastnosti.  
  
### <a name="to-store-a-value-in-a-property"></a>K uložení hodnoty do vlastnosti  
  
1.  Použijte název vlastnosti na levé straně příkazu přiřazení.  
  
     Následující příklad nastaví hodnotu jazyka Visual Basic `TimeOfDay` vlastnost noon, implicitně volání jeho `Set` postup.  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  Pokud vlastnost přebírá argumenty, postupujte podle názvu vlastnosti se závorkami uvést seznam argumentů. Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.  
  
3.  Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami. Ujistěte se, že zadáte argumenty ve stejném pořadí, že vlastnost definuje odpovídající parametry.  
  
4.  Hodnota generovaná na pravé straně příkazu přiřazení je uložená ve vlastnosti.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
