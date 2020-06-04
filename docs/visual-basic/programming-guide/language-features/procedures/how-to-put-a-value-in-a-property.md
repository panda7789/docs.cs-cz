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
ms.openlocfilehash: c0fb3e137010390097a68aea161efcff93839d94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414334"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>Postupy: Vložení hodnoty do vlastnosti (Visual Basic)
Hodnotu vlastnosti uložíte tak, že umístíte název vlastnosti na levou stranu příkazu přiřazení.  
  
 `Set`Procedura vlastnosti ukládá hodnotu, ale explicitně ji nevoláte podle názvu. Vlastnost použijete stejně, jako byste použili proměnnou. Visual Basic provede volání procedur vlastností.  
  
### <a name="to-store-a-value-in-a-property"></a>Uložení hodnoty do vlastnosti  
  
1. Použijte název vlastnosti na levé straně příkazu přiřazení.  
  
     Následující příklad nastaví hodnotu `TimeOfDay` vlastnosti Visual Basic na poledne a implicitně volá její `Set` proceduru.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. Pokud vlastnost přebírá argumenty, uveďte seznam argumentů tak, že postupujete podle názvu vlastnosti s závorkami. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.  
  
3. Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami. Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém vlastnost definuje odpovídající parametry.  
  
4. Hodnota vygenerovaná na pravé straně příkazu přiřazení je uložena ve vlastnosti.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Property – příkaz](../../../language-reference/statements/property-statement.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
