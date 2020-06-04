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
ms.openlocfilehash: 9bd1781e01bc4cbf1ce5da8c454ab2f5a679aead
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400173"
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Literál instrukcí pro zpracování XML (Visual Basic)
Literál představující <xref:System.Xml.Linq.XProcessingInstruction> objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Součásti  
 `<?`  
 Povinná hodnota. Označuje začátek literálu instrukcí pro zpracování XML.  
  
 `piName`  
 Povinná hodnota. Název, který určuje, která aplikace cílí na zpracování instrukcí. Nelze začínat řetězcem "XML" nebo "XML".  
  
 `piData`  
 Nepovinný parametr. Řetězec určující, jak aplikace, na kterou cílí, `piName` by měla zpracovat dokument XML.  
  
 `?>`  
 Povinná hodnota. Označuje konec instrukce pro zpracování.  
  
## <a name="return-value"></a>Návratová hodnota  
 Objekt <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="remarks"></a>Poznámky  
 Literály instrukcí pro zpracování XML označují, jak by měly aplikace zpracovat dokument XML. Když aplikace načte dokument XML, aplikace může ověřit instrukce pro zpracování XML a určit, jak se má dokument zpracovat. Aplikace interpretuje význam `piName` a `piData` .  
  
 Literál dokumentu XML používá syntaxi, která je podobná jako instrukce pro zpracování XML. Další informace naleznete v tématu [literál dokumentu XML](xml-document-literal.md).  
  
> [!NOTE]
> `piName`Element nemůže začínat řetězcem "XML" nebo "XML", protože specifikace xml 1,0 si tyto identifikátory vyhrazuje.  
  
 Literál instrukcí pro zpracování XML můžete přiřadit proměnné nebo ji zahrnout do literálu dokumentu XML.  
  
> [!NOTE]
> Literál XML může zahrnovat více řádků bez nutnosti znaků pro pokračování řádku. To vám umožní zkopírovat obsah z dokumentu XML a vložit ho přímo do Visual Basic programu.  
  
 Kompilátor Visual Basic převádí literál instrukcí pro zpracování XML na volání <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> konstruktoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří instrukci pro zpracování identifikující šablonu stylů dokumentu XML.  
  
 [!code-vb[VbXMLSamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#28)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XProcessingInstruction>
- [Literál dokumentu XML](xml-document-literal.md)
- [Literály XML](index.md)
- [Vytvoření XML v jazyce Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
