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
ms.openlocfilehash: 6ced9e2ab71ccb00c9ce3495e38d895a7104fdde
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738653"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Postupy: Definice operátora (Visual Basic)
Pokud jste definovali třídy nebo struktury, můžete definovat chování standardní – operátor (například `*`, `<>`, nebo `And`) Pokud je jeden nebo oba operandy typu třídy nebo struktury.  
  
 Standardní operátor definujte jako procedury operátora v rámci třídy nebo struktury. Musí být všechny procedury operátoru `Public` `Shared`.  
  
 Definování v třídě nebo struktuře operátor se také nazývá *přetížení* operátor.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `+` volat operátor pro strukturu `height`. Struktura používá měřené v stopy a palce výšky. Jeden *palec* je 2,54 cm a jedno *zápatí* 12 palců. Aby bylo zajištěno normalizované hodnoty (palce < 12.0), konstruktor provádí *modulo* aritmetické 12. `+` Operátor používá konstruktor k vygenerování normalizované hodnoty.  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 Můžete otestovat strukturu `height` následujícím kódem.  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
  
## <a name="see-also"></a>Viz také:
- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definice operátora převodu](./how-to-define-a-conversion-operator.md)
- [Postupy: Volání procedury operátora](./how-to-call-an-operator-procedure.md)
- [Postupy: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md)
- [Příkaz Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Postupy: Deklarace struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Operátor Mod](../../../../visual-basic/language-reference/operators/mod-operator.md)
