---
title: Programování s uzly
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 9c64c348f5d26172f26593b927e6bc24baf365bf
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794400"
---
# <a name="programming-with-nodes-visual-basic"></a><span data-ttu-id="c53d1-102">Programování s uzly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c53d1-102">Programming with Nodes (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c53d1-103">Vývojáři, kteří potřebují psát programy, jako je editor XML, transformační systém nebo zapisovač sestav, často potřebují psát programy, které fungují na jemnější úrovni členitosti než prvky a atributy.</span><span class="sxs-lookup"><span data-stu-id="c53d1-103">developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="c53d1-104">Často potřebují pracovat na úrovni uzlu, manipulaci s textovými uzly, pokyny pro zpracování a komentáře.</span><span class="sxs-lookup"><span data-stu-id="c53d1-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="c53d1-105">Toto téma poskytuje některé podrobnosti o programování na úrovni uzlu.</span><span class="sxs-lookup"><span data-stu-id="c53d1-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="c53d1-106">Podrobnosti uzlu</span><span class="sxs-lookup"><span data-stu-id="c53d1-106">Node Details</span></span>  
 <span data-ttu-id="c53d1-107">Existuje řada podrobných informací o programování, které by programátor pracující na úrovni uzlu měl znát.</span><span class="sxs-lookup"><span data-stu-id="c53d1-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="c53d1-108">Vlastnost Parent podřízených uzlů XDocument je nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c53d1-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="c53d1-109"><xref:System.Xml.Linq.XObject.Parent%2A> Vlastnost obsahuje nadřazenou položku <xref:System.Xml.Linq.XElement>, ne nadřazený uzel.</span><span class="sxs-lookup"><span data-stu-id="c53d1-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="c53d1-110">Podřízené uzly <xref:System.Xml.Linq.XDocument> nemají žádnou nadřazenou <xref:System.Xml.Linq.XElement>položku.</span><span class="sxs-lookup"><span data-stu-id="c53d1-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="c53d1-111">Jejich nadřazeným prvkem je dokument, takže <xref:System.Xml.Linq.XObject.Parent%2A> vlastnost pro tyto uzly je nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c53d1-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="c53d1-112">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="c53d1-112">The following example demonstrates this:</span></span>  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 <span data-ttu-id="c53d1-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c53d1-113">This example produces the following output:</span></span>  
  
```console  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="c53d1-114">Jsou možné sousední uzly textu.</span><span class="sxs-lookup"><span data-stu-id="c53d1-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="c53d1-115">V řadě programovacích modelů XML jsou sousední textové uzly vždycky sloučeny.</span><span class="sxs-lookup"><span data-stu-id="c53d1-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="c53d1-116">To se někdy označuje jako normalizace textových uzlů.</span><span class="sxs-lookup"><span data-stu-id="c53d1-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c53d1-117">nenormalizuje textové uzly.</span><span class="sxs-lookup"><span data-stu-id="c53d1-117">does not normalize text nodes.</span></span> <span data-ttu-id="c53d1-118">Pokud přidáte dva textové uzly do stejného elementu, bude výsledkem sousedících textových uzlů.</span><span class="sxs-lookup"><span data-stu-id="c53d1-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="c53d1-119">Pokud však přidáte obsah zadaný jako řetězec, nikoli jako <xref:System.Xml.Linq.XText> uzel, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] může řetězec sloučit s sousedícím textovým uzlem.</span><span class="sxs-lookup"><span data-stu-id="c53d1-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="c53d1-120">Následující příklad ukazuje toto:</span><span class="sxs-lookup"><span data-stu-id="c53d1-120">The following example demonstrates this:</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
' This does not add a new text node.  
xmlTree.Add("new content")  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
'// This does add a new, adjacent text node.  
xmlTree.Add(New XText("more text"))  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
```  
  
 <span data-ttu-id="c53d1-121">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c53d1-121">This example produces the following output:</span></span>  
  
