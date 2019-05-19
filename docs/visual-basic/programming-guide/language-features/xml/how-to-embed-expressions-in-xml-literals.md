---
title: 'Postupy: Vložení výrazů do literálů XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 9d0fd1e3713dc5b81cfca0ce54b571b38e648f87
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879102"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Postupy: Vložení výrazů do literálů XML (Visual Basic)
Literály XML lze kombinovat s vložené výrazy pro vytvoření dokumentu XML, fragment nebo element, který obsahuje obsah vytvořený v době běhu. Následující příklady ukazují, jak používat vložené výrazy k naplnění obsah elementu, atributy a názvy elementů v době běhu.  
  
 Syntaxe pro vložený výraz je `<%=` `exp` `%>`, což je stejné syntaxe, která používá ASP.NET. Další informace najdete v tématu [vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Můžete také použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API k vytvoření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty. Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-insert-text-as-element-content"></a>Chcete-li vložit textového obsahu elementu  
  
- Následující příklad ukazuje, jak vložit text, který je součástí `contactName` mezi prvky a na konci názvu proměnné.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     Tento příklad vytvoří následující výstup:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Chcete-li vložit text hodnotu atributu  
  
- Následující příklad ukazuje, jak vložit text, který je součástí `phoneType` jako hodnotu proměnné `type` atribut.  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     Tento příklad vytvoří následující výstup:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Chcete-li vložit text pro název elementu  
  
- Následující příklad ukazuje, jak vložit text, který je součástí `elementName` proměnné jako název elementu.  
  
     Při vytváření elementů tímto způsobem, je nutné zavřít jim \</ > značky.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     Tento příklad vytvoří následující výstup:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytváření literálů XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [Vložené výrazy v XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
