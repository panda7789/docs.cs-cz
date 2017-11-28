---
title: "Zpracování kódu XML dat pomocí jazyka XPath datový Model"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d2c8db03d494be13a93df06a359e4e4294c22a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="process-xml-data-using-the-xpath-data-model"></a>Zpracování kódu XML dat pomocí jazyka XPath datový Model
<xref:System.Xml?displayProperty=nameWithType> Obor názvů poskytuje programovací reprezentace XML dokumenty, fragmenty, uzly nebo sad uzlů v paměti, pomocí <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument> třídy.  
  
 <xref:System.Xml.XPath.XPathDocument> Třída poskytuje rychlé, jen pro čtení, v paměti reprezentace dokumentu XML pomocí modelu dat XPath. <xref:System.Xml.XmlDocument> Třída poskytuje reprezentaci upravovat v paměti dokumentu XML, které implementují základní úroveň 1 W3C Model Document Object (DOM) a základní DOM Level 2. Obě třídy implementovat <xref:System.Xml.XPath.IXPathNavigable> rozhraní a vrátit <xref:System.Xml.XPath.XPathNavigator> objekt použitý k výběru, vyhodnotit, přejděte a v některých případech upravit základní data XML.  
  
 Následující části popisují funkce <xref:System.Xml.XPath.XPathNavigator> třída založena na třídu, která vrátí ji.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Načítání dat XML pomocí XPathDocument a třídou XMLDocument nastavenou na](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 Popisuje postup vytvoření jen pro čtení <xref:System.Xml.XPath.XPathDocument> třída objektu určeného ke čtení dokumentu XML a jak vytvořit upravitelné <xref:System.Xml.XmlDocument> objektu třídy číst a upravovat dokument XML. Toto téma také popisuje, jak návratový <xref:System.Xml.XPath.XPathNavigator> objekt z každé třídě přejděte a upravit dokument XML.  
  
 [Výběr, Evaluating a porovnávání dat XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třída používaná k vyberte uzly ve <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí dotaz XPath, hodnocení a podívejte se na výsledky výraz XPath a určit, jestli uzlu v dokumentu XML odpovídá dané XPath výraz.  
  
 [Přístup k datům XML pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třída používaná přejděte uzly, extrahovat XML data a přístup k datům silného typu XML v <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.  
  
 [Úpravy pomocí objektem XPathNavigator nastaveným na Data XML](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 Popisuje metody <xref:System.Xml.XPath.XPathNavigator> třída používaná vložit, upravovat a odebírat uzly a hodnoty z dokumentu XML, který je součástí <xref:System.Xml.XmlDocument> objektu.  
  
 [Ověření schématu pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)  
 Popisuje, jak ověřit obsah XML, které jsou součástí <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> objektu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování dat XML pomocí modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
