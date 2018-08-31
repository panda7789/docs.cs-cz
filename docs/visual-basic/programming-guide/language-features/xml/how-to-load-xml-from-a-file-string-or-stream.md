---
title: 'Postupy: Načtení XML ze souboru, řetězce nebo proudu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 241f6552e46d7689b42a409ba44bc747984773ca
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258401"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Postupy: Načtení XML ze souboru, řetězce nebo proudu (Visual Basic)
Můžete vytvořit [literály XML](../../../../visual-basic/language-reference/xml-literals/index.md) a naplníte je obsah z externího zdroje, jako je například souboru, řetězce nebo proudu pomocí několika metod. Tyto metody jsou uvedeny v následujících příkladech.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a>Načtení XML ze souboru  
  
-   K naplnění literálu jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt ze souboru, použijte `Load` metody. Tato metoda může trvat cesta k souboru, textového datového proudu nebo datový proud XML jako vstup.  
  
     Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metoda k naplnění <xref:System.Xml.Linq.XDocument> objektu s jazykem XML z textového souboru.  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a>Načtení XML z řetězce  
  
-   K naplnění literálu jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt z řetězce, můžete použít `Parse` metody.  
  
     Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metoda k naplnění <xref:System.Xml.Linq.XDocument> objekt s XML z řetězce.  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a>Načtení z datový proud XML  
  
-   K naplnění literálu jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objektu z datového proudu, můžete použít `Load` – metoda nebo <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> metody.  
  
 Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XNode.ReadFrom%2A> metoda k naplnění <xref:System.Xml.Linq.XDocument> objektu s jazykem XML z datový proud XML.  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [Literály XML](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Manipulace s kódem XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
