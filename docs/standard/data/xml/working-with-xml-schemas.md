---
title: Práce se schématy XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
ms.openlocfilehash: 0fd7313e800024ebb7e3563cb4323c5780cbf1c3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710008"
---
# <a name="working-with-xml-schemas"></a>Práce se schématy XML
Chcete-li definovat strukturu dokumentu XML a také jeho vztahy mezi prvky, datové typy a omezení obsahu, použijte definici typu dokumentu (DTD) nebo schéma schématu definice jazyka XML (XSD). I když je dokument XML považován za ve správném formátu, pokud splňuje všechny syntaktické požadavky definované doporučením konsorcium World Wide Web (W3C) jazyk XML (eXtensible Markup Language) (XML) 1,0, není považován za platný, pokud není ve správném formátu a vyhovuje omezením definovaným pomocí DTD nebo schématu. Proto i když jsou všechny platné dokumenty XML ve správném formátu, nejsou všechny správně formátované dokumenty XML platné.  
  
 Další informace o XML naleznete v [doporučení W3C XML 1,0](https://www.w3.org/TR/REC-xml/). Další informace o schématu XML naleznete v [části 1 W3C XML schématu: doporučení struktury](https://www.w3.org/TR/xmlschema-1/) a [část 2 W3C XML schématu: DataTypes](https://www.w3.org/TR/xmlschema-2/) doporučení doporučení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 Tento článek popisuje model objektu schématu (SOM) v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů, který poskytuje sadu tříd, které vám umožní číst schéma schématu schématu (XSD) ze souboru nebo programově vytvořit schéma v paměti.  
  
 [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 Popisuje <xref:System.Xml.Schema.XmlSchemaSet> třídu, která je mezipaměť, kde lze uložit a ověřit schémata XSD.  
  
 [Přímé ověření XmlSchemaValidator](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 Popisuje <xref:System.Xml.Schema.XmlSchemaValidator> třídu, která poskytuje účinný a vysoce výkonný mechanismus pro ověřování dat XML proti schématům XSD v rámci způsobu založeném na nabízených oznámeních.  
  
 [Odvození schématu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 Popisuje, jak použít <xref:System.Xml.Schema.XmlSchemaInference> třídu k odvození schématu XSD ze struktury dokumentu XML.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Xml.Schema.XmlSchemaSet>&#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124;<xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>Související oddíly  
 [Ověřování dokumentu XML v modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 Popisuje, jak ověřit XML v model DOM (Document Object Model) (DOM). XML můžete ověřit tak, jak je načteno do modelu DOM, nebo ověřit dříve neověřený dokument XML v modelu DOM.  
  
 [Ověření schématu pomocí XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Popisuje, jak ověřit, že kód XML prochází a upravuje <xref:System.Xml.XPath.XPathNavigator> pomocí třídy.
