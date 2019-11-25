---
title: 'Postupy: Vytváření literálů XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: e3af5185d2c2106e6a696a6569ef59897d0f1fe1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333005"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Postupy: Vytváření literálů XML (Visual Basic)
You can create an XML document, fragment, or element directly in code by using an XML literal. The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.  
  
 You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects. Další informace najdete v tématu <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>To create an XML element  
  
- Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     Run the code. The output of this code is:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>To create an XML document  
  
- Create the XML document inline. The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     Run the code. The output of this code is:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Viz také:

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
