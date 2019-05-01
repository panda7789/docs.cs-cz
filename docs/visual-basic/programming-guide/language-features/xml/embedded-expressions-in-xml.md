---
title: Vložené výrazy v XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 4c96665994a7e56bc70f72b66d5922f5a6472a13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961223"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>Vložené výrazy v XML (Visual Basic)
Vložené výrazy umožňují vytváření literálů XML, které obsahují výrazy, které jsou vyhodnocovány v době běhu. Syntaxe pro vložený výraz je `<%=` `expression` `%>`, která je stejná jako syntaxe používané [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].  
  
 Například můžete vytvořit XML element literál, kombinování vložené výrazy s obsahem prostý text.  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 Pokud `isbnNumber` obsahuje celé číslo 12345 a `modifiedDate` obsahuje datum 3/5/2006, když tento kód se vykoná, hodnota `book` je:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Vložený výraz umístění a ověřování  
 Vložené výrazy se může zobrazit jenom na určité umístění v rámci výrazů literálu XML. Ovládací prvky výraz umístění, které typy výraz se můžete vrátit a jak `Nothing` se zpracovává. Následující tabulka popisuje povolených umístění a typy vložené výrazy.  
  
|Umístění v literálu|Typ výrazu|Zpracování `Nothing`|  
|---|---|---|  
|Název elementu XML|<xref:System.Xml.Linq.XName>|Chyba|  
|Obsah elementu XML|`Object` nebo pole `Object`|Ignorováno|  
|Název atributu XML element|<xref:System.Xml.Linq.XName>|Chyba, pokud hodnota atributu je také `Nothing`|  
|Hodnota atributu XML element|`Object`|Atribut deklarace se ignoruje.|  
|Atribut – element XML|<xref:System.Xml.Linq.XAttribute> nebo kolekce <xref:System.Xml.Linq.XAttribute>|Ignorováno|  
|Kořenový element dokumentu XML|<xref:System.Xml.Linq.XElement> kolekce jednoho nebo <xref:System.Xml.Linq.XElement> objektu a libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> a <xref:System.Xml.Linq.XComment> objekty|Ignorováno|  
  
- Příklad vložený výraz v název elementu XML:  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- Příklad vložený výraz v obsahu prvku XML:  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- Příklad vložený výraz v atributu název elementu XML:  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- Příklad vložený výraz v hodnotě atributu – element XML:  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- Příklad vložený výraz v atributu – element XML:  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- Příklad vložený výraz v kořenový element dokumentu XML:  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 Pokud povolíte `Option Strict`, kompilátor kontroluje, že na požadovaný typ rozšiřuje typ každý vložený výraz. Jedinou výjimkou je pro kořenový element dokumentu XML, který je ověřen při spuštění kódu. Pokud kompilujete bez `Option Strict`, můžete vložit výrazy typu `Object` a jejich typ je ověřený v době běhu.  
  
 V umístění, kde je volitelné, obsah vložené výrazy, které obsahují `Nothing` jsou ignorovány. To znamená, že není potřeba zkontrolovat obsah elementu hodnoty atributů a prvky pole nejsou `Nothing` před použitím literál XML. Požadované hodnoty, jako jsou názvy prvků a atributů nemůžou být `Nothing`.  
  
 Další informace o použití vloženého výrazu v konkrétním typu literál najdete v tématu [literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Pravidla vytváření oborů  
 Kompilátor převede každý literál XML volání konstruktoru pro příslušný typ literálu. Literálový obsah a vložené výrazy v literálu XML jsou předány jako argumenty konstruktoru. To znamená, že všechny dostupné pro literál XML programovací prvky jazyka Visual Basic jsou také k dispozici pro jeho vložené výrazy.  
  
 V rámci literál XML, můžete přístup k oboru názvů XML předpony deklarována s `Imports` příkazu. Můžete deklarovat novou předponu oboru názvů XML nebo předponu existujícího oboru názvů XML v elementu s použitím stínové `xmlns` atribut. Nový obor názvů je k dispozici do podřízených uzlů daného prvku, ale ne do literálů XML ve vložené výrazy.  
  
> [!NOTE]
>  Pokud deklarujete předponu oboru názvů XML s použitím `xmlns` atribut oboru názvů, hodnota atributu musí být konstanty typu řetězec. V tomto ohledu pomocí `xmlns` atribut je například `Imports` příkaz deklarujte obor názvů XML. Chcete-li určit hodnotu oboru názvů XML nelze použít vložený výraz.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Přehled literálů XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
