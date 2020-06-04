---
title: Literál dokumentu XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: 3a2182d2937827bc8dc45e22307a3668420261a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400199"
---
# <a name="xml-document-literal-visual-basic"></a>Literál dokumentu XML (Visual Basic)
Literál představující <xref:System.Xml.Linq.XDocument> objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`encoding`|Nepovinný parametr. Textový literál, který deklaruje, který kódování dokumentu používá.|  
|`standalone`|Nepovinný parametr. Textový literál Musí být "Ano" nebo "ne".|  
|`piCommentList`|Nepovinný parametr. Seznam instrukcí pro zpracování XML a komentářů XML Má následující formát:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Každá `piComment` z těchto možností může být jedna z následujících:<br /><br /> -   [Literál instrukcí pro zpracování XML](xml-processing-instruction-literal.md)<br />-   [Literál komentáře XML](xml-comment-literal.md)|  
|`rootElement`|Povinná hodnota. Kořenový element dokumentu Formát je jeden z následujících:<br /><br /> <ul><li>[Literál elementu XML](xml-element-literal.md).</li><li>Vložený `<%=` výraz formuláře `elementExp` `%>` `elementExp`Vrátí jednu z následujících možností:<br /><br /> <ul><li>Objekt <xref:System.Xml.Linq.XElement>.</li><li>Kolekce, která obsahuje jeden <xref:System.Xml.Linq.XElement> objekt a libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> objektů a <xref:System.Xml.Linq.XComment> .</li></ul></li></ul><br /> Další informace najdete v tématu [vložené výrazy v XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt <xref:System.Xml.Linq.XDocument>.  
  
## <a name="remarks"></a>Poznámky  
 Literál dokumentu XML je identifikován deklarací XML na začátku literálu. I když každý literál dokumentu XML musí mít přesně jeden kořenový element XML, může mít libovolný počet instrukcí pro zpracování XML a komentáře XML.  
  
 Literál dokumentu XML nemůže být použit v elementu XML.  
  
> [!NOTE]
> Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku. To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.  
  
 Kompilátor Visual Basic převádí literál dokumentu XML na volání <xref:System.Xml.Linq.XDocument.%23ctor%2A> <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktorů a.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dokument XML, který má deklaraci XML, instrukci zpracování, komentář a prvek, který obsahuje jiný element.  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [Literál instrukcí pro zpracování XML](xml-processing-instruction-literal.md)
- [Literál komentáře XML](xml-comment-literal.md)
- [Literál XML elementu](xml-element-literal.md)
- [Literály XML](index.md)
- [Vytvoření XML v jazyce Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Vložené výrazy v XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
