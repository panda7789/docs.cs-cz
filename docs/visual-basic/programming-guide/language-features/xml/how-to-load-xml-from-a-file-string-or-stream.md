---
title: 'Postupy: Načtení XML ze souboru, řetězce nebo proudu'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7f2a961ebb7ecd4fc0512e141b4a437be87bec0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392285"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Postupy: Načtení XML ze souboru, řetězce nebo proudu (Visual Basic)

Můžete vytvořit [literály XML](../../../language-reference/xml-literals/index.md) a naplnit je obsahem z externího zdroje, jako je například soubor, řetězec nebo datový proud pomocí několika metod. Tyto metody jsou uvedeny v následujících příkladech.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Načtení XML ze souboru

K naplnění literálu XML jako <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objektu nebo ze souboru použijte `Load` metodu. Tato metoda může jako vstup přijmout cestu k souboru, textový Stream nebo datový proud XML.

Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metody k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z textového souboru.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Načtení XML z řetězce

K naplnění literálu XML, jako je například <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objekt nebo z řetězce, lze použít `Parse` metodu.

Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metody k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z řetězce.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Načtení XML z datového proudu

Chcete-li naplnit literál XML jako <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> objekt nebo z datového proudu, můžete použít `Load` metodu nebo <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> metodu.

Následující příklad kódu ukazuje použití <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody k naplnění <xref:System.Xml.Linq.XDocument> objektu XML z datového proudu XML.

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [Literály XML](../../../language-reference/xml-literals/index.md)
- [XML](index.md)
- [Zacházení s XML v jazyce Visual Basic](manipulating-xml.md)
