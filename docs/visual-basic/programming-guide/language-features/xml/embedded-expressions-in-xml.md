---
title: "Vložené výrazy v XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1cdba0a39a932f143ac98c2514240e1696a8fe0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>Vložené výrazy v XML (Visual Basic)
Vložené výrazy umožňují vytváření literálů XML, které obsahují výrazy, které jsou vyhodnocovány v době běhu. Syntaxe pro embedded výrazu je `<%=` `expression` `%>`, což je stejný jako syntaxe použít v [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].  
  
 Například můžete vytvoříte XML element literálu, kombinace vložené výrazy s literálu textového obsahu.  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 Pokud `isbnNumber` obsahuje 12345 celé číslo a `modifiedDate` obsahuje datum 3/5/2006, když tento kód provede, hodnota `book` je:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Umístění vložených výraz a ověřování  
 Vložené výrazy se může vyskytovat pouze v určitých umístění ve výrazech literál XML. Ovládací prvky výraz umístění, které typy výraz se můžete vrátit a jak `Nothing` se zpracovává. Následující tabulka popisuje povolených umístění a typy vložené výrazy.  
  
|Umístění v literál|Typ výrazu|Zpracování`Nothing`|  
|---|---|---|  
|Název elementu XML|<xref:System.Xml.Linq.XName>|Chyba|  
|Obsah elementu XML|`Object`nebo pole`Object`|Ignorováno|  
|Atribut název elementu XML|<xref:System.Xml.Linq.XName>|Chyba, pokud hodnota atributu je také`Nothing`|  
|Hodnota atributu XML element|`Object`|Atribut deklarace ignorovat|  
|Atribut XML element|<xref:System.Xml.Linq.XAttribute>nebo kolekci<xref:System.Xml.Linq.XAttribute>|Ignorováno|  
|Kořenový element dokumentu XML|<xref:System.Xml.Linq.XElement>nebo kolekce jednoho <xref:System.Xml.Linq.XElement> objekt a libovolný počet <xref:System.Xml.Linq.XProcessingInstruction> a <xref:System.Xml.Linq.XComment> objekty|Ignorováno|  
  
-   Příklad embedded výrazu v název elementu XML:  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   Příklad výrazu vložený obsah elementu XML:  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   Příklad embedded výrazu v atributu název elementu XML:  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   Příklad embedded výrazu v hodnotě atributu – element XML:  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   Příklad embedded výrazu v atributu – element XML:  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   Příklad embedded výrazu v kořenový element dokumentu XML:  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 Pokud povolíte `Option Strict`, kompilátor ověří, že typ každý embedded výraz rozšiřuje na požadovaný typ. Jedinou výjimkou je pro kořenový element dokumentu XML, který bude ověřen při spuštění kódu. Pokud je kompilovat bez `Option Strict`, můžete vložit výrazy typu `Object` a jejich typů bude ověřen v době běhu.  
  
 V umístění, kde je volitelné, obsah vložené výrazy, které obsahují `Nothing` jsou ignorovány. To znamená, nemáte ke kontrole obsahu elementu hodnoty atributu, a elementy pole nejsou `Nothing` dříve, než použijete literál XML. Požadované hodnoty, například názvy elementu a atributu nelze `Nothing`.  
  
 Další informace o použití vložených výrazu v konkrétní typ literál najdete v tématu [literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Pravidla rozsahu  
 Kompilátor převede každý literál XML volání konstruktoru pro příslušný typ literálu. Literál obsah a vložené výrazy v literál XML jsou předány jako argumenty pro konstruktor. To znamená, že všechny [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programovací elementy, které jsou k dispozici literál XML je také možné jeho vložené výrazy.  
  
 V rámci literál XML, můžete přístup k oboru názvů XML, který je předpony deklarovat s `Imports` příkaz. Můžete deklarovat nový obor názvů XML nebo stínové předponu existující obor názvů XML elementu s použitím `xmlns` atribut. Nový obor názvů je k dispozici na podřízených uzlů tohoto elementu, ale ne na XML – literály v vložené výrazy.  
  
> [!NOTE]
>  Pokud deklarace předponu oboru názvů XML pomocí `xmlns` atribut namespace hodnota atributu musí být konstantní řetězec. V tomto ohledu pomocí `xmlns` atribut je třeba pomocí `Imports` příkaz k deklaraci oboru názvů XML. Vložené výrazu nelze použít k určení hodnoty obor názvů XML.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Literál dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [Literál XML elementu](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Imports – příkaz (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Přehled literálů XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
