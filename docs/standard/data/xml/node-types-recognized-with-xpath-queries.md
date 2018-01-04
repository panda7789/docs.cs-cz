---
title: "Typy uzlů rozpoznána s dotazy XPath"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: db309bf0d04dfab4fd9fbdd2c8b145c1705d8428
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="node-types-recognized-with-xpath-queries"></a>Typy uzlů rozpoznána s dotazy XPath
Typy uzlů rozpoznán v dotaz XPath nejsou stejné typy uzlů nalezen v objektu modelu dokumentu (DOM).  
  
## <a name="w3c-xpath-node-types"></a>Typy uzlů XPath W3C  
 Typy uzlů rozpoznán v dotaz XPath nejsou typy uzlů nalezen v objektu modelu dokumentu (DOM). Toto jsou typy uzlů XPath reprezentována <xref:System.Xml.XPath.XPathNodeType> výčtu.  
  
-   <xref:System.Xml.XPath.XPathNodeType.All>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Element>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Root>  
  
-   <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Text>  
  
-   <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 Tyto typy uzlů jsou založené na XPath datový model, kde jsou uzly odvozené ze sady informace XML. <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> a <xref:System.Xml.XPath.XPathNodeType.Whitespace> rozšíření rozhraní Microsoft .NET Framework pro typy základní uzlů, které jsou popsané v datovém modelu XPath jsou typy uzlů.  
  
 Typ uzlu atribut se používá jinak v datovém modelu XPath než je v modelu DOM. V datovém modelu XPath uzlu element obsahuje sadu atributů uzly s ním souvisejí a uzel elementu je nadřazená každého uzlu atributu. V modelu DOM, uzlu element je však vlastníka a není nadřazený. V obou modelech atribut a obor názvů uzly nejsou považovány za podřízené uzly uzlu elementu.  
  
 Typ uzlu oboru názvů je doplňkem k XPath datový model a není rozpoznaný typ uzlu DOM.  
  
 Další informace o navigace element atribut a uzly oboru názvů najdete v tématu [uzlu nastavit navigační pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) a [atribut a Namespace uzlu navigace pomocí objektem XPathNavigator nastaveným na](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) témata.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Výběr dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Vyhodnocení výrazů XPath pomocí XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Párování uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Zkompilované výrazy XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
