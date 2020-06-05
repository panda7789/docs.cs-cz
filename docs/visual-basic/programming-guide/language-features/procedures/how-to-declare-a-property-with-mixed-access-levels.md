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
ms.openlocfilehash: f0f7aba25888544dfcc093906850ae7ada621182
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388242"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu (Visual Basic)
Pokud chcete, aby `Get` `Set` procedury a u vlastnosti měly různé úrovně přístupu, můžete použít přísnější úroveň v `Property` příkazu a více omezující úroveň v `Get` `Set` příkazu or. Smíšené úrovně přístupu lze použít pro vlastnost, pokud chcete, aby určité části kódu byly schopny získat hodnotu vlastnosti, a některé další části kódu budou moci změnit hodnotu.  
  
 Další informace o úrovních přístupu najdete v tématu [úrovně přístupu v Visual Basic](../declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Deklarace vlastnosti se smíšenými úrovněmi přístupu  
  
1. Deklarujte vlastnost normálním způsobem a určete méně omezující úroveň přístupu (například `Public` ) v `Property` příkazu.  
  
2. Deklarujte buď `Get` nebo `Set` proceduru, která určuje více omezující úroveň přístupu (například `Friend` ).  
  
3. Nezadávejte úroveň přístupu pro druhý postup vlastnosti. Předpokládá úroveň přístupu deklarovanou v `Property` příkazu. Přístup můžete omezit pouze na jeden z procedur vlastností.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     V předchozím příkladu `Get` má procedura stejný `Protected` přístup jako vlastnost samotnou, zatímco `Set` procedura má `Private` přístup. Třída odvozená z `employee` může číst `salary` hodnotu, ale `employee` může ji nastavit pouze třída.  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Property – příkaz](../../../language-reference/statements/property-statement.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
