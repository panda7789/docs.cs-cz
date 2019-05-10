---
title: Rozpoznané typy uzlů s dotazy XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa004f0def04c7efe2ba7450050a899760b0bbcd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590191"
---
# <a name="node-types-recognized-with-xpath-queries"></a>Rozpoznané typy uzlů s dotazy XPath
Typy uzlů, které jsou rozpoznány ve dotaz XPath nejsou stejné typy uzlů nalezen v modelu Document Object Model (DOM).  
  
## <a name="w3c-xpath-node-types"></a>Typy uzlů XPath W3C  
 Typy uzlů, které jsou rozpoznány ve dotaz XPath nejsou typy uzlů nalezen v modelu Document Object Model (DOM). Toto jsou typy uzlů XPath reprezentována <xref:System.Xml.XPath.XPathNodeType> výčtu.  
  
- <xref:System.Xml.XPath.XPathNodeType.All>  
  
- <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
- <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
- <xref:System.Xml.XPath.XPathNodeType.Element>  
  
- <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
- <xref:System.Xml.XPath.XPathNodeType.Root>  
  
- <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.Text>  
  
- <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 Tyto typy uzlů jsou založeny na XPath datový model, ve kterém uzly jsou odvozeny z nastavení XML informací. <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> a <xref:System.Xml.XPath.XPathNodeType.Whitespace> typy uzlů se rozšíření rozhraní Microsoft .NET Framework pro základní uzel typů uvedených v modelu dat XPath.  
  
 Typ uzlu atribut se používá různě v modelu dat XPath než jsou v modelu DOM. V modelu dat XPath uzlu elementu má sadu uzlů atributů s ní spojené a uzlu element je nadřazeného člena každý uzel atributu. V modelu DOM, uzel prvku je však vlastníka a není nadřazený. V obou modelech uzly atributu a oboru názvů nejsou považovány za podřízené uzly uzlu elementu.  
  
 Typ uzlu oboru názvů je doplněk k modelu dat XPath a není rozpoznaný typ modelu DOM uzlu.  
  
 Další informace o procházení elementu, atributu a uzly oboru názvů, najdete v článku [uzlu nastavení navigace pomocí XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) a [atribut a Namespace uzlu navigace pomocí XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) témata.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Výběr dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Vyhodnocení výrazů XPath pomocí XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Párování uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Zkompilované výrazy XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
