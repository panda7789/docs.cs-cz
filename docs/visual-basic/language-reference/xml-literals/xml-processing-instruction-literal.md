---
title: Literál instrukcí pro zpracování XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: e6d4c200822f58c7dbe5bf423282740d4aa86ac3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604130"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Literál instrukcí pro zpracování XML (Visual Basic)
Literál představující <xref:System.Xml.Linq.XProcessingInstruction> objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Součásti  
 `<?`  
 Požadováno. Označuje začátek XML literál instrukcí pro zpracování.  
  
 `piName`  
 Požadováno. Název označující, která aplikace cíle instrukcí pro zpracování. Nemůže začínat řetězcem "xml" nebo "XML".  
  
 `piData`  
 Volitelné. Řetězec určující, jak aplikaci cílem `piName` by měl zpracovat v dokumentu XML.  
  
 `?>`  
 Požadováno. Označuje konec pokyny pro zpracování.  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XProcessingInstruction> Objektu.  
  
## <a name="remarks"></a>Poznámky  
 XML – literály instrukce zpracování označuje, jak by měla aplikace zpracovat dokument XML. Pokud aplikace načte dokument XML, aplikace můžete zkontrolovat pokyny pro zpracování XML určit, jak zpracovat dokumentu. Aplikace interpretuje význam `piName` a `piData`.  
  
 Literál dokumentu XML používá syntaxi, která je podobná pokyny pro zpracování XML. Další informace najdete v tématu [literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
>  `piName` Element nemůže začínat číslem řetězce "xml" nebo "XML", protože specifikace XML 1.0 si vyhrazuje tyto identifikátory.  
  
 Můžete přiřadit XML literál instrukcí pro zpracování proměnné nebo její zahrnutí do literál dokumentu XML.  
  
> [!NOTE]
>  Literál XML může zahrnovat více řádků bez nutnosti znaky pokračování řádku. To umožňuje kopírovat obsah z dokumentu XML a vložte jej přímo do programu Visual Basic.  
  
 Visual Basic – kompilátor převede XML literál instrukcí pro zpracování volání <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktor.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří instrukce pro zpracování identifikace šablonu stylů pro dokument XML.  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [Literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
