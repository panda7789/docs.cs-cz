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
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="dbc6e-102">Dotazy a obory názvů XPath</span><span class="sxs-lookup"><span data-stu-id="dbc6e-102">XPath Queries and Namespaces</span></span>
<span data-ttu-id="dbc6e-103">Dotazy XPath mají na paměti obory názvů v dokumentu XML a můžou použít předpony oboru názvů k získání názvů elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-103">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="dbc6e-104">Kvalifikování názvů elementů a atributů s předponou oboru názvů omezuje uzly vrácené dotazem XPath pouze na ty uzly, které patří do konkrétního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-104">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="dbc6e-105">`books` Například pokud předpona mapuje na obor názvů `http://www.contoso.com/books`, pak následující dotaz `/books:books/books:book` XPath vybere pouze ty `book` prvky v oboru názvů. `http://www.contoso.com/books`</span><span class="sxs-lookup"><span data-stu-id="dbc6e-105">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="dbc6e-106">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="dbc6e-106">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="dbc6e-107">Chcete-li použít obory názvů v dotazu XPath, objekt odvozený z <xref:System.Xml.IXmlNamespaceResolver> rozhraní <xref:System.Xml.XmlNamespaceManager> , jako je třída, je vytvořen pomocí identifikátoru URI a předpony oboru názvů, které mají být zahrnuty do dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-107">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="dbc6e-108"><xref:System.Xml.XmlNamespaceManager> Objekt může být v dotazu použit v každém z následujících způsobů.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-108">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
- <span data-ttu-id="dbc6e-109"><xref:System.Xml.XmlNamespaceManager> Objekt je přidružen k existujícímu <xref:System.Xml.XPath.XPathExpression> objektu pomocí <xref:System.Xml.XPath.XPathExpression.SetContext%2A> metody <xref:System.Xml.XPath.XPathExpression> objektu.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-109">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="dbc6e-110">Můžete <xref:System.Xml.XPath.XPathExpression> také kompilovat nový objekt pomocí statické <xref:System.Xml.XPath.XPathExpression.Compile%2A> metody, která přijímá řetězec představující výraz XPath a <xref:System.Xml.XmlNamespaceManager> objekt jako parametry a vrací nový <xref:System.Xml.XPath.XPathExpression> objekt.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-110">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
- <span data-ttu-id="dbc6e-111">Samotný <xref:System.Xml.XmlNamespaceManager> objekt je předán jako parametr do přijímací <xref:System.Xml.XPath.XPathNavigator> metody třídy společně s řetězcem představujícím výraz XPath.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-111">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="dbc6e-112">Níže jsou uvedené metody <xref:System.Xml.XPath.XPathNavigator> třídy, které přijímají objekt odvozený z <xref:System.Xml.IXmlNamespaceResolver> rozhraní jako parametr.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-112">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="dbc6e-113">Výchozí obor názvů</span><span class="sxs-lookup"><span data-stu-id="dbc6e-113">The Default Namespace</span></span>  
 <span data-ttu-id="dbc6e-114">V dokumentu XML, který následuje, je pro deklaraci `http://www.contoso.com/books` oboru názvů použit výchozí obor názvů s prázdnou předponou.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-114">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="dbc6e-115">XPath zpracovává prázdnou předponu jako `null` obor názvů.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-115">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="dbc6e-116">Jinými slovy, v dotazech XPath lze použít pouze předpony mapované na obory názvů.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-116">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="dbc6e-117">To znamená, že pokud chcete dotazovat na obor názvů v dokumentu XML, i když se jedná o výchozí obor názvů, musíte pro něj definovat předponu.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-117">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="dbc6e-118">Například bez definice prefixu pro dokument XML výše nevrátí dotaz `/books/book` XPath žádné výsledky.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-118">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="dbc6e-119">Předpona musí být vázána, aby zabránila nejednoznačnosti při dotazování dokumentů s některými uzly, které nejsou v oboru názvů, a některé ve výchozím oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-119">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="dbc6e-120">Následující kód definuje předponu pro výchozí obor názvů a vybere všechny `book` prvky z `http://www.contoso.com/books` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="dbc6e-120">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dbc6e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbc6e-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="dbc6e-122">Zpracování dat XML pomocí modelu dat XPath</span><span class="sxs-lookup"><span data-stu-id="dbc6e-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="dbc6e-123">Výběr dat XML pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="dbc6e-123">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="dbc6e-124">Vyhodnocení výrazů XPath pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="dbc6e-124">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="dbc6e-125">Párování uzlů pomocí XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="dbc6e-125">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="dbc6e-126">Rozpoznané typy uzlů s dotazy XPath</span><span class="sxs-lookup"><span data-stu-id="dbc6e-126">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="dbc6e-127">Zkompilované výrazy XPath</span><span class="sxs-lookup"><span data-stu-id="dbc6e-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
