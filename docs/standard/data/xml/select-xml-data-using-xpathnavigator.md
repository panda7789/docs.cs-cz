---
title: Výběr dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: 99b6b3b6959abf4c8adc313364ad641249bd9bc3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710164"
---
# <a name="select-xml-data-using-xpathnavigator"></a>Výběr dat XML pomocí XPathNavigator
Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje sadu metod, které slouží k výběru sady uzlů v objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath. Po výběru můžete iterovat přes vybranou sadu uzlů.  
  
## <a name="xpathnavigator-selection-methods"></a>Metody výběru XPathNavigator  
 Třída <xref:System.Xml.XPath.XPathNavigator> poskytuje sadu metod, které slouží k výběru sady uzlů v objektu <xref:System.Xml.XPath.XPathDocument> nebo <xref:System.Xml.XmlDocument> pomocí výrazu XPath. Třída <xref:System.Xml.XPath.XPathNavigator> také poskytuje sadu optimalizovaných metod pro výběr nadřazených a podřízených uzlů rychleji než použití výrazu XPath. Vybraná sada uzlů se vrátí v objektu <xref:System.Xml.XPath.XPathNodeIterator> nebo objektu <xref:System.Xml.XPath.XPathNavigator> v případě jednoho vybraného uzlu.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>Výběr uzlů pomocí výrazů XPath  
 Chcete-li vybrat sadu uzlů pomocí výrazu XPath, použijte jednu z následujících metod výběru.  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Při volání tyto metody vrátí sadu uzlů, které můžete volně procházet pomocí objektu <xref:System.Xml.XPath.XPathNodeIterator> nebo objektu <xref:System.Xml.XPath.XPathNavigator> v případě jednoho vybraného uzlu.  
  
 Navigace s objektem <xref:System.Xml.XPath.XPathNodeIterator> nemá vliv na pozici objektu <xref:System.Xml.XPath.XPathNavigator> používaného k jeho vytvoření. Objekt <xref:System.Xml.XPath.XPathNavigator> vrácený z <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>ch metod je umístěn na jednom vráceném uzlu a také nemá vliv na pozici objektu <xref:System.Xml.XPath.XPathNavigator>, který se používá k jeho vytvoření.  
  
 Následující příklad ukazuje vytvoření objektu <xref:System.Xml.XPath.XPathNavigator> z objektu <xref:System.Xml.XPath.XPathDocument>, použití metody <xref:System.Xml.XPath.XPathNavigator.Select%2A> k výběru uzlů v objektu <xref:System.Xml.XPath.XPathDocument> a použití objektu <xref:System.Xml.XPath.XPathNodeIterator> k iterování na vybraných uzlech.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 V příkladu se jako vstup používá soubor `books.xml`.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>Metody optimalizovaného výběru  
 Metody <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>a <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> třídy <xref:System.Xml.XPath.XPathNavigator> reprezentují výrazy XPath běžně používané k načtení uzlů podřízenosti, následníka a předchůdce. Tyto metody jsou optimalizované pro výkon a jsou rychlejší než jejich odpovídající výrazy XPath. Metody <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>a <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> vyberou nadřazené, podřízené a odvozené uzly na základě hodnoty <xref:System.Xml.XPath.XPathNodeType> nebo místního názvu a identifikátoru URI oboru názvů uzlů k výběru. Vybrané uzly předchůdce, podřízené a následníka jsou vráceny v objektu <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Vyhodnocení výrazů XPath pomocí XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Párování uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Rozpoznané typy uzlů s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Dotazy XPath a obory názvů](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Zkompilované výrazy XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
