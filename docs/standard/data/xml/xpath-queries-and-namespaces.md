---
title: "Dotazy XPath a obory názvů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eeed1594582765e5079aa1e3d82f95737a79d1f0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="44d91-102">Dotazy XPath a obory názvů</span><span class="sxs-lookup"><span data-stu-id="44d91-102">XPath Queries and Namespaces</span></span>
<span data-ttu-id="44d91-103">Dotazy XPath věděli, obory názvů v dokumentu XML a předpony oboru názvů můžete použít k vyfiltrování názvy elementu a atributu.</span><span class="sxs-lookup"><span data-stu-id="44d91-103">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="44d91-104">Kvalifikující názvy elementu a atributu předponu oboru názvů omezuje uzly vrácený dotaz XPath pro pouze uzly, které patří do konkrétní oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="44d91-104">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="44d91-105">Například pokud předponu `books` mapy do oboru názvů `http://www.contoso.com/books`, pak následující dotaz XPath `/books:books/books:book` vybere pouze ty `book` elementy v oboru názvů `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="44d91-105">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="44d91-106">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="44d91-106">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="44d91-107">V dotaz XPath použít obory názvů, objekt odvozené z <xref:System.Xml.IXmlNamespaceResolver> rozhraní jako <xref:System.Xml.XmlNamespaceManager> třída je vytvořený pomocí identifikátor URI oboru názvů a předpony, které chcete zahrnout do dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="44d91-107">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="44d91-108"><xref:System.Xml.XmlNamespaceManager> Objektu může být použitý v dotazu v každé z následujících způsobů.</span><span class="sxs-lookup"><span data-stu-id="44d91-108">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
-   <span data-ttu-id="44d91-109"><xref:System.Xml.XmlNamespaceManager> Objekt je přidružený ke stávající <xref:System.Xml.XPath.XPathExpression> objekt pomocí <xref:System.Xml.XPath.XPathExpression.SetContext%2A> metodu <xref:System.Xml.XPath.XPathExpression> objektu.</span><span class="sxs-lookup"><span data-stu-id="44d91-109">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="44d91-110">Může také zkompilujete novou <xref:System.Xml.XPath.XPathExpression> pomocí statické <xref:System.Xml.XPath.XPathExpression.Compile%2A> metoda, která přebírá řetězec představující výraz XPath a <xref:System.Xml.XmlNamespaceManager> objektu jako parametry a vrátí nové <xref:System.Xml.XPath.XPathExpression> objektu.</span><span class="sxs-lookup"><span data-stu-id="44d91-110">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
-   <span data-ttu-id="44d91-111"><xref:System.Xml.XmlNamespaceManager> Samotného objektu je předán jako parametr přijetí <xref:System.Xml.XPath.XPathNavigator> třídy metoda společně s řetězec představující výraz XPath.</span><span class="sxs-lookup"><span data-stu-id="44d91-111">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="44d91-112">Toto jsou metody <xref:System.Xml.XPath.XPathNavigator> třídu, která přijmout objekt odvozené z <xref:System.Xml.IXmlNamespaceResolver> rozhraní jako parametr.</span><span class="sxs-lookup"><span data-stu-id="44d91-112">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="44d91-113">Namespace výchozí</span><span class="sxs-lookup"><span data-stu-id="44d91-113">The Default Namespace</span></span>  
 <span data-ttu-id="44d91-114">V dokumentu XML, který následuje, je výchozí obor názvů s prázdnou předponu používá k deklaraci `http://www.contoso.com/books` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="44d91-114">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.example.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="44d91-115">Výraz XPath jsou považovány za prázdnou předponu `null` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="44d91-115">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="44d91-116">Jinými slovy lze použít pouze předpon, které jsou namapované na obory názvů dotazů XPath.</span><span class="sxs-lookup"><span data-stu-id="44d91-116">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="44d91-117">To znamená, že pokud chcete dotaz proti oboru názvů v dokumentu XML, i když je výchozí obor názvů, budete muset definovat předponu pro něj.</span><span class="sxs-lookup"><span data-stu-id="44d91-117">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="44d91-118">Například bez definování předponu pro dokument XML výše jazyka XPath dotaz `/books/book` nebude nevrátí žádné výsledky.</span><span class="sxs-lookup"><span data-stu-id="44d91-118">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="44d91-119">Aby se zabránilo nejednoznačnosti při dotazování dokumentů pomocí některé uzly nejsou v oboru názvů a některé v výchozí obor názvů musí být vázána předponu.</span><span class="sxs-lookup"><span data-stu-id="44d91-119">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="44d91-120">Následující kód definuje předponu pro výchozí obor názvů a vybere všechny `book` elementy z `http://www.contoso.com/books` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="44d91-120">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44d91-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="44d91-121">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="44d91-122">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="44d91-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="44d91-123">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="44d91-123">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="44d91-124">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="44d91-124">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="44d91-125">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="44d91-125">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="44d91-126">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="44d91-126">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="44d91-127">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="44d91-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
