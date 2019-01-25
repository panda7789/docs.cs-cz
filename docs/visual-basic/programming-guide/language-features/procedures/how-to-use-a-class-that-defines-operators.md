---
title: 'Postupy: Použití třídy, která definuje operátory (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 372d3f663109597fc2d25c5d75a9efa6b3648682
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640670"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Postupy: Použití třídy, která definuje operátory (Visual Basic)
Pokud používáte třídu nebo strukturu, která definuje vlastní operátory, můžete tyto operátory přistupovat z jazyka Visual Basic.  
  
 Definování v třídě nebo struktuře operátor se také nazývá *přetížení* operátor.  
  
## <a name="example"></a>Příklad  
 Následující příklad přistupuje k SQL struktura <xref:System.Data.SqlTypes.SqlString>, která definuje operátory převodu ([funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) v obou směrech mezi řetězec jazyka Visual Basic a řetězec SQL. Použití `CType(` *SQL řetězcového výrazu*, `String)` pro převod řetězce SQL na řetězec jazyka Visual Basic a `CType(` *výraz řetězce jazyka Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` pro převod opačným směrem.  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <xref:System.Data.SqlTypes.SqlString> Struktury definuje operátor převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` k <xref:System.Data.SqlTypes.SqlString> a druhý z <xref:System.Data.SqlTypes.SqlString> k `String`. Příkaz, který přiřazuje `title` k `jobTitle` využívá první operátor a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> druhý používá volání funkce.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ujistěte se, že třídy nebo struktury, které používáte definuje operátor, který chcete použít. Nepředpokládejte, že každý operátor, který je k dispozici pro přetížení definoval třídy nebo struktury. Seznam dostupných operátorů najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Zahrnout odpovídající `Imports` příkaz pro řetězec SQL na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlTypes>).  
  
 Váš projekt musí obsahovat odkazy na System.Data a System.XML.  
  
## <a name="see-also"></a>Viz také:
- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definovat operátor](./how-to-define-an-operator.md)
- [Postupy: Definice operátora převodu](./how-to-define-a-conversion-operator.md)
- [Postupy: Volání procedury operátora](./how-to-call-an-operator-procedure.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Postupy: Deklarace struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
