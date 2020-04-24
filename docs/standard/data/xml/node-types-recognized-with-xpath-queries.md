---
title: Rozpoznané typy uzlů s dotazy XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
ms.openlocfilehash: cc1aa668ccf6fc7f210f48a28cf76b364459c784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710541"
---
# <a name="node-types-recognized-with-xpath-queries"></a>Rozpoznané typy uzlů s dotazy XPath
Typy uzlů rozpoznané v dotazu XPath nejsou stejné typy uzlů, které se nacházejí v model DOM (Document Object Model) (DOM).  
  
## <a name="w3c-xpath-node-types"></a>Typy uzlů XPath W3C  
 Typy uzlů rozpoznané v dotazu XPath nejsou typy uzlů, které se nacházejí v model DOM (Document Object Model) (DOM). Níže jsou uvedeny typy uzlů XPath reprezentované <xref:System.Xml.XPath.XPathNodeType> výčtem.  
  
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
  
 Tyto typy uzlů jsou založeny na datovém modelu XPath, kde jsou uzly odvozeny ze sady informací XML. Typy <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> uzlů <xref:System.Xml.XPath.XPathNodeType.Whitespace> a jsou rozšířeními od Microsoftu .NET Framework k typům základních uzlů popsaným v datovém modelu XPath.  
  
 Typ uzlu atributu je v datovém modelu XPath použit odlišně, než je v modelu DOM. V datovém modelu XPath uzel elementu obsahuje sadu uzlů atributů, které se týkají, a uzel elementu je nadřazeným uzlem každého uzlu atributu. V modelu DOM je však uzel prvku vlastníkem a nikoli nadřazeným objektem. V obou modelech se uzly atributů a názvů nepovažují za podřízené uzly uzlu elementu.  
  
 Typ uzlu oboru názvů je doplněk k datovému modelu XPath a není rozpoznaným typem uzlu modelu DOM.  
  
 Další informace o přechodu elementů, atributů a uzlů oboru názvů naleznete v tématu [uzel nastavení navigace pomocí prvku XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) a [atribut a uzel oboru názvů pomocí témat XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Výběr dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Vyhodnocení výrazů XPath pomocí XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Párování uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Dotazy a obory názvů XPath](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Zkompilované výrazy XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
