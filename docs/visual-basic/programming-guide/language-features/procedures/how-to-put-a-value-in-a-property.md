---
title: 'Postupy: Vložení hodnoty do vlastnosti'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: ad0d0e81f94dd3dead50f21c3bd6ff580c004dd6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346058"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Postupy: Vložení hodnoty do vlastnosti (Visual Basic)
Hodnotu vlastnosti uložíte tak, že umístíte název vlastnosti na levou stranu příkazu přiřazení.  
  
 Procedura `Set` vlastnosti ukládá hodnotu, ale explicitně ji nevoláte podle názvu. Vlastnost použijete stejně, jako byste použili proměnnou. Visual Basic provede volání procedur vlastností.  
  
### <a name="to-store-a-value-in-a-property"></a>Uložení hodnoty do vlastnosti  
  
1. Použijte název vlastnosti na levé straně příkazu přiřazení.  
  
     Následující příklad nastaví hodnotu vlastnosti Visual Basic `TimeOfDay` na Nún, implicitně volá `Set` proceduru.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Pokud vlastnost přebírá argumenty, uveďte seznam argumentů tak, že postupujete podle názvu vlastnosti s závorkami. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.  
  
3. Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami. Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém vlastnost definuje odpovídající parametry.  
  
4. Hodnota vygenerovaná na pravé straně příkazu přiřazení je uložena ve vlastnosti.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Rozdíly mezi vlastnostmi a proměnnými v Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
