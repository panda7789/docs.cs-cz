---
title: 'Postupy: Získání hodnoty z vlastnosti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5e2676a0880092a78405fe5dafa0469161b85610
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302930"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Postupy: Získání hodnoty z vlastnosti (Visual Basic)
Načtení hodnoty vlastnosti včetně názvu vlastnosti ve výrazu.  
  
 Vlastnosti `Get` postup načte hodnotu, ale můžete explicitně ho nevolají podle názvu. Vlastnost se stejným způsobem, jako by proměnná. Visual Basic provede volání do procedury vlastnosti.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>K načtení hodnoty z vlastnosti  
  
1. Použijte název vlastnosti výrazu stejným způsobem použijete název proměnné. Můžete použít vlastnost kdekoli můžete použít proměnnou nebo konstantu.  
  
     -nebo-  
  
     Použijte název vlastnosti po rovnosti (`=`) Přihlaste se příkazu přiřazení.  
  
     Následující příklad přečte hodnotu jazyka Visual Basic `Now` vlastnost implicitně volání jeho `Get` postup.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Pokud vlastnost přebírá argumenty, postupujte podle názvu vlastnosti se závorkami uvést seznam argumentů. Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.  
  
3. Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami. Ujistěte se, že zadáte argumenty ve stejném pořadí, že vlastnost definuje odpovídající parametry.  
  
 Hodnota vlastnosti podílí na výraz, stejně jako proměnné by – konstanta nebo je uložen v proměnné nebo vlastnosti na levé straně příkazu přiřazení.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
