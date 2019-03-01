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
ms.openlocfilehash: 1906c9101f9a53bde13698d0ed17b7b8d0988c1d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981371"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Literál instrukcí pro zpracování XML (Visual Basic)
Literál představující <xref:System.Xml.Linq.XProcessingInstruction> objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Součásti  
 `<?`  
 Povinný parametr. Označuje začátek instrukce zpracování XML literál.  
  
 `piName`  
 Povinný parametr. Jméno označující aplikaci, pro kterou zpracování instrukcí cíle. Nesmí začínat znakem "xml" nebo "XML".  
  
 `piData`  
 Volitelné. Řetězec určující, jak aplikace cílem `piName` by měl zpracovat dokument XML.  
  
 `?>`  
 Povinný parametr. Označuje konec instrukce ke zpracování.  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XProcessingInstruction> Objektu.  
  
## <a name="remarks"></a>Poznámky  
 Literály instrukce zpracování XML určit, jak aplikace by měl zpracovat dokument XML. Když aplikace načte dokument XML, aplikace může kontrolovat pokyny pro zpracování XML k určení způsobu zpracování dokumentu. Aplikace interpretuje význam `piName` a `piData`.  
  
 Literál dokumentu XML používá syntaxe, která je podobná instrukce zpracování XML. Další informace najdete v tématu [literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
>  `piName` Elementu nemůže začínat řetězce "xml" nebo "XML", protože tyto identifikátory specifikace XML 1.0.  
  
 Můžete přiřadit proměnné literál instrukce zpracování XML nebo zahrnout do literál dokumentu XML.  
  
> [!NOTE]
>  Literál XML může zahrnovat více řádků bez nutnosti znaky pokračování řádku. To umožňuje kopírovat obsah z dokumentu XML a vložte ho přímo do programu Visual Basic.  
  
 Kompilátor jazyka Visual Basic převede instrukce zpracování XML literál na volání <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří zpracování instrukcí identifikující šablony stylů pro dokument XML.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Xml.Linq.XProcessingInstruction>
- [Literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytvoření XML v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
