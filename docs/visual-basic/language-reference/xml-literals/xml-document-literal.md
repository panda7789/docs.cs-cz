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
ms.openlocfilehash: f58c1365e145166dfe122d455854d44526300a1e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814624"
---
# <a name="xml-document-literal-visual-basic"></a>Literál dokumentu XML (Visual Basic)
Literál představující <xref:System.Xml.Linq.XDocument> objektu.  
  
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
|`encoding`|Volitelné. Deklarace kódování, které používá dokumentu prostý text.|  
|`standalone`|Volitelné. Prostý text. Musí být "Ano" nebo "Ne".|  
|`piCommentList`|Volitelné. Seznam pokyny pro zpracování XML a komentáře XML. Má následující formát:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Každý `piComment` může být jedna z následujících akcí:<br /><br /> -   [Literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [Literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Povinný parametr. Kořenový element dokumentu. Formát je jeden z následujících akcí:<br /><br /> <ul><li>[Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Vložený výraz ve tvaru `<%=` `elementExp` `%>`. `elementExp` Vrátí jednu z následujících akcí:<br /><br /> <ul><li><xref:System.Xml.Linq.XElement> Objektu.</li><li>Kolekce, která obsahuje jeden <xref:System.Xml.Linq.XElement> objektu a libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> a <xref:System.Xml.Linq.XComment> objekty.</li></ul></li></ul><br /> Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XDocument> Objektu.  
  
## <a name="remarks"></a>Poznámky  
 Literál dokumentu XML je identifikován deklarace XML na začátek literálu. I když každá literál dokumentu XML musí mít přesně jeden kořenový element XML, může mít libovolný počet pokyny pro zpracování XML a komentáře XML.  
  
 Literál dokumentu XML se nemůže objevit v elementu jazyka XML.  
  
> [!NOTE]
>  Literál XML může zahrnovat více řádků bez použití znaků pokračování řádku. To umožňuje kopírovat obsah z dokumentu XML a vložte ho přímo do programu Visual Basic.  
  
 Kompilátor jazyka Visual Basic převede literál dokumentu XML na volání <xref:System.Xml.Linq.XDocument.%23ctor%2A> a <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktory.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dokument XML, který má deklarace XML, instrukce pro zpracování, komentáře a element, který obsahuje jiný prvek.  
  
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
- [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
