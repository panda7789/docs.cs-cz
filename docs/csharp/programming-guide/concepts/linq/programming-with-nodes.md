---
title: Programování s uzly (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 05c2e95fe97effda7b537a7ac2d8f5780f4e212b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168311"
---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="5b161-102">Programování s uzly (C#)</span><span class="sxs-lookup"><span data-stu-id="5b161-102">Programming with Nodes (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5b161-103">Vývojáři, kteří potřebují psát programy, jako je editor XML, transformační systém nebo zapisovatel sestavy, často potřebují psát programy, které pracují na jemnější úrovni rozlišovací schopnosti než prvky a atributy.</span><span class="sxs-lookup"><span data-stu-id="5b161-103">developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="5b161-104">Často je třeba pracovat na úrovni uzlu, manipulace s textovými uzly, pokyny pro zpracování a komentáře.</span><span class="sxs-lookup"><span data-stu-id="5b161-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="5b161-105">Toto téma obsahuje některé podrobnosti o programování na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="5b161-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="5b161-106">Podrobnosti o uzlu</span><span class="sxs-lookup"><span data-stu-id="5b161-106">Node Details</span></span>  
 <span data-ttu-id="5b161-107">Existuje celá řada podrobností o programování, které programátor pracující na úrovni uzlu by měl vědět.</span><span class="sxs-lookup"><span data-stu-id="5b161-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="5b161-108">Nadřazená vlastnost podřízených uzlů XDocument je nastavena na hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="5b161-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="5b161-109">Vlastnost <xref:System.Xml.Linq.XObject.Parent%2A> obsahuje nadřazený <xref:System.Xml.Linq.XElement>uzel , nikoli nadřazený uzel.</span><span class="sxs-lookup"><span data-stu-id="5b161-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="5b161-110">Podřízené uzly <xref:System.Xml.Linq.XElement>nemají nadřazenou položku <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="5b161-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="5b161-111">Jejich nadřazený <xref:System.Xml.Linq.XObject.Parent%2A> je dokument, takže vlastnost pro tyto uzly je nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5b161-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="5b161-112">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="5b161-112">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="5b161-113">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5b161-113">This example produces the following output:</span></span>  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="5b161-114">Sousední textové uzly jsou možné</span><span class="sxs-lookup"><span data-stu-id="5b161-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="5b161-115">V řadě programovacích modelů XML jsou sousední textové uzly vždy sloučeny.</span><span class="sxs-lookup"><span data-stu-id="5b161-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="5b161-116">To se někdy nazývá normalizace textových uzlů.</span><span class="sxs-lookup"><span data-stu-id="5b161-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5b161-117">nenormalizuje textové uzly.</span><span class="sxs-lookup"><span data-stu-id="5b161-117">does not normalize text nodes.</span></span> <span data-ttu-id="5b161-118">Pokud přidáte dva textové uzly do stejného prvku, bude výsledkem sousední textové uzly.</span><span class="sxs-lookup"><span data-stu-id="5b161-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="5b161-119">Pokud však přidáte obsah určený jako řetězec, nikoli [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jako uzel, <xref:System.Xml.Linq.XText> může řetězec sloučit s sousedním textovým uzlem.</span><span class="sxs-lookup"><span data-stu-id="5b161-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="5b161-120">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="5b161-120">The following example demonstrates this:</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does not add a new text node  
xmlTree.Add("new content");  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does add a new, adjacent text node  
xmlTree.Add(new XText("more text"));  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
```  
  
 <span data-ttu-id="5b161-121">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5b161-121">This example produces the following output:</span></span>  
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="5b161-122">Prázdné textové uzly jsou možné</span><span class="sxs-lookup"><span data-stu-id="5b161-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="5b161-123">V některých programovacích modelech XML je zaručeno, že textové uzly neobsahují prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5b161-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="5b161-124">Důvodem je, že takový textový uzel nemá žádný vliv na serializaci XML.</span><span class="sxs-lookup"><span data-stu-id="5b161-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="5b161-125">Ze stejného důvodu, že sousední textové uzly jsou možné, pokud odeberete text z textového uzlu nastavením jeho hodnoty na prázdný řetězec, samotný textový uzel nebude odstraněn.</span><span class="sxs-lookup"><span data-stu-id="5b161-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);
```  
  
 <span data-ttu-id="5b161-126">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5b161-126">This example produces the following output:</span></span>  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="5b161-127">Prázdný textový uzel ovlivňuje serializaci</span><span class="sxs-lookup"><span data-stu-id="5b161-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="5b161-128">Pokud prvek obsahuje pouze podřízený textový uzel, který je prázdný, je `<Child></Child>`serializován s syntaxí dlouhé značky: .</span><span class="sxs-lookup"><span data-stu-id="5b161-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="5b161-129">Pokud prvek neobsahuje žádné podřízené uzly, je serializován `<Child />`s syntaxí krátké značky: .</span><span class="sxs-lookup"><span data-stu-id="5b161-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);
```  
  
 <span data-ttu-id="5b161-130">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5b161-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="5b161-131">Obory názvů jsou atributy ve stromu LINQ do stromu XML</span><span class="sxs-lookup"><span data-stu-id="5b161-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="5b161-132">I když deklarace oboru názvů mají identickou syntaxi atributů, v některých programovacích rozhraních, jako jsou XSLT a XPath, deklarace oboru názvů nejsou považovány za atributy.</span><span class="sxs-lookup"><span data-stu-id="5b161-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="5b161-133">V aplikaci jsou [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]však <xref:System.Xml.Linq.XAttribute> obory názvů uloženy jako objekty ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="5b161-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="5b161-134">Pokud iterát prostřednictvím atributy pro prvek, který obsahuje deklaraci oboru názvů, zobrazí se deklarace oboru názvů jako jedna z položek ve vrácené kolekci.</span><span class="sxs-lookup"><span data-stu-id="5b161-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="5b161-135">Vlastnost <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> označuje, zda je atribut deklarací oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5b161-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="5b161-136">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5b161-136">This example produces the following output:</span></span>  
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="5b161-137">Metody osy XPath nevracejí podřízený prázdné místo xdocument</span><span class="sxs-lookup"><span data-stu-id="5b161-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5b161-138">umožňuje podřízené textové uzly <xref:System.Xml.Linq.XDocument>, pokud textové uzly obsahují pouze prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="5b161-138">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="5b161-139">Objektový model XPath však neobsahuje prázdné místo jako podřízené uzly dokumentu, takže <xref:System.Xml.Linq.XDocument> při <xref:System.Xml.Linq.XContainer.Nodes%2A> iterace prostřednictvím podřízených objektů pomocí osy budou vráceny prázdné textové uzly.</span><span class="sxs-lookup"><span data-stu-id="5b161-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white-space text nodes will be returned.</span></span> <span data-ttu-id="5b161-140">Však při iterace prostřednictvím <xref:System.Xml.Linq.XDocument> podřízených pomocí metody osy XPath, prázdné textové uzly nebudou vráceny.</span><span class="sxs-lookup"><span data-stu-id="5b161-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white-space text nodes will not be returned.</span></span>  
  
```csharp  
// Create a document with some white-space child nodes of the document.  
XDocument root = XDocument.Parse(  
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
  
<Root/>  
  
<!--a comment-->  
", LoadOptions.PreserveWhitespace);  
  
// count the white-space child nodes using LINQ to XML  
Console.WriteLine(root.Nodes().OfType<XText>().Count());  
  
// count the white-space child nodes using XPathEvaluate  
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());
```  
  
 <span data-ttu-id="5b161-141">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5b161-141">This example produces the following output:</span></span>  
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="5b161-142">Objekty XDeclaration nejsou uzly</span><span class="sxs-lookup"><span data-stu-id="5b161-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="5b161-143">Při itetu prostřednictvím podřízených <xref:System.Xml.Linq.XDocument>uzlů , neuvidíte objekt deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="5b161-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="5b161-144">Je vlastnostdokumentu, nikoli podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="5b161-144">It is a property of the document, not a child node of it.</span></span>  
  
```csharp  
XDocument doc = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root")  
);  
doc.Save("Temp.xml");  
Console.WriteLine(File.ReadAllText("Temp.xml"));  
  
// this shows that there is only one child node of the document  
Console.WriteLine(doc.Nodes().Count());  
```  
  
 <span data-ttu-id="5b161-145">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5b161-145">This example produces the following output:</span></span>  
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  