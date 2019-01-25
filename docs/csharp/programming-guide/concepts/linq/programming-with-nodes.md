---
title: Programování s uzly (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 0924d7b1d25a33635cc5140ca32622658b10fa0e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730175"
---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="82f27-102">Programování s uzly (C#)</span><span class="sxs-lookup"><span data-stu-id="82f27-102">Programming with Nodes (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="82f27-103">vývojářům, kteří potřebují psát programy, jako je například XML editor, systém transformace nebo Autor sestavy často potřeba psát programy, které fungují na jemnější úrovni členitosti než elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="82f27-103">developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="82f27-104">Často potřebují pracovat na úrovni uzlu manipulace s uzly text, instrukce ke zpracování a komentáře.</span><span class="sxs-lookup"><span data-stu-id="82f27-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="82f27-105">Toto téma obsahuje podrobnosti o programování na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="82f27-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="82f27-106">Podrobnosti o uzlu</span><span class="sxs-lookup"><span data-stu-id="82f27-106">Node Details</span></span>  
 <span data-ttu-id="82f27-107">Existuje mnoho detailů programování, které byste měli mít programátor funguje na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="82f27-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="82f27-108">Nadřazená vlastnost z podřízené uzly z XDocument nastaven na hodnotu Null</span><span class="sxs-lookup"><span data-stu-id="82f27-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="82f27-109"><xref:System.Xml.Linq.XObject.Parent%2A> Vlastnost obsahuje nadřazené <xref:System.Xml.Linq.XElement>, není nadřazený uzel.</span><span class="sxs-lookup"><span data-stu-id="82f27-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="82f27-110">Podřízené uzly <xref:System.Xml.Linq.XDocument> mít žádný nadřazený objekt <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="82f27-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="82f27-111">Jejich nadřazené je dokument, takže <xref:System.Xml.Linq.XObject.Parent%2A> pro ty uzly, je hodnota nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="82f27-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="82f27-112">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="82f27-112">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="82f27-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="82f27-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="82f27-114">Sousední textové uzly jsou možné</span><span class="sxs-lookup"><span data-stu-id="82f27-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="82f27-115">V řadě programovacích modelů XML jsou vždy sloučeny sousední textové uzly.</span><span class="sxs-lookup"><span data-stu-id="82f27-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="82f27-116">To se někdy nazývá normalizace textové uzly.</span><span class="sxs-lookup"><span data-stu-id="82f27-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="82f27-117">není normalizovat textové uzly.</span><span class="sxs-lookup"><span data-stu-id="82f27-117">does not normalize text nodes.</span></span> <span data-ttu-id="82f27-118">Pokud chcete přidat dva textové uzly stejného elementu, jinak dojde sousední textové uzly.</span><span class="sxs-lookup"><span data-stu-id="82f27-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="82f27-119">Ale pokud chcete přidat obsah určený jako řetězce, nikoli jako <xref:System.Xml.Linq.XText> uzlu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může sloučit řetězec s sousední textový uzel.</span><span class="sxs-lookup"><span data-stu-id="82f27-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="82f27-120">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="82f27-120">The following example demonstrates this:</span></span>  
  
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
  
 <span data-ttu-id="82f27-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="82f27-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="82f27-122">Co jsou prázdné textové uzly</span><span class="sxs-lookup"><span data-stu-id="82f27-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="82f27-123">V některých programovací modely jazyka XML je zaručeno textové uzly nesmí obsahovat prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="82f27-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="82f27-124">Důvody, proč je, že textový uzel nemá žádný vliv na serializace XML.</span><span class="sxs-lookup"><span data-stu-id="82f27-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="82f27-125">Ale ze stejného důvodu, které jsou uzly okolního textu možná, pokud odeberete text z textového uzlu tak, že nastavíte její hodnotu na prázdný řetězec, samotný uzel text se neodstraní.</span><span class="sxs-lookup"><span data-stu-id="82f27-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 <span data-ttu-id="82f27-126">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="82f27-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="82f27-127">Prázdný textový uzel má vliv na serializace</span><span class="sxs-lookup"><span data-stu-id="82f27-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="82f27-128">Pokud element obsahuje pouze podřízený textový uzel, který je prázdný, je serializován pomocí syntaxe dlouhé značek: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="82f27-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="82f27-129">Pokud element obsahuje podřízené uzly jakýmkoli způsobem, je serializované pomocí syntaxe krátký značek: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="82f27-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 <span data-ttu-id="82f27-130">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="82f27-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="82f27-131">Obory názvů jsou atributy v technologii LINQ to XML stromu</span><span class="sxs-lookup"><span data-stu-id="82f27-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="82f27-132">I když deklarace oboru názvů mají stejné syntaxi atributů, v některých rozhraních programování, jako je například XSLT a výraz XPath, deklarace oboru názvů nejsou považovány za atributy.</span><span class="sxs-lookup"><span data-stu-id="82f27-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="82f27-133">Nicméně v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], obory názvů jsou uloženy jako <xref:System.Xml.Linq.XAttribute> objekty ve stromové struktuře XML.</span><span class="sxs-lookup"><span data-stu-id="82f27-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="82f27-134">Pokud iteraci atributy pro element, který obsahuje deklarace oboru názvů, uvidíte jako jednu z položek v kolekci vrácené deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="82f27-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="82f27-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Vlastnost určuje, zda je atribut deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="82f27-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="82f27-136">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="82f27-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="82f27-137">Metody osy XPath nevrátí podřízené prázdné znaky z XDocument</span><span class="sxs-lookup"><span data-stu-id="82f27-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="82f27-138">Umožňuje pro podřízené uzly text <xref:System.Xml.Linq.XDocument>, tak dlouho, dokud textové uzly obsahující jenom prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="82f27-138">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="82f27-139">Však XPath objektový model neobsahuje mezery jako podřízené uzly dokumentu, tak při iteraci podřízených položek <xref:System.Xml.Linq.XDocument> pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> osy, bude vrácen text prázdné znaky uzly.</span><span class="sxs-lookup"><span data-stu-id="82f27-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white-space text nodes will be returned.</span></span> <span data-ttu-id="82f27-140">Ale při iteraci podřízených položek <xref:System.Xml.Linq.XDocument> pomocí metod osy XPath, nebude vrácena uzly text prázdné místo.</span><span class="sxs-lookup"><span data-stu-id="82f27-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white-space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="82f27-141">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="82f27-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="82f27-142">XDeclaration objekty nejsou uzly</span><span class="sxs-lookup"><span data-stu-id="82f27-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="82f27-143">Při iteraci podřízené uzly <xref:System.Xml.Linq.XDocument>, neuvidíte objekt deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="82f27-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="82f27-144">Je to vlastnost dokumentu a jeho není podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="82f27-144">It is a property of the document, not a child node of it.</span></span>  
  
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
  
 <span data-ttu-id="82f27-145">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="82f27-145">This example produces the following output:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="82f27-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82f27-146">See also</span></span>

- [<span data-ttu-id="82f27-147">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="82f27-147">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
