---
title: 'Postupy: Načtení XML ze souboru, řetězce nebo proudu'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7a2a0513a066ae8ea8a70f7a5ae340ab29de7d25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330964"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Postupy: Načtení XML ze souboru, řetězce nebo proudu (Visual Basic)

Můžete vytvořit [literály XML](../../../../visual-basic/language-reference/xml-literals/index.md) a naplnit je obsahem z externího zdroje, jako je například soubor, řetězec nebo datový proud pomocí několika metod. Tyto metody jsou uvedeny v následujících příkladech.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Načtení XML ze souboru

Chcete-li naplnit literál XML, jako je například <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt ze souboru, použijte metodu `Load`. Tato metoda může jako vstup přijmout cestu k souboru, textový Stream nebo datový proud XML.

Následující příklad kódu ukazuje použití metody <xref:System.Xml.Linq.XDocument.Load%28System.String%29> k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z textového souboru.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Načtení XML z řetězce

Chcete-li naplnit literál XML, jako je například <xref:System.Xml.Linq.XElement> nebo objekt <xref:System.Xml.Linq.XDocument> z řetězce, lze použít metodu `Parse`.

Následující příklad kódu ukazuje použití metody <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z řetězce.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Načtení XML z datového proudu

Chcete-li naplnit literál XML, jako je například <xref:System.Xml.Linq.XElement> nebo <xref:System.Xml.Linq.XDocument> objekt z datového proudu, lze použít metodu `Load` nebo metodu <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>.

Následující příklad kódu ukazuje použití metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z datového proudu XML.

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [Literály XML](../../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Manipulace s XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
