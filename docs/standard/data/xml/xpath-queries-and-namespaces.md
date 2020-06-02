---
title: Dotazy a obory názvů XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: d3314a7ff4cf957dac4cd8ad0416aad434b19af2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283192"
---
# <a name="xpath-queries-and-namespaces"></a>Dotazy a obory názvů XPath
Dotazy XPath mají na paměti obory názvů v dokumentu XML a můžou použít předpony oboru názvů k získání názvů elementů a atributů. Kvalifikování názvů elementů a atributů s předponou oboru názvů omezuje uzly vrácené dotazem XPath pouze na ty uzly, které patří do konkrétního oboru názvů.  
  
 Například pokud předpona `books` mapuje na obor názvů `http://www.contoso.com/books` , pak následující dotaz XPath `/books:books/books:book` vybere pouze ty `book` prvky v oboru názvů `http://www.contoso.com/books` .  
  
## <a name="the-xmlnamespacemanager"></a>XmlNamespaceManager  
 Chcete-li použít obory názvů v dotazu XPath, objekt odvozený z <xref:System.Xml.IXmlNamespaceResolver> rozhraní, jako je <xref:System.Xml.XmlNamespaceManager> třída, je VYTVOŘEN pomocí identifikátoru URI a předpony oboru názvů, které mají být zahrnuty do dotazu XPath.  
  
 <xref:System.Xml.XmlNamespaceManager>Objekt může být v dotazu použit v každém z následujících způsobů.  
  
- <xref:System.Xml.XmlNamespaceManager>Objekt je přidružen k existujícímu <xref:System.Xml.XPath.XPathExpression> objektu pomocí <xref:System.Xml.XPath.XPathExpression.SetContext%2A> metody <xref:System.Xml.XPath.XPathExpression> objektu. Můžete také kompilovat nový <xref:System.Xml.XPath.XPathExpression> objekt pomocí statické <xref:System.Xml.XPath.XPathExpression.Compile%2A> metody, která přijímá řetězec představující výraz XPath a <xref:System.Xml.XmlNamespaceManager> objekt jako parametry a vrací nový <xref:System.Xml.XPath.XPathExpression> objekt.  
  
- <xref:System.Xml.XmlNamespaceManager>Samotný objekt je předán jako parametr do přijímací <xref:System.Xml.XPath.XPathNavigator> metody třídy společně s řetězcem představujícím výraz XPath.  
  
 Níže jsou uvedené metody <xref:System.Xml.XPath.XPathNavigator> třídy, které přijímají objekt odvozený z <xref:System.Xml.IXmlNamespaceResolver> rozhraní jako parametr.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a>Výchozí obor názvů  
 V dokumentu XML, který následuje, je pro deklaraci oboru názvů použit výchozí obor názvů s prázdnou předponou `http://www.contoso.com/books` .  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 XPath zpracovává prázdnou předponu jako `null` obor názvů. Jinými slovy, v dotazech XPath lze použít pouze předpony mapované na obory názvů. To znamená, že pokud chcete dotazovat na obor názvů v dokumentu XML, i když se jedná o výchozí obor názvů, musíte pro něj definovat předponu.  
  
 Například bez definice prefixu pro dokument XML výše `/books/book` nevrátí dotaz XPath žádné výsledky.  
  
 Předpona musí být vázána, aby zabránila nejednoznačnosti při dotazování dokumentů s některými uzly, které nejsou v oboru názvů, a některé ve výchozím oboru názvů.  
  
 Následující kód definuje předponu pro výchozí obor názvů a vybere všechny `book` prvky z `http://www.contoso.com/books` oboru názvů.  
  
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

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Zpracování dat XML pomocí modelu dat XPath](process-xml-data-using-the-xpath-data-model.md)
- [Výběr dat XML pomocí XPathNavigator](select-xml-data-using-xpathnavigator.md)
- [Vyhodnocení výrazů XPath pomocí XPathNavigator](evaluate-xpath-expressions-using-xpathnavigator.md)
- [Párování uzlů pomocí XPathNavigator](matching-nodes-using-xpathnavigator.md)
- [Rozpoznané typy uzlů s dotazy XPath](node-types-recognized-with-xpath-queries.md)
- [Zkompilované výrazy XPath](compiled-xpath-expressions.md)
