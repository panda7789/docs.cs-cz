---
title: Literál instrukcí pro zpracování XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
ms.openlocfilehash: 3602a81feae9287a77d060bb46f10eefee4fc05d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347036"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Literál instrukcí pro zpracování XML (Visual Basic)
Literál představující objekt <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Součásti  
 `<?`  
 Požadováno. Označuje začátek literálu instrukcí pro zpracování XML.  
  
 `piName`  
 Požadováno. Název, který určuje, která aplikace cílí na zpracování instrukcí. Nelze začínat řetězcem "XML" nebo "XML".  
  
 `piData`  
 Volitelná. Řetězec, který označuje, jak aplikace, na kterou cílí `piName`, by měla zpracovat dokument XML.  
  
 `?>`  
 Požadováno. Označuje konec instrukce pro zpracování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="remarks"></a>Poznámky  
 Literály instrukcí pro zpracování XML označují, jak by měly aplikace zpracovat dokument XML. Když aplikace načte dokument XML, aplikace může ověřit instrukce pro zpracování XML a určit, jak se má dokument zpracovat. Aplikace interpretuje význam `piName` a `piData`.  
  
 Literál dokumentu XML používá syntaxi, která je podobná jako instrukce pro zpracování XML. Další informace naleznete v tématu [literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
> Element `piName` nemůže začínat řetězcem "XML" nebo "XML", protože specifikace XML 1,0 si tyto identifikátory vyhrazuje.  
  
 Literál instrukcí pro zpracování XML můžete přiřadit proměnné nebo ji zahrnout do literálu dokumentu XML.  
  
> [!NOTE]
> Literál XML může zahrnovat více řádků bez nutnosti znaků pro pokračování řádku. To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.  
  
 Kompilátor Visual Basic převádí literál instrukcí pro zpracování XML na volání konstruktoru <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří instrukci pro zpracování identifikující šablonu stylů dokumentu XML.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XProcessingInstruction>
- [Literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
