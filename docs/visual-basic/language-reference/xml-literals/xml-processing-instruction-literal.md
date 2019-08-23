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
ms.openlocfilehash: c589d3f4ac6bbb9aa9b2b8f2535888bddbf9c934
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958484"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Literál instrukcí pro zpracování XML (Visual Basic)
Literál představující <xref:System.Xml.Linq.XProcessingInstruction> objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Součásti  
 `<?`  
 Povinný parametr. Označuje začátek literálu instrukcí pro zpracování XML.  
  
 `piName`  
 Povinný parametr. Název, který určuje, která aplikace cílí na zpracování instrukcí. Nelze začínat řetězcem "XML" nebo "XML".  
  
 `piData`  
 Volitelný parametr. Řetězec určující, jak aplikace, na `piName` kterou cílí, by měla zpracovat dokument XML.  
  
 `?>`  
 Povinný parametr. Označuje konec instrukce pro zpracování.  
  
## <a name="return-value"></a>Návratová hodnota  
 <xref:System.Xml.Linq.XProcessingInstruction> Objekt.  
  
## <a name="remarks"></a>Poznámky  
 Literály instrukcí pro zpracování XML označují, jak by měly aplikace zpracovat dokument XML. Když aplikace načte dokument XML, aplikace může ověřit instrukce pro zpracování XML a určit, jak se má dokument zpracovat. Aplikace interpretuje význam `piName` a `piData`.  
  
 Literál dokumentu XML používá syntaxi, která je podobná jako instrukce pro zpracování XML. Další informace naleznete v tématu [literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
> `piName` Element nemůže začínat řetězcem "XML" nebo "XML", protože specifikace XML 1,0 si tyto identifikátory vyhrazuje.  
  
 Literál instrukcí pro zpracování XML můžete přiřadit proměnné nebo ji zahrnout do literálu dokumentu XML.  
  
> [!NOTE]
> Literál XML může zahrnovat více řádků bez nutnosti znaků pro pokračování řádku. To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.  
  
 Kompilátor Visual Basic převádí literál instrukcí pro zpracování XML na volání <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří instrukci pro zpracování identifikující šablonu stylů dokumentu XML.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XProcessingInstruction>
- [Literál dokumentu XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literály XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Vytváření XML v Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
