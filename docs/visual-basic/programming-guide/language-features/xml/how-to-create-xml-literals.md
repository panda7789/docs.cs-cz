---
title: 'Postupy: Vytváření literálů XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: e5f8429b3ff02678bf8bf3e9e32bef6eb1a56831
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Postupy: Vytváření literálů XML (Visual Basic)
Můžete vytvořit dokument XML, fragment nebo element přímo v kódu pomocí literál XML. V příkladech v tomto tématu ukazují, jak vytvořit element XML, který má tři podřízené elementy a jak vytvořit dokument XML.  
  
 Můžete také [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API pro vytvoření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty. Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Chcete-li vytvořit XML element  
  
-   Vytvořte vložený XML pomocí syntaxe literál XML, který je stejný jako skutečný syntaxe jazyka XML.  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     Spusťte kód. Výstup tohoto kódu je:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Chcete-li vytvořit dokument XML  
  
-   Vytvořte vložený dokument XML. Následující kód vytvoří dokument XML, který má literálu syntaxe, deklarace XML, pokyny pro zpracování, komentáře a elementu, který obsahuje jiný element.  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     Spusťte kód. Výstup tohoto kódu je:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Viz také  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
