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
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e21d402dce02ecb332d041f0cda651df911979ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-xml-schemas"></a>Práce s XML schémata
Chcete-li definovat strukturu dokumentu XML, jakož i jeho element relace, datové typy a obsahu omezení, použít definice typu dokumentu (DTD) nebo schématu XML definition language (XSD) schématu. I když dokumentu XML se považuje za ve správném formátu, pokud splňuje všechny požadavky syntaktické definované doporučení jazyka XML (Extensible Markup) 1.0 World Wide Web Consortium (W3C), není to považováno za platný pokud obě je ve správném formátu a vyhovuje omezení podle DTD nebo schéma. Proto i když jsou všechny platné dokumenty XML ve správném formátu, ne všechny dokumenty ve správném formátu XML nejsou platné.  
  
 Další informace o XML, najdete v článku [W3C XML 1.0 doporučení](http://go.microsoft.com/fwlink/?linkid=7269). Další informace o schématu XML, najdete v článku [W3C XML schéma část 1: doporučení struktury](http://go.microsoft.com/fwlink/?linkid=48881) a [W3C XML schéma část 2: datové typy doporučení](http://go.microsoft.com/fwlink/?linkid=17392) doporučení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Objektový Model schématu XML (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 Popisuje Model objektu schématu (SOM) v <xref:System.Xml.Schema?displayProperty=nameWithType> vytvořit obor názvů, který nabízí sadu tříd, které umožňuje číst schéma schématu definice jazyka (XSD) ze souboru nebo prostřednictvím kódu programu schéma v paměti.  
  
 [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 Popisuje <xref:System.Xml.Schema.XmlSchemaSet> třídy tedy mezipaměti, kde můžete ukládat a ověřit XSD schémata.  
  
 [Ověření nabízené XmlSchemaValidator](../../../../docs/standard/data/xml/xmlschemavalidator-push-based-validation.md)  
 Popisuje <xref:System.Xml.Schema.XmlSchemaValidator> třídu, která poskytuje mechanismus efektivní, vysoce výkonných ověřit data XML oproti XSD schémata nabízené způsobem.  
  
 [Odvození schématu XML](../../../../docs/standard/data/xml/inferring-an-xml-schema.md)  
 Popisuje postup použití <xref:System.Xml.Schema.XmlSchemaInference> třídy odvození schéma XSD ze struktury dokumentu XML.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Xml.Schema.XmlSchemaSet> &#124; <xref:System.Xml.Schema.XmlSchemaInference> &#124; <xref:System.Xml.XmlReader>  
  
## <a name="related-sections"></a>Související oddíly  
 [Ověřování dokumentu XML v modelu DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
 Popisuje, jak ověřit XML v objektu modelu dokumentu (DOM). Můžete ověřit XML, jako je načten do modelu DOM nebo ověřit dříve neověřený dokumentu XML v modelu DOM.  
  
 [Ověření schématu pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Popisuje, jak ověřit XML se navigaci a upravit pomocí <xref:System.Xml.XPath.XPathNavigator> třídy.