```console  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="c53d1-122">Jsou možné prázdné textové uzly.</span><span class="sxs-lookup"><span data-stu-id="c53d1-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="c53d1-123">V některých programovacích modelech XML je zaručeno, že textové uzly nebudou obsahovat prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c53d1-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="c53d1-124">Důvodem je, že takový textový uzel nemá žádný vliv na serializaci kódu XML.</span><span class="sxs-lookup"><span data-stu-id="c53d1-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="c53d1-125">Z toho důvodu, že když odeberete text z textového uzlu nastavením jeho hodnoty na prázdný řetězec, samotný textový uzel nebude odstraněn, ze stejného důvodu, že je možné použít sousední textové uzly.</span><span class="sxs-lookup"><span data-stu-id="c53d1-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 <span data-ttu-id="c53d1-126">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c53d1-126">This example produces the following output:</span></span>  
  
```console  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="c53d1-127">Prázdný textový uzel ovlivňuje serializaci.</span><span class="sxs-lookup"><span data-stu-id="c53d1-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="c53d1-128">Pokud element obsahuje pouze podřízený textový uzel, který je prázdný, je serializován pomocí syntaxe dlouhých značek: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="c53d1-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="c53d1-129">Pokud element neobsahuje žádné podřízené uzly, je serializován s syntaxí krátké značky: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="c53d1-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 <span data-ttu-id="c53d1-130">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c53d1-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="c53d1-131">Obory názvů jsou atributy ve stromu LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="c53d1-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="c53d1-132">I když deklarace oboru názvů mají identickou syntaxi atributů, v některých programovacích rozhraních, jako jsou XSLT a XPath, deklarace oborů názvů nejsou považovány za atributy.</span><span class="sxs-lookup"><span data-stu-id="c53d1-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="c53d1-133">V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]rozhraní se však obory názvů ukládají <xref:System.Xml.Linq.XAttribute> jako objekty ve stromu XML.</span><span class="sxs-lookup"><span data-stu-id="c53d1-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="c53d1-134">Pokud iterete pomocí atributů pro prvek, který obsahuje deklaraci oboru názvů, uvidíte deklaraci oboru názvů jako jednu z položek ve vrácené kolekci.</span><span class="sxs-lookup"><span data-stu-id="c53d1-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="c53d1-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Vlastnost označuje, zda je atribut deklarací oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c53d1-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```vb  
Dim root As XElement = _
<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>  
For Each att As XAttribute In root.Attributes()  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, _  
                      att.IsNamespaceDeclaration)  
Next  
```  
  
 <span data-ttu-id="c53d1-136">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c53d1-136">This example produces the following output:</span></span>  
  
```console  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="c53d1-137">Metody osy XPath nevracejí podřízené prázdné znaky XDocument</span><span class="sxs-lookup"><span data-stu-id="c53d1-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c53d1-138">umožňuje podřízených textových uzlů v <xref:System.Xml.Linq.XDocument>, pokud textové uzly obsahují pouze prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="c53d1-138">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="c53d1-139">Model objektu XPath ale neobsahuje prázdné znaky jako podřízené uzly dokumentu, takže při iteraci mezi podřízenými prvky <xref:System.Xml.Linq.XDocument> pomocí <xref:System.Xml.Linq.XContainer.Nodes%2A> osy se vrátí textové uzly s prázdným znakem.</span><span class="sxs-lookup"><span data-stu-id="c53d1-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="c53d1-140">Při iteraci po podřízených objektech <xref:System.Xml.Linq.XDocument> pomocí metod osy XPath však nebudou textové uzly prázdné místo vráceny.</span><span class="sxs-lookup"><span data-stu-id="c53d1-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes will not be returned.</span></span>  
  
```vb  
' Create a document with some white space child nodes of the document.  
Dim root As XDocument = XDocument.Parse( _  
"<?xml version='1.0' encoding='utf-8' standalone='yes'?>" & _  
vbNewLine & "<Root/>" & vbNewLine & "<!--a comment-->" & vbNewLine, _  
LoadOptions.PreserveWhitespace)  
  
' Count the white space child nodes using LINQ to XML.  
Console.WriteLine(root.Nodes().OfType(Of XText)().Count())  
  
' Count the white space child nodes using XPathEvaluate.  
Dim nodes As IEnumerable = CType(root.XPathEvaluate("text()"), IEnumerable)  
Console.WriteLine(nodes.OfType(Of XText)().Count())  
```  
  
 <span data-ttu-id="c53d1-141">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c53d1-141">This example produces the following output:</span></span>  
  
```console  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="c53d1-142">Objekty XDeclaration nejsou uzly.</span><span class="sxs-lookup"><span data-stu-id="c53d1-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="c53d1-143">Při iteraci mezi podřízenými uzly objektu <xref:System.Xml.Linq.XDocument>, se nezobrazí objekt deklarace XML.</span><span class="sxs-lookup"><span data-stu-id="c53d1-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="c53d1-144">Jedná se o vlastnost dokumentu, nikoli o podřízený uzel.</span><span class="sxs-lookup"><span data-stu-id="c53d1-144">It is a property of the document, not a child node of it.</span></span>  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 <span data-ttu-id="c53d1-145">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c53d1-145">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />
1
```  
  
## <a name="see-also"></a><span data-ttu-id="c53d1-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="c53d1-146">See also</span></span>

- [<span data-ttu-id="c53d1-147">Rozšířené programování LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c53d1-147">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
