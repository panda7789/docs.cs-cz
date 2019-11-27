---
title: 'Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349687"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu (Visual Basic)
Pokud chcete, aby `Get` a `Set` postupy u vlastnosti měly různé úrovně přístupu, můžete použít přísnější úroveň v příkazu `Property` a více omezující úroveň v příkazu `Get` nebo `Set`. Smíšené úrovně přístupu lze použít pro vlastnost, pokud chcete, aby určité části kódu byly schopny získat hodnotu vlastnosti, a některé další části kódu budou moci změnit hodnotu.  
  
 Další informace o úrovních přístupu najdete v tématu [úrovně přístupu v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Deklarace vlastnosti se smíšenými úrovněmi přístupu  
  
1. Deklarujte vlastnost normálním způsobem a v příkazu `Property` určete úroveň přístupu s méně omezujícími možnostmi (například `Public`).  
  
2. Deklarujte buď `Get`, nebo `Set` proceduru, která určuje více omezující úroveň přístupu (například `Friend`).  
  
3. Nezadávejte úroveň přístupu pro druhý postup vlastnosti. Předpokládá úroveň přístupu deklarovanou v příkazu `Property`. Přístup můžete omezit pouze na jeden z procedur vlastností.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     V předchozím příkladu má procedura `Get` stejný `Protected` přístup jako vlastnost, zatímco `Set` procedura má `Private` přístup. Třída odvozená z `employee` může číst hodnotu `salary`, ale může ji nastavit pouze třída `employee`.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Rozdíly mezi vlastnostmi a proměnnými v Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
