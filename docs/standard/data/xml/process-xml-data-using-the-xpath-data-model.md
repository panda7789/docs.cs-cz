---
title: Zpracování dat XML pomocí modelu dat XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
ms.openlocfilehash: f964864577cf08eb074bdfb9af7f7daf3ffb37b9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710437"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a>Zpracování dat XML pomocí modelu dat XPath
<xref:System.Xml?displayProperty=nameWithType> Obor názvů poskytuje programovou reprezentaci dokumentů XML, fragmentů, uzlů nebo sad uzlů v paměti s použitím tříd <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> .  
  
 <xref:System.Xml.XPath.XPathDocument> Třída poskytuje rychlé znázornění dokumentu XML, který je jen pro čtení a který je v paměti, pomocí datového modelu XPath. <xref:System.Xml.XmlDocument> Třída poskytuje upravitelnou reprezentaci v paměti dokumentu XML implementující model DOM (Document Object Model) W3C (DOM) úrovně 1 Core a Core DOM úrovně 2. Obě třídy implementují <xref:System.Xml.XPath.IXPathNavigable> rozhraní a vracejí <xref:System.Xml.XPath.XPathNavigator> objekt, který slouží k výběru, vyhodnocení, procházení a v některých případech, úpravám podkladových dat XML.  
  
 Následující části popisují funkčnost <xref:System.Xml.XPath.XPathNavigator> třídy na základě třídy, která je vrátí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Načítání dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Popisuje, jak vytvořit objekt třídy jen <xref:System.Xml.XPath.XPathDocument> pro čtení pro čtení dokumentu XML a jak vytvořit upravitelný <xref:System.Xml.XmlDocument> objekt třídy pro čtení a úpravy dokumentu XML. Toto téma také popisuje, jak vrátit <xref:System.Xml.XPath.XPathNavigator> objekt z každé třídy pro procházení a úpravy dokumentu XML.  
  
 [Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třídy používané k výběru uzlů v objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí dotazu XPath, vyhodnocení a přezkoumání výsledků výrazu XPath a určení, zda uzel v dokumentu XML odpovídá danému výrazu XPath.  
  
 [Přístup k datům XML pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třídy používané pro navigaci v uzlech, extrakci dat XML a přístup k datům XML silného typu <xref:System.Xml.XPath.XPathDocument> v <xref:System.Xml.XmlDocument> objektu or.  
  
 [Úpravy dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třídy používané pro vložení, úpravu a odebrání uzlů a hodnot z dokumentu XML obsaženého v <xref:System.Xml.XmlDocument> objektu.  
  
 [Ověření schématu pomocí XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Popisuje způsoby, jak ověřit obsah XML obsažený v objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
