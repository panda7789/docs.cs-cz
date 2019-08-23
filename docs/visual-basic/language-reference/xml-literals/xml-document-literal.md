---
title: Literál dokumentu XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: 8a489be46295c213b7a8b355eb3c9786d49dd8f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958505"
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
  
|Termín|Definice|  
|---|---|  
|`encoding`|Volitelný parametr. Textový literál, který deklaruje, který kódování dokumentu používá.|  
|`standalone`|Volitelný parametr. Textový literál Musí být "Ano" nebo "ne".|  
|`piCommentList`|Volitelný parametr. Seznam instrukcí pro zpracování XML a komentářů XML Má následující formát:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Každá `piComment` z těchto možností může být jedna z následujících:<br /><br /> -   [Literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)<br />-   [Literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)|  
|`rootElement`|Povinný parametr. Kořenový element dokumentu Formát je jeden z následujících:<br /><br /> <ul><li>[Literál elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Vložený výraz formuláře `<%=` `elementExp` `%>` `elementExp` Vrátí jednu z následujících možností:<br /><br /> <ul><li><xref:System.Xml.Linq.XElement> Objekt.</li><li>Kolekce, která obsahuje jeden <xref:System.Xml.Linq.XElement> objekt a libovolný <xref:System.Xml.Linq.XProcessingInstruction> počet objektů a <xref:System.Xml.Linq.XComment> .</li></ul></li></ul><br /> Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XDocument> Objekt.  
  
## <a name="remarks"></a>Poznámky  
 Literál dokumentu XML je identifikován deklarací XML na začátku literálu. I když každý literál dokumentu XML musí mít přesně jeden kořenový element XML, může mít libovolný počet instrukcí pro zpracování XML a komentáře XML.  
  
 Literál dokumentu XML nemůže být použit v elementu XML.  
  
> [!NOTE]
> Literál XML může zahrnovat více řádků bez použití znaků pro pokračování řádku. To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.  
  
 Kompilátor Visual Basic převádí literál dokumentu XML na volání <xref:System.Xml.Linq.XDocument.%23ctor%2A> konstruktorů a. <xref:System.Xml.Linq.XDeclaration.%23ctor%2A>  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dokument XML, který má deklaraci XML, instrukci zpracování, komentář a prvek, který obsahuje jiný element.  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [Literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [Literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
