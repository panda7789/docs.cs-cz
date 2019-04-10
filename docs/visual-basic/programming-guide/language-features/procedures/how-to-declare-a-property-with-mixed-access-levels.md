---
title: 'Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu (Visual Basic)'
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
ms.openlocfilehash: e899b57e02f492b0e4909aca84c069e5b7688618
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339811"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu (Visual Basic)
Pokud chcete, aby `Get` a `Set` postupy na vlastnost, která má mít různé úrovně přístupu, můžete použít úroveň mnohem mírnější v `Property` příkazu a více omezující úroveň buď `Get` nebo `Set` příkaz. Pokud chcete, aby určité části kódu, abyste mohli získat hodnotu vlastnosti a některých jiných částí kódu budete moci změnit hodnotu použijete u vlastnosti smíšenými úrovněmi přístupu.  
  
 Další informace o úrovních přístupu najdete v části [úrovní v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Deklarace vlastnosti se smíšenými úrovněmi přístupu  
  
1. Deklarovat vlastnost běžným způsobem a zadejte méně omezující úroveň přístupu (například `Public`) v `Property` příkazu.  
  
2. Deklarace některé `Get` nebo `Set` postup určení více omezující úroveň přístupu (například `Friend`).  
  
3. Nezadávejte úroveň přístupu na Další procedura property. Úroveň přístupu, které jsou deklarované v předpokládá `Property` příkazu. Můžete omezit přístup na pouze jednu z vlastností.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     V předchozím příkladu `Get` procedura nemá stejný `Protected` přístup jako vlastnost, zatímco `Set` procedura nemá `Private` přístup. Třída odvozená z `employee` můžete přečíst `salary` hodnotu, ale jenom `employee` třídy můžete ho nastavit.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury Property](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Volání procedury Property](./how-to-call-a-property-procedure.md)
- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
- [Postupy: Postupy: Získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
