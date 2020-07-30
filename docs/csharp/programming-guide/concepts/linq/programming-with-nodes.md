---
title: Programování s uzly (C#)
description: Přečtěte si o programování s použitím uzlů. To umožňuje vývojářům psát programy, které fungují na jemnější úrovni podrobností než prvky a atributy.
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8a31d6459ab644a682d480239cabc3d88fd7dc14
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301681"
---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="b4816-104">Programování s uzly (C#)</span><span class="sxs-lookup"><span data-stu-id="b4816-104">Programming with Nodes (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b4816-105">Vývojáři, kteří potřebují psát programy, jako je editor XML, transformační systém nebo zapisovač sestav, často potřebují psát programy, které fungují na jemnější úrovni členitosti než prvky a atributy.</span><span class="sxs-lookup"><span data-stu-id="b4816-105">developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="b4816-106">Často potřebují pracovat na úrovni uzlu, manipulaci s textovými uzly, pokyny pro zpracování a komentáře.</span><span class="sxs-lookup"><span data-stu-id="b4816-106">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="b4816-107">Toto téma poskytuje některé podrobnosti o programování na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="b4816-107">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="b4816-108">Podrobnosti uzlu</span><span class="sxs-lookup"><span data-stu-id="b4816-108">Node Details</span></span>  
 <span data-ttu-id="b4816-109">Existuje řada podrobných informací o programování, které by programátor pracující na úrovni uzlu měl znát.</span><span class="sxs-lookup"><span data-stu-id="b4816-109">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="b4816-110">Vlastnost Parent podřízených uzlů XDocument je nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b4816-110">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="b4816-111"><xref:System.Xml.Linq.XObject.Parent%2A>Vlastnost obsahuje nadřazenou položku <xref:System.Xml.Linq.XElement> , ne nadřazený uzel.</span><span class="sxs-lookup"><span data-stu-id="b4816-111">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="b4816-112">Podřízené uzly <xref:System.Xml.Linq.XDocument> nemají žádnou nadřazenou položku <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="b4816-112">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b4816-113">Jejich nadřazeným prvkem je dokument, takže <xref:System.Xml.Linq.XObject.Parent%2A> vlastnost pro tyto uzly je nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b4816-113">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="b4816-114">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="b4816-114">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="b4816-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b4816-115">This example produces the following output:</span></span>  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="b4816-116">Jsou možné sousední uzly textu.</span><span class="sxs-lookup"><span data-stu-id="b4816-116">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="b4816-117">V řadě programovacích modelů XML jsou sousední textové uzly vždycky sloučeny.</span><span class="sxs-lookup"><span data-stu-id="b4816-117">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="b4816-118">To se někdy označuje jako normalizace textových uzlů.</span><span class="sxs-lookup"><span data-stu-id="b4816-118">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b4816-119">nenormalizuje textové uzly.</span><span class="sxs-lookup"><span data-stu-id="b4816-119">does not normalize text nodes.</span></span> <span data-ttu-id="b4816-120">Pokud přidáte dva textové uzly do stejného elementu, bude výsledkem sousedících textových uzlů.</span><span class="sxs-lookup"><span data-stu-id="b4816-120">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="b4816-121">Pokud však přidáte obsah zadaný jako řetězec, nikoli jako <xref:System.Xml.Linq.XText> uzel, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může řetězec sloučit s sousedícím textovým uzlem.</span><span class="sxs-lookup"><span data-stu-id="b4816-121">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="b4816-122">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="b4816-122">The following example demonstrates this:</span></span>  
  
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
  
 <span data-ttu-id="b4816-123">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b4816-123">This example produces the following output:</span></span>  
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="b4816-124">Jsou možné prázdné textové uzly.</span><span class="sxs-lookup"><span data-stu-id="b4816-124">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="b4816-125">V některých programovacích modelech XML je zaručeno, že textové uzly nebudou obsahovat prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="b4816-125">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="b4816-126">Důvodem je, že takový textový uzel nemá žádný vliv na serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="b4816-126">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="b4816-127">Z toho důvodu, že když odeberete text z textového uzlu nastavením jeho hodnoty na prázdný řetězec, samotný textový uzel nebude odstraněn, ze stejného důvodu, že je možné použít sousední textové uzly.</span><span class="sxs-lookup"><span data-stu-id="b4816-127">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);
```  
  
 <span data-ttu-id="b4816-128">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b4816-128">This example produces the following output:</span></span>  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="b4816-129">Prázdný textový uzel ovlivňuje serializaci.</span><span class="sxs-lookup"><span data-stu-id="b4816-129">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="b4816-130">Pokud element obsahuje pouze podřízený textový uzel, který je prázdný, je serializován pomocí syntaxe dlouhých značek: `<Child></Child>` .</span><span class="sxs-lookup"><span data-stu-id="b4816-130">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="b4816-131">Pokud element neobsahuje žádné podřízené uzly, je serializován s syntaxí krátké značky: `<Child />` .</span><span class="sxs-lookup"><span data-stu-id="b4816-131">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);
```  
  
 <span data-ttu-id="b4816-132">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b4816-132">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="b4816-133">Obory názvů jsou atributy ve stromu LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="b4816-133">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="b4816-134">I když deklarace oboru názvů mají identickou syntaxi atributů, v některých programovacích rozhraních, jako jsou XSLT a XPath, deklarace oborů názvů nejsou považovány za atributy.</span><span class="sxs-lookup"><span data-stu-id="b4816-134">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="b4816-135">V rozhraní se však [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obory názvů ukládají jako <xref:System.Xml.Linq.XAttribute> objekty ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="b4816-135">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="b4816-136">Pokud iterete pomocí atributů pro prvek, který obsahuje deklaraci oboru názvů, uvidíte deklaraci oboru názvů jako jednu z položek ve vrácené kolekci.</span><span class="sxs-lookup"><span data-stu-id="b4816-136">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="b4816-137"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A>Vlastnost označuje, zda je atribut deklarací oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b4816-137">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="b4816-138">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b4816-138">This example produces the following output:</span></span>  
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="b4816-139">Metody osy XPath nevracejí podřízené prázdné znaky XDocument</span><span class="sxs-lookup"><span data-stu-id="b4816-139">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b4816-140">umožňuje podřízených textových uzlů v <xref:System.Xml.Linq.XDocument> , pokud textové uzly obsahují pouze prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="b4816-140">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="b4816-141">Model objektu XPath ale neobsahuje prázdné znaky jako podřízené uzly dokumentu, takže při iteraci mezi podřízenými prvky <xref:System.Xml.Linq.XDocument> pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> osy se vrátí textové uzly bílého prostoru.</span><span class="sxs-lookup"><span data-stu-id="b4816-141">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white-space text nodes will be returned.</span></span> <span data-ttu-id="b4816-142">Při iteraci mezi podřízenými objekty <xref:System.Xml.Linq.XDocument> pomocí metod osy XPath ale prázdné textové uzly nebudou vráceny.</span><span class="sxs-lookup"><span data-stu-id="b4816-142">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white-space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="b4816-143">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b4816-143">This example produces the following output:</span></span>  
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="b4816-144">Objekty XDeclaration nejsou uzly.</span><span class="sxs-lookup"><span data-stu-id="b4816-144">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="b4816-145">Při iteraci mezi podřízenými uzly objektu <xref:System.Xml.Linq.XDocument> , se nezobrazí objekt deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="b4816-145">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="b4816-146">Jedná se o vlastnost dokumentu, nikoli o podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="b4816-146">It is a property of the document, not a child node of it.</span></span>  
  
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
  
 <span data-ttu-id="b4816-147">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b4816-147">This example produces the following output:</span></span>  
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  