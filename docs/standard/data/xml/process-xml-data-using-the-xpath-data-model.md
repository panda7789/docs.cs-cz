---
title: Zpracování dat XML pomocí modelu dat XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67fbacd24b888b9c45072bcb34031f38adc118e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728395"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a>Zpracování dat XML pomocí modelu dat XPath
<xref:System.Xml?displayProperty=nameWithType> Obor názvů poskytuje programový reprezentace XML dokumenty, fragmentů, uzly nebo sad uzlů v paměti, pomocí <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> třídy.  
  
 <xref:System.Xml.XPath.XPathDocument> Třída poskytuje rychlé, jen pro čtení, v paměti reprezentace dokumentu XML pomocí modelu dat XPath. <xref:System.Xml.XmlDocument> Třída poskytuje reprezentaci upravovat v paměti implementace základní úrovně 1 W3C Document Object Model (DOM) a základní modelu DOM úrovně 2 dokumentu XML. Implementovat obě třídy <xref:System.Xml.XPath.IXPathNavigable> rozhraní a vrátit se <xref:System.Xml.XPath.XPathNavigator> objekt použitý k výběru, vyhodnocení, přejděte a v některých případech může upravovat podkladová data XML.  
  
 Následující části popisují funkce <xref:System.Xml.XPath.XPathNavigator> třídy podle třídy, která vrátí jej.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Načítání dat XML pomocí XPathDocument a XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Popisuje, jak vytvořit jen pro čtení <xref:System.Xml.XPath.XPathDocument> třída objektu určeného ke čtení dokumentu XML a jak vytvářet upravitelné <xref:System.Xml.XmlDocument> objektu třídy číst a upravovat dokumentu XML. Toto téma také popisuje, jak návratový <xref:System.Xml.XPath.XPathNavigator> objekt z každé třídě k procházení a úpravy dokumentu XML.  
  
 [Výběr, vyhodnocení a spárování dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třídu sloužící k výběru uzly v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí dotazu XPath, vyhodnocení a podívejte se na výsledky výrazu XPath a určit, pokud uzel v dokumentu XML odpovídá dané XPath výraz.  
  
 [Přístup k datům XML pomocí XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třídu použít k procházení uzly, extrahování dat XML a přístup k datům silného typu XML v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.  
  
 [Úpravy dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třídu sloužící k vložení, úpravu a odebrání uzlů a hodnot z dokumentu XML, který je součástí <xref:System.Xml.XmlDocument> objektu.  
  
 [Ověření schématu pomocí XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Popisuje, jak ověřit obsah XML obsažených v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
