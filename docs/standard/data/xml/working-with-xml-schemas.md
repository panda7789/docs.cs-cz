---
title: Práce se schématy XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83fddd00f44b184fa066f6c47b90b01fac7ef7bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959105"
---
# <a name="working-with-xml-schemas"></a>Práce se schématy XML
Pokud chcete definovat strukturu dokumentu XML, jakož i jeho element relace, datových typů a omezení obsahu, použijete definice typu dokumentu (DTD) nebo jazyk (XSD) schématu definice schématu XML. I když dokumentu XML se považuje za ve správném formátu, pokud splňuje všechny požadavky syntaktické určené World Wide Web Consortium (W3C) doporučení značek XML (Extensible Language) 1.0, není považováno za platný i není ve správném formátu a podřídí omezením určené jeho DTD nebo schématu. Proto i když jsou všechny platné dokumenty XML ve správném formátu, ne všechny dokumenty ve správném formátu XML jsou platné.  
  
 Další informace o XML, najdete v článku [W3C XML 1.0 doporučení](https://www.w3.org/TR/REC-xml/). Další informace o schématu XML, najdete v článku [části 1 W3C XML schématu: Struktury doporučení](https://www.w3.org/TR/xmlschema-1/) a [W3C XML schématu část 2: Datové typy doporučení](https://www.w3.org/TR/xmlschema-2/) doporučení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 Tento článek popisuje Model objektu schématu (SOM) v <xref:System.Xml.Schema?displayProperty=nameWithType> obor názvů, který obsahuje sadu tříd, který umožňuje načtení schématu jazyk (XSD) schématu definice, ze souboru nebo prostřednictvím kódu programu vytvořit schéma v paměti.  
  
 [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 Tento článek popisuje <xref:System.Xml.Schema.XmlSchemaSet> třídy, který je v mezipaměti, kde můžete ukládat a ověřit schémata XSD.  
  
 [Přímé ověření XmlSchemaValidator](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 Tento článek popisuje <xref:System.Xml.Schema.XmlSchemaValidator> třídu, která poskytuje mechanismus efektivního, vysoce výkonné ověřit data XML oproti schémata XSD nabízené způsobem.  
  
 [Odvození schématu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 Tento článek popisuje způsob použití <xref:System.Xml.Schema.XmlSchemaInference> třídy odvodit schéma XSD ze struktury dokumentu XML.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>Související oddíly  
 [Ověřování dokumentu XML v modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 Popisuje, jak ověřit kód XML v modelu Document Object Model (DOM). Ověřit kód XML, jako je načten do modelu DOM nebo ověřit dřív neověřených dokument XML v modelu DOM.  
  
 [Ověření schématu pomocí XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Popisuje, jak ověřit XML se přejde poté a upravit pomocí <xref:System.Xml.XPath.XPathNavigator> třídy.
