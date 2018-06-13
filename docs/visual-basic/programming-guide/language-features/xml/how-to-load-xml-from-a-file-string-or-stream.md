---
title: 'Postupy: Načtení XML ze souboru, řetězce nebo proudu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 241f6552e46d7689b42a409ba44bc747984773ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647628"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Postupy: Načtení XML ze souboru, řetězce nebo proudu (Visual Basic)
Můžete vytvořit [XML – literály](../../../../visual-basic/language-reference/xml-literals/index.md) a naplnit je obsah z externího zdroje například souboru, řetězce nebo datový proud pomocí několika metod. Tyto metody jsou uvedeny v následujících příkladech.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a>K načtení XML ze souboru  
  
-   K naplnění literál jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt ze souboru, použijte `Load` metoda. Tato metoda může trvat cesta k souboru, datový proud text nebo datový proud XML jako vstup.  
  
     Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metoda k naplnění <xref:System.Xml.Linq.XDocument> objekt s XML z textového souboru.  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a>K načtení XML z řetězce  
  
-   K naplnění literál jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt z řetězce, můžete použít `Parse` metoda.  
  
     Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metoda k naplnění <xref:System.Xml.Linq.XDocument> objekt s XML z řetězce.  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a>K načtení XML z datového proudu  
  
-   K naplnění literál jako XML <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objektu z datového proudu, můžete použít `Load` metoda nebo <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> metoda.  
  
 Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XNode.ReadFrom%2A> metoda k naplnění <xref:System.Xml.Linq.XDocument> objekt s XML z datový proud XML.  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [Literály XML](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Zacházení s XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
