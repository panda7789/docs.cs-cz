---
title: 'Postupy: Použití třídy, která definuje operátory.'
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
ms.openlocfilehash: 455c839702b90738ec5aea37c1b09d72eba42ff4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347882"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Postupy: Použití třídy, která definuje operátory (Visual Basic).
Pokud používáte třídu nebo strukturu, která definuje své vlastní operátory, můžete k těmto operátorům přistupovat z Visual Basic.  
  
 Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad přistupuje k struktuře SQL <xref:System.Data.SqlTypes.SqlString>, která definuje operátory převodu ([funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) v obou směrech mezi řetězcem SQL a řetězcem Visual Basic. Použijte `CType(`*řetězcového výrazu SQL*, `String)` pro převod řetězce sql na Visual Basic řetězec a `CType(`*Visual Basic řetězcového výrazu*, <xref:System.Data.SqlTypes.SqlString>`)` pro převod v druhém směru.  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 Struktura <xref:System.Data.SqlTypes.SqlString> definuje operátor převodu ([CType funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` na <xref:System.Data.SqlTypes.SqlString> a další od <xref:System.Data.SqlTypes.SqlString> až po `String`. Příkaz, který přiřazuje `title` pro `jobTitle` používá první operátor a volání funkce <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> používá sekundu.  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Ujistěte se, že třída nebo struktura, kterou používáte, definuje operátor, který chcete použít. Nepředpokládají, že třída nebo struktura definovala každý operátor, který je k dispozici pro přetížení. Seznam dostupných operátorů naleznete v tématu [příkaz operator](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Zahrňte příslušný příkaz `Imports` pro řetězec SQL na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlTypes>).  
  
 Projekt musí mít odkazy na System. data a System. XML.  
  
## <a name="see-also"></a>Viz také:

- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definice operátoru](./how-to-define-an-operator.md)
- [Postupy: Definice operátoru převodu](./how-to-define-a-conversion-operator.md)
- [Postupy: Volání procedury operátoru](./how-to-call-an-operator-procedure.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Postupy: Definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
