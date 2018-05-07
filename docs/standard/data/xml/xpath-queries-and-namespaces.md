---
title: Dotazy XPath a obory názvů
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a121f58df93f88af851bbcc85d75e71fc067af78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xpath-queries-and-namespaces"></a>Dotazy XPath a obory názvů
Dotazy XPath věděli, obory názvů v dokumentu XML a předpony oboru názvů můžete použít k vyfiltrování názvy elementu a atributu. Kvalifikující názvy elementu a atributu předponu oboru názvů omezuje uzly vrácený dotaz XPath pro pouze uzly, které patří do konkrétní oboru názvů.  
  
 Například pokud předponu `books` mapy do oboru názvů `http://www.contoso.com/books`, pak následující dotaz XPath `/books:books/books:book` vybere pouze ty `book` elementy v oboru názvů `http://www.contoso.com/books`.  
  
## <a name="the-xmlnamespacemanager"></a>XmlNamespaceManager  
 V dotaz XPath použít obory názvů, objekt odvozené z <xref:System.Xml.IXmlNamespaceResolver> rozhraní jako <xref:System.Xml.XmlNamespaceManager> třída je vytvořený pomocí identifikátor URI oboru názvů a předpony, které chcete zahrnout do dotazu XPath.  
  
 <xref:System.Xml.XmlNamespaceManager> Objektu může být použitý v dotazu v každé z následujících způsobů.  
  
-   <xref:System.Xml.XmlNamespaceManager> Objekt je přidružený ke stávající <xref:System.Xml.XPath.XPathExpression> objekt pomocí <xref:System.Xml.XPath.XPathExpression.SetContext%2A> metodu <xref:System.Xml.XPath.XPathExpression> objektu. Může také zkompilujete novou <xref:System.Xml.XPath.XPathExpression> pomocí statické <xref:System.Xml.XPath.XPathExpression.Compile%2A> metoda, která přebírá řetězec představující výraz XPath a <xref:System.Xml.XmlNamespaceManager> objektu jako parametry a vrátí nové <xref:System.Xml.XPath.XPathExpression> objektu.  
  
-   <xref:System.Xml.XmlNamespaceManager> Samotného objektu je předán jako parametr přijetí <xref:System.Xml.XPath.XPathNavigator> třídy metoda společně s řetězec představující výraz XPath.  
  
 Toto jsou metody <xref:System.Xml.XPath.XPathNavigator> třídu, která přijmout objekt odvozené z <xref:System.Xml.IXmlNamespaceResolver> rozhraní jako parametr.  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a>Namespace výchozí  
 V dokumentu XML, který následuje, je výchozí obor názvů s prázdnou předponu používá k deklaraci `http://www.contoso.com/books` oboru názvů.  
  
```xml  
<books xmlns="http://www.example.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 Výraz XPath jsou považovány za prázdnou předponu `null` oboru názvů. Jinými slovy lze použít pouze předpon, které jsou namapované na obory názvů dotazů XPath. To znamená, že pokud chcete dotaz proti oboru názvů v dokumentu XML, i když je výchozí obor názvů, budete muset definovat předponu pro něj.  
  
 Například bez definování předponu pro dokument XML výše jazyka XPath dotaz `/books/book` nebude nevrátí žádné výsledky.  
  
 Aby se zabránilo nejednoznačnosti při dotazování dokumentů pomocí některé uzly nejsou v oboru názvů a některé v výchozí obor názvů musí být vázána předponu.  
  
 Následující kód definuje předponu pro výchozí obor názvů a vybere všechny `book` elementy z `http://www.contoso.com/books` oboru názvů.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Zpracování dat XML pomocí modelu dat XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Výběr dat XML pomocí XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Vyhodnocení výrazů XPath pomocí XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Párování uzlů pomocí XPathNavigator](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [Rozpoznané typy uzlů s dotazy XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Zkompilované výrazy XPath](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
