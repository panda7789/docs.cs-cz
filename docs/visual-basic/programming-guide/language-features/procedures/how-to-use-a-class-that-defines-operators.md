---
title: "Postupy: Použití třídy, která definuje operátory (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 223b3fc84fe75d1d530cd182c9332e5c663aa519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>Postupy: Použití třídy, která definuje operátory (Visual Basic).
Pokud používáte třídu nebo strukturu, která definuje vlastní operátory, dostanete tyto operátory z [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá strukturu SQL <xref:System.Data.SqlTypes.SqlString>, která definuje operátory převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) v obou směrech mezi řetězec SQL a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] řetězec. Použití `CType(` *SQL řetězcového výrazu*, `String)` převést řetězec SQL tak, aby [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] řetězci a `CType(` *řetězcového výrazu jazyka Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` převést opačným směrem.  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <xref:System.Data.SqlTypes.SqlString> Struktura definuje operátora převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` k <xref:System.Data.SqlTypes.SqlString> a jiné z <xref:System.Data.SqlTypes.SqlString> k `String`. Příkaz, který přiřazuje `title` k `jobTitle` využívá první operátor a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> volání funkce používá druhý.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ujistěte se, že třídu nebo strukturu, který používáte definuje operátor, který chcete použít. Nepředpokládejte, že třídu nebo strukturu definovala každých operátor, který je k dispozici pro přetížení. Seznam dostupných operátory najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
 Zahrnout odpovídající `Imports` příkaz SQL řetězce na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlTypes>).  
  
 Projekt musí mít odkazy na System.Data a System.XML.  
  
## <a name="see-also"></a>Viz také  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: definice operátora](./how-to-define-an-operator.md)  
 [Postupy: definice operátora převodu](./how-to-define-a-conversion-operator.md)  
 [Postupy: volání procedury operátora](./how-to-call-an-operator-procedure.md)  
 [Rozšíření](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Zužující](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure – příkaz](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Postupy: definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
