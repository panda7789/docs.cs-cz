---
title: Dotazy a obory názvů XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0704e78a0e7fbf3987b3bc75bb46e135f00110e9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615341"
---
# <a name="xpath-queries-and-namespaces"></a>Dotazy a obory názvů XPath
Dotazy XPath vědomi obory názvů v dokumentu XML a předpony oboru názvů můžete použít k vyfiltrování názvy prvků a atributů. Kvalifikující názvy prvků a atributů s předponu oboru názvů omezí vrácené dotaz XPath pro pouze ty uzly, které patří do konkrétní obor názvů uzly.  
  
 Například pokud předponu `books` mapuje na obor názvů `http://www.contoso.com/books`, pak následující dotaz XPath `/books:books/books:book` vybere pouze ty `book` prvky v oboru názvů `http://www.contoso.com/books`.  
  
## <a name="the-xmlnamespacemanager"></a>XmlNamespaceManager  
 Obory názvů používané dotaz XPath, objekt odvozený z <xref:System.Xml.IXmlNamespaceResolver> rozhraní jako <xref:System.Xml.XmlNamespaceManager> třídy je vytvořený pomocí identifikátoru URI oboru názvů a předpony, které mají být zahrnuty dotaz XPath.  
  
 <xref:System.Xml.XmlNamespaceManager> Objekt může být použitý v dotazu v každé z následujících způsobů.  
  
- <xref:System.Xml.XmlNamespaceManager> Objekt je spojen s existujícím <xref:System.Xml.XPath.XPathExpression> s použitím <xref:System.Xml.XPath.XPathExpression.SetContext%2A> metodu <xref:System.Xml.XPath.XPathExpression> objektu. Také může zkompilovat nový <xref:System.Xml.XPath.XPathExpression> pomocí statické <xref:System.Xml.XPath.XPathExpression.Compile%2A> metodu, která přebírá řetězec představující výraz XPath a <xref:System.Xml.XmlNamespaceManager> jako parametry a vrátí nový objekt <xref:System.Xml.XPath.XPathExpression> objektu.  
  
- <xref:System.Xml.XmlNamespaceManager> Samotný objekt je předán jako parametr přijímání <xref:System.Xml.XPath.XPathNavigator> metoda spolu s řetězec představující výraz XPath třídy.  
  
 Toto jsou metody <xref:System.Xml.XPath.XPathNavigator> třídu, která typu reference přijmout objekt odvozený od <xref:System.Xml.IXmlNamespaceResolver> rozhraní jako parametr.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a>Výchozí Namespace  
 V dokumentu XML, který následuje, výchozí obor názvů s prázdnou předponu slouží k deklaraci `http://www.contoso.com/books` oboru názvů.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 Výraz XPath prázdnou předponu považuje `null` oboru názvů. Jinými slovy lze použít pouze předpony, které jsou namapované na obory názvů v dotazy XPath. To znamená, pokud chcete zadat dotaz na obor názvů v dokumentu XML, i když jsou výchozí obor názvů, budete muset definovat předponu pro něj.  
  
 Například bez definování předponu pro dokument XML výše, XPath dotaz `/books/book` nebudou nalezeny žádné výsledky.  
  
 Aby se zabránilo nejednoznačnosti při dotazování dokumentů pomocí některé uzly není v oboru názvů a některé ve výchozím oboru názvů musí být vázán předponu.  
  
 Následující kód definuje předponu pro výchozí obor názvů a vybere všechny `book` elementy ze `http://www.contoso.com/books` oboru názvů.  
  
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
