---
title: "Práce s XML schémata"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbbcc70c-bf9a-4f6a-af72-1bab5384a187
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6cba66a0d8291592b082898d20ca780c8067401e
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2018
---
# <a name="working-with-xml-schemas"></a>Práce s XML schémata
Chcete-li definovat strukturu dokumentu XML, jakož i jeho element relace, datové typy a obsahu omezení, použít definice typu dokumentu (DTD) nebo schématu XML definition language (XSD) schématu. I když dokumentu XML se považuje za ve správném formátu, pokud splňuje všechny požadavky syntaktické definované doporučení jazyka XML (Extensible Markup) 1.0 World Wide Web Consortium (W3C), není to považováno za platný pokud obě je ve správném formátu a vyhovuje omezení podle DTD nebo schéma. Proto i když jsou všechny platné dokumenty XML ve správném formátu, ne všechny dokumenty ve správném formátu XML nejsou platné.  
  
 Další informace o XML, najdete v článku [W3C XML 1.0 doporučení](https://www.w3.org/TR/REC-xml/). Další informace o schématu XML, najdete v článku [W3C XML schéma část 1: doporučení struktury](https://www.w3.org/TR/xmlschema-1/) a [W3C XML schéma část 2: datové typy doporučení](https://www.w3.org/TR/xmlschema-2/) doporučení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Model objektu schématu (SOM) XML](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 Popisuje Model objektu schématu (SOM) v <xref:System.Xml.Schema?displayProperty=nameWithType> vytvořit obor názvů, který nabízí sadu tříd, které umožňuje číst schéma schématu definice jazyka (XSD) ze souboru nebo prostřednictvím kódu programu schéma v paměti.  
  
 [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 Popisuje <xref:System.Xml.Schema.XmlSchemaSet> třídy tedy mezipaměti, kde můžete ukládat a ověřit XSD schémata.  
  
 [Přímé ověření XmlSchemaValidator](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 Popisuje <xref:System.Xml.Schema.XmlSchemaValidator> třídu, která poskytuje mechanismus efektivní, vysoce výkonných ověřit data XML oproti XSD schémata nabízené způsobem.  
  
 [Odvození schématu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 Popisuje postup použití <xref:System.Xml.Schema.XmlSchemaInference> třídy odvození schéma XSD ze struktury dokumentu XML.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>Související oddíly  
 [Ověřování dokumentu XML v modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 Popisuje, jak ověřit XML v objektu modelu dokumentu (DOM). Můžete ověřit XML, jako je načten do modelu DOM nebo ověřit dříve neověřený dokumentu XML v modelu DOM.  
  
 [Ověření schématu pomocí XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Popisuje, jak ověřit XML se navigaci a upravit pomocí <xref:System.Xml.XPath.XPathNavigator> třídy.
