---
title: 'Postupy: Volání procedury vlastnosti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: d05c1b63f5567ade9935f80ecc022eb4840e0af0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318742"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>Postupy: Volání procedury vlastnosti (Visual Basic)
Volání procedury vlastnosti uložení hodnoty do vlastnosti nebo načítání jeho hodnotu. Přístup k vlastnosti stejným způsobem, přístup k proměnné.  
  
 Vlastnosti `Set` postup uloží hodnotu a jeho `Get` postup načte hodnotu. Však není volána explicitně tyto postupy podle názvu. Pomocí vlastnosti v příkazu přiřazení nebo výraz, stejně jako by ukládat nebo načítat hodnoty proměnné. Visual Basic provede volání do procedury vlastnosti.  
  
### <a name="to-call-a-propertys-get-procedure"></a>Volání procedury Get vlastnosti  
  
1. Použijte název vlastnosti výrazu stejným způsobem použijete název proměnné. Můžete použít vlastnost kdekoli můžete použít proměnnou nebo konstantu.  
  
     -nebo-  
  
     Použijte název vlastnosti po rovnosti (`=`) Přihlaste se příkazu přiřazení.  
  
     Následující příklad přečte hodnotu <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> vlastnost implicitně volání jeho `Get` postup.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Pokud vlastnost přebírá argumenty, postupujte podle názvu vlastnosti se závorkami uvést seznam argumentů. Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.  
  
3. Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami. Ujistěte se, že zadáte argumenty ve stejném pořadí, že vlastnost definuje odpovídající parametry.  
  
 Hodnota vlastnosti podílí na výraz, stejně jako proměnné by – konstanta nebo je uložen v proměnné nebo vlastnosti na levé straně příkazu přiřazení.  
  
### <a name="to-call-a-propertys-set-procedure"></a>Volání vlastnosti je postup nastavení  
  
1. Použijte název vlastnosti na levé straně příkazu přiřazení.  
  
     Následující příklad nastaví hodnotu vlastnosti <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> vlastnost implicitně volání `Set` postup.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Pokud vlastnost přebírá argumenty, postupujte podle názvu vlastnosti se závorkami uvést seznam argumentů. Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.  
  
3. Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami. Ujistěte se, že zadáte argumenty ve stejném pořadí, že vlastnost definuje odpovídající parametry.  
  
 Hodnota generovaná na pravé straně příkazu přiřazení je uložená ve vlastnosti.  
  
## <a name="see-also"></a>Viz také:

- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
- [Příkaz Get](../../../../visual-basic/language-reference/statements/get-statement.md)
- [Příkaz Set](../../../../visual-basic/language-reference/statements/set-statement.md)
