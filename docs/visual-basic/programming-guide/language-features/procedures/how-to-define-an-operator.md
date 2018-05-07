---
title: 'Postupy: Definice operátora (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: c759ebf38ab0727aeada218d288b5ac01e3ecd03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-an-operator-visual-basic"></a>Postupy: Definice operátora (Visual Basic)
Pokud jste definovali třídu nebo strukturu, můžete definovat chování standardní operátor (například `*`, `<>`, nebo `And`) Pokud je jedna nebo obě sady operandy typu třídu nebo strukturu.  
  
 Definujte standardní operátor jako procedury operátora v rámci třídu nebo strukturu. Musí být všechny postupy operátor `Public` `Shared`.  
  
 Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je definován `+` názvem operátor pro strukturu `height`. Struktura používá výšky měřená v stopy a palce. Jeden *palec* je 2,54 cm a jeden */zápatí* je 12 palců. Aby normalizovaný hodnoty (palce < 12.0), provede konstruktoru *modulo* aritmetické 12. `+` Operátor používá ke generování hodnot normalizovaný konstruktoru.  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 Můžete otestovat strukturu `height` následujícím kódem.  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 Další informace a příklady naleznete v tématu [operátor přetížení Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Viz také  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: Definice operátoru převodu](./how-to-define-a-conversion-operator.md)  
 [Postupy: Volání procedury operátoru](./how-to-call-an-operator-procedure.md)  
 [Postupy: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md)  
 [Příkaz Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Postupy: Definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Operátor Mod](../../../../visual-basic/language-reference/operators/mod-operator.md)
