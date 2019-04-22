---
title: 'Postupy: Vytváření literálů XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 836ec4390e7675effe57c75c79768272d66925a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836857"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Postupy: Vytváření literálů XML (Visual Basic)
Dokument XML, fragment nebo element můžete vytvořit přímo v kódu pomocí literálů XML. Příklady v tomto tématu ukazují, jak vytvořit element XML, který obsahuje tři podřízené prvky a vytvořit dokument XML.  
  
 Můžete také použít [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozhraní API k vytvoření [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objekty. Další informace naleznete v tématu <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Chcete-li vytvořit XML element  
  
-   Vytvořte vložený kód XML pomocí syntaxe literálu XML, který je stejný jako skutečný syntaxe jazyka XML.  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     Spusťte kód. Výstup tohoto kódu je následující:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Chcete-li vytvořit dokument XML  
  
-   Vytvořte vložený dokument XML. Následující kód vytvoří dokument XML, který má literálu syntaxi deklarace XML, instrukce pro zpracování, komentáře a element, který obsahuje jiný prvek.  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     Spusťte kód. Výstup tohoto kódu je následující:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Viz také:

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
