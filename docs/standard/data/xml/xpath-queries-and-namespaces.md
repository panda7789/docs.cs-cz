---
title: Dotazy a obory názvů XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: 91503ce0bffa1a9390432a51bff1ef10d80f563a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709774"
---
# <a name="xpath-queries-and-namespaces"></a>Dotazy a obory názvů XPath
Dotazy XPath mají na paměti obory názvů v dokumentu XML a můžou použít předpony oboru názvů k získání názvů elementů a atributů. Kvalifikování názvů elementů a atributů s předponou oboru názvů omezuje uzly vrácené dotazem XPath pouze na ty uzly, které patří do konkrétního oboru názvů.  
  
 Například pokud předpona `books` namapována na obor názvů `http://www.contoso.com/books`, pak následující dotaz XPath `/books:books/books:book` vybere pouze ty `book` elementy v oboru názvů `http://www.contoso.com/books`.  
  
## <a name="the-xmlnamespacemanager"></a>XmlNamespaceManager  
 Chcete-li použít obory názvů v dotazu XPath, objekt odvozený z rozhraní <xref:System.Xml.IXmlNamespaceResolver>, jako je <xref:System.Xml.XmlNamespaceManager> třída, je vytvořen pomocí identifikátoru URI a předpony oboru názvů, které mají být zahrnuty do dotazu XPath.  
  
 Objekt <xref:System.Xml.XmlNamespaceManager> může být v dotazu použit v každém z následujících způsobů.  
  
- Objekt <xref:System.Xml.XmlNamespaceManager> je přidružen k existujícímu objektu <xref:System.Xml.XPath.XPathExpression> pomocí metody <xref:System.Xml.XPath.XPathExpression.SetContext%2A> objektu <xref:System.Xml.XPath.XPathExpression>. Můžete také zkompilovat nový objekt <xref:System.Xml.XPath.XPathExpression> pomocí metody static <xref:System.Xml.XPath.XPathExpression.Compile%2A>, která přebírá řetězec představující výraz XPath a objekt <xref:System.Xml.XmlNamespaceManager> jako parametry a vrací nový objekt <xref:System.Xml.XPath.XPathExpression>.  
  
- Samotný objekt <xref:System.Xml.XmlNamespaceManager> je předán jako parametr pro přijetí metody <xref:System.Xml.XPath.XPathNavigator> třídy spolu s řetězcem představujícím výraz XPath.  
  
 Níže jsou uvedené metody třídy <xref:System.Xml.XPath.XPathNavigator>, které přijímají objekt odvozený z rozhraní <xref:System.Xml.IXmlNamespaceResolver> jako parametr.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a>Výchozí obor názvů  
 V dokumentu XML, který následuje, je použit výchozí obor názvů s prázdnou předponou pro deklaraci oboru názvů `http://www.contoso.com/books`.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 XPath zpracovává prázdnou předponu jako obor názvů `null`. Jinými slovy, v dotazech XPath lze použít pouze předpony mapované na obory názvů. To znamená, že pokud chcete dotazovat na obor názvů v dokumentu XML, i když se jedná o výchozí obor názvů, musíte pro něj definovat předponu.  
  
 Například bez definice prefixu pro dokument XML výše, `/books/book` dotaz XPath nevrátí žádné výsledky.  
  
 Předpona musí být vázána, aby zabránila nejednoznačnosti při dotazování dokumentů s některými uzly, které nejsou v oboru názvů, a některé ve výchozím oboru názvů.  
  
 Následující kód definuje předponu pro výchozí obor názvů a vybere všechny `book` prvky z oboru názvů `http://www.contoso.com/books`.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim query As XPathExpression = navigator.Compile("/books:books/books:book")  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(navigator.NameTable)  
manager.AddNamespace("books", "http://www.contoso.com/books")  
query.SetContext(manager)  
Dim nodes As XPathNodeIterator = navigator.Select(query)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathExpression query = navigator.Compile("/books:books/books:book");  
XmlNamespaceManager manager = new XmlNamespaceManager(navigator.NameTable);  
manager.AddNamespace("books", "http://www.contoso.com/books");  
query.SetContext(manager);  
XPathNodeIterator nodes = navigator.Select(query);  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Výběr dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Vyhodnocení výrazů XPath pomocí XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Párování uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [Rozpoznané typy uzlů s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Zkompilované výrazy XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
