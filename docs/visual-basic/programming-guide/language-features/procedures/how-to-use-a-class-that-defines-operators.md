---
title: 'Postupy: Použití třídy, která definuje operátory (Visual Basic).'
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
ms.openlocfilehash: 7e1d5698c1e83f0adf1be67245e0726aecaabdac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Postupy: Použití třídy, která definuje operátory (Visual Basic).
Pokud používáte třídu nebo strukturu, která definuje vlastní operátory, můžete tyto operátory přistupovat z jazyka Visual Basic.  
  
 Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá strukturu SQL <xref:System.Data.SqlTypes.SqlString>, která definuje operátory převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) v obou směrech mezi řetězec jazyka Visual Basic a řetězec SQL. Použití `CType(` *SQL řetězcového výrazu*, `String)` převést řetězec SQL na řetězec jazyka Visual Basic a `CType(` *řetězcového výrazu jazyka Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` převést opačným směrem.  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <xref:System.Data.SqlTypes.SqlString> Struktura definuje operátora převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` k <xref:System.Data.SqlTypes.SqlString> a jiné z <xref:System.Data.SqlTypes.SqlString> k `String`. Příkaz, který přiřazuje `title` k `jobTitle` využívá první operátor a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> volání funkce používá druhý.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ujistěte se, že třídu nebo strukturu, který používáte definuje operátor, který chcete použít. Nepředpokládejte, že třídu nebo strukturu definovala každých operátor, který je k dispozici pro přetížení. Seznam dostupných operátory najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Zahrnout odpovídající `Imports` příkaz SQL řetězce na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlTypes>).  
  
 Projekt musí mít odkazy na System.Data a System.XML.  
  
## <a name="see-also"></a>Viz také  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: Definice operátoru](./how-to-define-an-operator.md)  
 [Postupy: Definice operátoru převodu](./how-to-define-a-conversion-operator.md)  
 [Postupy: Volání procedury operátoru](./how-to-call-an-operator-procedure.md)  
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Postupy: Definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
