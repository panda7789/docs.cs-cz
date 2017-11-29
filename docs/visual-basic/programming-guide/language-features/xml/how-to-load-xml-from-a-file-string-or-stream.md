---
title: "Postupy: Načtení XML ze souboru, řetězce nebo proudu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 572e34b1cd4813fad35e6afaf2ec3d0d9dac470a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [XML – literály](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Zacházení s XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
