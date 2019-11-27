---
title: Vložené výrazy v XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 0cdb960160457108ddf18c554dae5f5993269833
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332357"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>Vložené výrazy v XML (Visual Basic)
Vložené výrazy umožňují vytvořit literály XML, které obsahují výrazy, které jsou vyhodnocovány v době běhu. Syntaxe vloženého výrazu je `<%=` `expression` `%>`, která se shoduje s syntaxí použitou v ASP.NET.  
  
 Můžete například vytvořit literál elementu XML a zkombinovat vložené výrazy s textovým obsahem literálu.  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 Pokud `isbnNumber` obsahuje celé číslo 12345 a `modifiedDate` obsahuje datum 3/5/2006, když se tento kód spustí, hodnota `book` je:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Umístění a ověřování vloženého výrazu  
 Vložené výrazy mohou být zobrazeny pouze v určitých umístěních ve výrazech literálů XML. Umístění výrazu určuje, které typy výrazu mohou vracet a jak se má `Nothing` zpracovat. Následující tabulka popisuje povolená umístění a typy vložených výrazů.  
  
|Umístění v literálu|Typ výrazu|Manipulace s `Nothing`|  
|---|---|---|  
|Název elementu XML|<xref:System.Xml.Linq.XName>|Chyba|  
|Obsah elementu XML|`Object` nebo pole `Object`|Ignorováno|  
|Název atributu elementu XML|<xref:System.Xml.Linq.XName>|Chyba, pokud není hodnota atributu také `Nothing`|  
|Hodnota atributu elementu XML|`Object`|Deklarace atributu se ignorovala.|  
|Atribut elementu XML|<xref:System.Xml.Linq.XAttribute> nebo kolekce <xref:System.Xml.Linq.XAttribute>|Ignorováno|  
|Kořenový element dokumentu XML|<xref:System.Xml.Linq.XElement> nebo kolekce jednoho objektu <xref:System.Xml.Linq.XElement> a libovolný počet objektů <xref:System.Xml.Linq.XProcessingInstruction> a <xref:System.Xml.Linq.XComment>|Ignorováno|  
  
- Příklad vloženého výrazu v názvu elementu XML:  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- Příklad vloženého výrazu v obsahu elementu XML:  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- Příklad vloženého výrazu v názvu atributu elementu XML:  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- Příklad vloženého výrazu v hodnotě atributu elementu XML:  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- Příklad vloženého výrazu v atributu elementu XML:  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- Příklad vloženého výrazu v kořenovém elementu dokumentu XML:  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 Pokud povolíte `Option Strict`, kompilátor zkontroluje, že se typ každého vloženého výrazu rozšíří na požadovaný typ. Jediná výjimka je určena pro kořenový prvek dokumentu XML, který je ověřen při spuštění kódu. Pokud kompilujete bez `Option Strict`, můžete vložit výrazy typu `Object` a jejich typ se ověří za běhu.  
  
 V místech, kde je obsah volitelný, jsou vložené výrazy obsahující `Nothing` ignorovány. To znamená, že nemusíte kontrolovat obsah elementu, hodnoty atributů a prvky pole `Nothing` před použitím literálu XML. Požadované hodnoty, například názvy elementů a atributů, nelze `Nothing`.  
  
 Další informace o použití vloženého výrazu v konkrétním typu literálu naleznete v tématu [literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literál elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Pravidla oboru  
 Kompilátor převede každý literál XML na volání konstruktoru pro příslušný typ literálu. Obsah literálu a vložené výrazy v literálu XML jsou předány jako argumenty konstruktoru. To znamená, že všechny programové prvky Visual Basic dostupné pro literál XML jsou také k dispozici pro vložené výrazy.  
  
 V rámci literálu XML máte přístup k předponám oboru názvů XML deklarovaným pomocí příkazu `Imports`. Můžete deklarovat novou předponu oboru názvů XML nebo vytvořit stín předpony oboru názvů XML v elementu pomocí atributu `xmlns`. Nový obor názvů je k dispozici podřízeným uzlům daného prvku, ale nikoli k literálům XML ve vložených výrazech.  
  
> [!NOTE]
> Pokud deklarujete předponu oboru názvů XML pomocí atributu `xmlns` obor názvů, hodnota atributu musí být konstantní řetězec. V tomto ohledu použití atributu `xmlns` je například použití příkazu `Imports` k deklaraci oboru názvů XML. Vložený výraz nelze použít k určení hodnoty oboru názvů XML.  
  
## <a name="see-also"></a>Viz také:

- [Vytváření XML v Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Přehled literálů XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
