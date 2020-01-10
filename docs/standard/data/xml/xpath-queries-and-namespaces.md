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
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="5d9fb-102">Dotazy a obory názvů XPath</span><span class="sxs-lookup"><span data-stu-id="5d9fb-102">XPath Queries and Namespaces</span></span>
<span data-ttu-id="5d9fb-103">Dotazy XPath mají na paměti obory názvů v dokumentu XML a můžou použít předpony oboru názvů k získání názvů elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-103">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="5d9fb-104">Kvalifikování názvů elementů a atributů s předponou oboru názvů omezuje uzly vrácené dotazem XPath pouze na ty uzly, které patří do konkrétního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-104">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="5d9fb-105">Například pokud předpona `books` namapována na obor názvů `http://www.contoso.com/books`, pak následující dotaz XPath `/books:books/books:book` vybere pouze ty `book` elementy v oboru názvů `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-105">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="5d9fb-106">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="5d9fb-106">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="5d9fb-107">Chcete-li použít obory názvů v dotazu XPath, objekt odvozený z rozhraní <xref:System.Xml.IXmlNamespaceResolver>, jako je <xref:System.Xml.XmlNamespaceManager> třída, je vytvořen pomocí identifikátoru URI a předpony oboru názvů, které mají být zahrnuty do dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-107">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="5d9fb-108">Objekt <xref:System.Xml.XmlNamespaceManager> může být v dotazu použit v každém z následujících způsobů.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-108">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
- <span data-ttu-id="5d9fb-109">Objekt <xref:System.Xml.XmlNamespaceManager> je přidružen k existujícímu objektu <xref:System.Xml.XPath.XPathExpression> pomocí metody <xref:System.Xml.XPath.XPathExpression.SetContext%2A> objektu <xref:System.Xml.XPath.XPathExpression>.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-109">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="5d9fb-110">Můžete také zkompilovat nový objekt <xref:System.Xml.XPath.XPathExpression> pomocí metody static <xref:System.Xml.XPath.XPathExpression.Compile%2A>, která přebírá řetězec představující výraz XPath a objekt <xref:System.Xml.XmlNamespaceManager> jako parametry a vrací nový objekt <xref:System.Xml.XPath.XPathExpression>.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-110">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
- <span data-ttu-id="5d9fb-111">Samotný objekt <xref:System.Xml.XmlNamespaceManager> je předán jako parametr pro přijetí metody <xref:System.Xml.XPath.XPathNavigator> třídy spolu s řetězcem představujícím výraz XPath.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-111">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="5d9fb-112">Níže jsou uvedené metody třídy <xref:System.Xml.XPath.XPathNavigator>, které přijímají objekt odvozený z rozhraní <xref:System.Xml.IXmlNamespaceResolver> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-112">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="5d9fb-113">Výchozí obor názvů</span><span class="sxs-lookup"><span data-stu-id="5d9fb-113">The Default Namespace</span></span>  
 <span data-ttu-id="5d9fb-114">V dokumentu XML, který následuje, je použit výchozí obor názvů s prázdnou předponou pro deklaraci oboru názvů `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-114">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="5d9fb-115">XPath zpracovává prázdnou předponu jako obor názvů `null`.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-115">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="5d9fb-116">Jinými slovy, v dotazech XPath lze použít pouze předpony mapované na obory názvů.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-116">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="5d9fb-117">To znamená, že pokud chcete dotazovat na obor názvů v dokumentu XML, i když se jedná o výchozí obor názvů, musíte pro něj definovat předponu.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-117">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="5d9fb-118">Například bez definice prefixu pro dokument XML výše, `/books/book` dotaz XPath nevrátí žádné výsledky.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-118">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="5d9fb-119">Předpona musí být vázána, aby zabránila nejednoznačnosti při dotazování dokumentů s některými uzly, které nejsou v oboru názvů, a některé ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-119">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="5d9fb-120">Následující kód definuje předponu pro výchozí obor názvů a vybere všechny `book` prvky z oboru názvů `http://www.contoso.com/books`.</span><span class="sxs-lookup"><span data-stu-id="5d9fb-120">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d9fb-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d9fb-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="5d9fb-122">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="5d9fb-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="5d9fb-123">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5d9fb-123">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="5d9fb-124">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5d9fb-124">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="5d9fb-125">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5d9fb-125">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="5d9fb-126">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="5d9fb-126">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="5d9fb-127">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="5d9fb-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
