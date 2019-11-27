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
Můžete vytvořit dokument XML, fragment nebo element přímo v kódu pomocí literálu XML. Příklady v tomto tématu ukazují, jak vytvořit element XML, který má tři podřízené prvky a jak vytvořit dokument XML.  
  
 K vytváření objektů [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete použít taky rozhraní [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API. Další informace najdete v tématu <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Vytvoření elementu XML  
  
- Vytvořte XML inline pomocí syntaxe literálu XML, která je stejná jako skutečná syntaxe XML.  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     Spusťte kód. Výstup tohoto kódu je:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Vytvoření dokumentu XML  
  
- Vytvořte vložený dokument XML. Následující kód vytvoří dokument XML, který má syntaxi literálu, deklaraci XML, instrukci zpracování, komentář a prvek, který obsahuje jiný element.  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     Spusťte kód. Výstup tohoto kódu je:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Viz také:

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Vytváření XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
