---
title: 'Postupy: Načtení XML ze souboru, řetězce nebo datového proudu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: ba88ae19abc216a318d6c2069ab0846d5db8a346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054168"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Postupy: Načtení XML ze souboru, řetězce nebo datového proudu (Visual Basic)

Můžete vytvořit [literály XML](../../../../visual-basic/language-reference/xml-literals/index.md) a naplnit je obsahem z externího zdroje, jako je například soubor, řetězec nebo datový proud pomocí několika metod. Tyto metody jsou uvedeny v následujících příkladech.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Načtení XML ze souboru

K naplnění literálu XML jako <xref:System.Xml.Linq.XElement> objektu <xref:System.Xml.Linq.XDocument> nebo ze souboru použijte `Load` metodu. Tato metoda může jako vstup přijmout cestu k souboru, textový Stream nebo datový proud XML.

Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metody k <xref:System.Xml.Linq.XDocument> naplnění objektu XML z textového souboru.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Načtení XML z řetězce

K naplnění literálu XML <xref:System.Xml.Linq.XElement> `Parse` , jako <xref:System.Xml.Linq.XDocument> je například objekt nebo z řetězce, lze použít metodu.

Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metody k <xref:System.Xml.Linq.XDocument> naplnění objektu XML z řetězce.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Načtení XML z datového proudu

Chcete-li naplnit literál XML jako <xref:System.Xml.Linq.XElement> objekt <xref:System.Xml.Linq.XDocument> nebo z datového proudu `Load` , můžete <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> použít metodu nebo metodu.

Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody k <xref:System.Xml.Linq.XDocument> naplnění objektu XML z datového proudu XML.

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
