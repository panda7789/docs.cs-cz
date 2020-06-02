---
title: Výběr dat XML pomocí XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: d5e7074fc8c68a0a0243ea4ad237e713e0a729b3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289054"
---
# <a name="select-xml-data-using-xpathnavigator"></a>Výběr dat XML pomocí XPathNavigator
<xref:System.Xml.XPath.XPathNavigator>Třída poskytuje sadu metod, které slouží k výběru sady uzlů v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo pomocí výrazu XPath. Po výběru můžete iterovat přes vybranou sadu uzlů.  
  
## <a name="xpathnavigator-selection-methods"></a>Metody výběru XPathNavigator  
 <xref:System.Xml.XPath.XPathNavigator>Třída poskytuje sadu metod, které slouží k výběru sady uzlů v <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> objektu nebo pomocí výrazu XPath. <xref:System.Xml.XPath.XPathNavigator>Třída také poskytuje sadu optimalizovaných metod pro výběr nadřazených a podřízených uzlů rychleji než použití výrazu XPath. Vybraná sada uzlů je vrácena v <xref:System.Xml.XPath.XPathNodeIterator> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jednoho vybraného uzlu.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>Výběr uzlů pomocí výrazů XPath  
 Chcete-li vybrat sadu uzlů pomocí výrazu XPath, použijte jednu z následujících metod výběru.  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Při volání tyto metody vrátí sadu uzlů, které můžete volně procházet pomocí <xref:System.Xml.XPath.XPathNodeIterator> objektu nebo <xref:System.Xml.XPath.XPathNavigator> objektu v případě jednoho vybraného uzlu.  
  
 Navigace s <xref:System.Xml.XPath.XPathNodeIterator> objektem nemá vliv na pozici <xref:System.Xml.XPath.XPathNavigator> objektu používaného k jeho vytvoření. <xref:System.Xml.XPath.XPathNavigator>Objekt vrácený z <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metod je umístěn na jednom vráceném uzlu a také nemá vliv na pozici <xref:System.Xml.XPath.XPathNavigator> objektu používaného k jeho vytvoření.  
  
 Následující příklad ukazuje vytvoření <xref:System.Xml.XPath.XPathNavigator> objektu z <xref:System.Xml.XPath.XPathDocument> objektu, použití <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody k výběru uzlů v <xref:System.Xml.XPath.XPathDocument> objektu a použití <xref:System.Xml.XPath.XPathNodeIterator> objektu k iterování na vybraných uzlech.  
  
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
  
 Příklad přebírá `books.xml` soubor jako vstup.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>Metody optimalizovaného výběru  
 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>Metody, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> a <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> <xref:System.Xml.XPath.XPathNavigator> třídy reprezentují výrazy XPath běžně používané k načtení uzlů podřízenosti, následníka a předchůdce. Tyto metody jsou optimalizované pro výkon a jsou rychlejší než jejich odpovídající výrazy XPath. <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>Metody, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A> a slouží <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> k výběru nadřazených uzlů, podřízených uzlů a následníků na základě <xref:System.Xml.XPath.XPathNodeType> hodnoty nebo místního názvu a identifikátoru URI uzlů, které chcete vybrat. Vybrané předchůdce, podřízené uzly a následníky jsou vráceny v <xref:System.Xml.XPath.XPathNodeIterator> objektu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](process-xml-data-using-the-xpath-data-model.md)
- [Vyhodnocení výrazů XPath pomocí XPathNavigator](evaluate-xpath-expressions-using-xpathnavigator.md)
- [Párování uzlů pomocí XPathNavigator](matching-nodes-using-xpathnavigator.md)
- [Rozpoznané typy uzlů s dotazy XPath](node-types-recognized-with-xpath-queries.md)
- [Dotazy a obory názvů XPath](xpath-queries-and-namespaces.md)
- [Zkompilované výrazy XPath](compiled-xpath-expressions.md)
