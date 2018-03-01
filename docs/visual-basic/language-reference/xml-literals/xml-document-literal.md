---
title: "Literál dokumentu XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 008b5857418a572046797bf061a05f265669d427
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
|`encoding`|Volitelné. Literál text deklarace, které kódování dokumentu používá.|  
|`standalone`|Volitelné. Literál text. Musí být "Ano" nebo "Ne".|  
|`piCommentList`|Volitelné. Seznam příkazů pro zpracování XML a komentáře XML. Má následující formát:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Každý `piComment` může být jedna z následujících akcí:<br /><br /> -   [Literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [Literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Požadováno. Kořenový element dokumentu. Formát je jedním z těchto:<br /><br /> <ul><li>[Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Vložené výrazu ve formátu `<%=` `elementExp` `%>`. `elementExp` Vrátí jednu z následujících akcí:<br /><br /> <ul><li><xref:System.Xml.Linq.XElement> Objektu.</li><li>Kolekce, která obsahuje jednu <xref:System.Xml.Linq.XElement> objekt a libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> a <xref:System.Xml.Linq.XComment> objekty.</li></ul></li></ul><br /> Další informace najdete v tématu [vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XDocument> Objektu.  
  
## <a name="remarks"></a>Poznámky  
 Literál dokumentu XML je identifikována deklaraci XML na začátku literál. I když každý literál dokumentu XML musí mít přesně jeden kořenový element XML, může mít libovolný počet příkazů pro zpracování XML a komentáře XML.  
  
 Literál dokumentu XML se nemůže vyskytovat v elementu XML.  
  
> [!NOTE]
>  Literál XML může zahrnovat více řádků bez použití znaky pokračování řádku. To umožňuje kopírovat obsah z dokumentu XML a vložte ji přímo do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru převede literál dokumentu XML volání <xref:System.Xml.Linq.XDocument.%23ctor%2A> a <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> konstruktory.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dokument XML, který má deklarace XML, pokyny pro zpracování, komentáře a elementu, který obsahuje jiný element.  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 <xref:System.Xml.Linq.XComment>  
 <xref:System.Xml.Linq.XDocument>  
 [Literál instrukcí pro zpracování XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)  
 [Literál komentáře XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [Literál XML elementu](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML – literály](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Vložené výrazy v XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
