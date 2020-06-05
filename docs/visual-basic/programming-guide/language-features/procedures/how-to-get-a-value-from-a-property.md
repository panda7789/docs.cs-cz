---
title: 'Postupy: Získání hodnoty z vlastnosti'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 2c92cd4a869acbb7c8c52fbf4117112967386498
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387891"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Postupy: Získání hodnoty z vlastnosti (Visual Basic)
Hodnotu vlastnosti načtete tak, že zahrnete název vlastnosti do výrazu.  
  
 `Get`Procedura vlastnosti načte hodnotu, ale explicitně ji nevoláte podle názvu. Vlastnost použijete stejně, jako byste použili proměnnou. Visual Basic provede volání procedur vlastností.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>Načtení hodnoty z vlastnosti  
  
1. Použijte název vlastnosti ve výrazu stejným způsobem, jako byste použili název proměnné. Vlastnost můžete použít všude, kde můžete použít proměnnou nebo konstantu.  
  
     -nebo-  
  
     Použijte název vlastnosti za znaménkem EQUAL ( `=` ) v příkazu přiřazení.  
  
     Následující příklad přečte hodnotu `Now` vlastnosti Visual Basic, implicitně volá její `Get` proceduru.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Pokud vlastnost přebírá argumenty, uveďte seznam argumentů tak, že postupujete podle názvu vlastnosti s závorkami. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.  
  
3. Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami. Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém vlastnost definuje odpovídající parametry.  
  
 Hodnota vlastnosti se účastní ve výrazu stejně jako proměnná nebo konstanta nebo je uložena v proměnné nebo vlastnosti na levé straně příkazu přiřazení.  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Property – příkaz](../../../language-reference/statements/property-statement.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
