---
title: 'Postupy: Definice operátora'
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
ms.openlocfilehash: 49b9c8d1a6db56a56b50c16b4a6bb5b928df6c7d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388034"
---
# <a name="how-to-define-an-operator-visual-basic"></a>Postupy: Definice operátora (Visual Basic)
Pokud jste definovali třídu nebo strukturu, můžete definovat chování operátoru standardního (například `*` , `<>` nebo `And` ), pokud jeden nebo oba operandy jsou typu vaší třídy nebo struktury.  
  
 V rámci třídy nebo struktury definujte operátor standardní jako proceduru operátoru. Všechny procedury operátoru musí být `Public` `Shared` .  
  
 Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `+` operátor pro strukturu s názvem `height` . Struktura využívá výšky měřenou v nohou a palcích. Jedna *palec* je 2,54 centimetrů a jedno *chodidlo* je 12 palců. Chcete-li zajistit normalizované hodnoty (palce < 12,0), konstruktor provede *modulo* 12 aritmetické operace. `+`Operátor používá konstruktor ke generování normalizovaných hodnot.  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 Strukturu můžete otestovat `height` pomocí následujícího kódu.  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a>Viz také

- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definice operátoru převodu](./how-to-define-a-conversion-operator.md)
- [Postupy: Volání procedury operátoru](./how-to-call-an-operator-procedure.md)
- [Postupy: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md)
- [Operator – příkaz](../../../language-reference/statements/operator-statement.md)
- [Structure – příkaz](../../../language-reference/statements/structure-statement.md)
- [Postupy: Deklarace struktury](../data-types/how-to-declare-a-structure.md)
- [Mod – operátor](../../../language-reference/operators/mod-operator.md)
