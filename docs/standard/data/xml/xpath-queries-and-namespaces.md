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
ms.openlocfilehash: 5f35725f5e1a08f2fcb1d6bc87765f50308c963f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026780"
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="11bac-102">Dotazy a obory názvů XPath</span><span class="sxs-lookup"><span data-stu-id="11bac-102">XPath Queries and Namespaces</span></span>
<span data-ttu-id="11bac-103">Dotazy XPath vědomi obory názvů v dokumentu XML a předpony oboru názvů můžete použít k vyfiltrování názvy prvků a atributů.</span><span class="sxs-lookup"><span data-stu-id="11bac-103">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="11bac-104">Kvalifikující názvy prvků a atributů s předponu oboru názvů omezí vrácené dotaz XPath pro pouze ty uzly, které patří do konkrétní obor názvů uzly.</span><span class="sxs-lookup"><span data-stu-id="11bac-104">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="11bac-105">Například pokud předponu `books` mapuje na obor názvů `http://www.contoso.com/books`, pak následující dotaz XPath `/books:books/books:book` vybere pouze ty `book` prvky v oboru názvů `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="11bac-105">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="11bac-106">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="11bac-106">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="11bac-107">Obory názvů používané dotaz XPath, objekt odvozený z <xref:System.Xml.IXmlNamespaceResolver> rozhraní jako <xref:System.Xml.XmlNamespaceManager> třídy je vytvořený pomocí identifikátoru URI oboru názvů a předpony, které mají být zahrnuty dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="11bac-107">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="11bac-108"><xref:System.Xml.XmlNamespaceManager> Objekt může být použitý v dotazu v každé z následujících způsobů.</span><span class="sxs-lookup"><span data-stu-id="11bac-108">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
- <span data-ttu-id="11bac-109"><xref:System.Xml.XmlNamespaceManager> Objekt je spojen s existujícím <xref:System.Xml.XPath.XPathExpression> s použitím <xref:System.Xml.XPath.XPathExpression.SetContext%2A> metodu <xref:System.Xml.XPath.XPathExpression> objektu.</span><span class="sxs-lookup"><span data-stu-id="11bac-109">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="11bac-110">Také může zkompilovat nový <xref:System.Xml.XPath.XPathExpression> pomocí statické <xref:System.Xml.XPath.XPathExpression.Compile%2A> metodu, která přebírá řetězec představující výraz XPath a <xref:System.Xml.XmlNamespaceManager> jako parametry a vrátí nový objekt <xref:System.Xml.XPath.XPathExpression> objektu.</span><span class="sxs-lookup"><span data-stu-id="11bac-110">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
- <span data-ttu-id="11bac-111"><xref:System.Xml.XmlNamespaceManager> Samotný objekt je předán jako parametr přijímání <xref:System.Xml.XPath.XPathNavigator> metoda spolu s řetězec představující výraz XPath třídy.</span><span class="sxs-lookup"><span data-stu-id="11bac-111">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="11bac-112">Toto jsou metody <xref:System.Xml.XPath.XPathNavigator> třídu, která typu reference přijmout objekt odvozený od <xref:System.Xml.IXmlNamespaceResolver> rozhraní jako parametr.</span><span class="sxs-lookup"><span data-stu-id="11bac-112">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="11bac-113">Výchozí Namespace</span><span class="sxs-lookup"><span data-stu-id="11bac-113">The Default Namespace</span></span>  
 <span data-ttu-id="11bac-114">V dokumentu XML, který následuje, výchozí obor názvů s prázdnou předponu slouží k deklaraci `http://www.contoso.com/books` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="11bac-114">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="11bac-115">Výraz XPath prázdnou předponu považuje `null` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="11bac-115">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="11bac-116">Jinými slovy lze použít pouze předpony, které jsou namapované na obory názvů v dotazy XPath.</span><span class="sxs-lookup"><span data-stu-id="11bac-116">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="11bac-117">To znamená, pokud chcete zadat dotaz na obor názvů v dokumentu XML, i když jsou výchozí obor názvů, budete muset definovat předponu pro něj.</span><span class="sxs-lookup"><span data-stu-id="11bac-117">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="11bac-118">Například bez definování předponu pro dokument XML výše, XPath dotaz `/books/book` nebudou nalezeny žádné výsledky.</span><span class="sxs-lookup"><span data-stu-id="11bac-118">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="11bac-119">Aby se zabránilo nejednoznačnosti při dotazování dokumentů pomocí některé uzly není v oboru názvů a některé ve výchozím oboru názvů musí být vázán předponu.</span><span class="sxs-lookup"><span data-stu-id="11bac-119">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="11bac-120">Následující kód definuje předponu pro výchozí obor názvů a vybere všechny `book` elementy ze `http://www.contoso.com/books` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="11bac-120">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11bac-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11bac-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="11bac-122">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="11bac-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="11bac-123">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="11bac-123">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="11bac-124">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="11bac-124">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="11bac-125">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="11bac-125">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="11bac-126">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="11bac-126">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="11bac-127">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="11bac-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
