---
title: Úvod k Literálům XML v Visual Basic2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 68ba1e018d4ad9501532745a88090f0f756b5c17
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841278"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="70074-102">Úvod k Literálům XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70074-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="70074-103">Tato část obsahuje informace o vytváření stromů XML v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="70074-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="70074-104">Informace o použití výsledků dotazů LINQ jako obsah pro stromu XML, naleznete v tématu [funkční konstrukce (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="70074-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="70074-105">Další informace o literálech XML v jazyce Visual Basic najdete v tématu [Přehled technologie LINQ to XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="70074-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="70074-106">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="70074-106">Creating XML Trees</span></span>  
 <span data-ttu-id="70074-107">Následující příklad ukazuje, jak vytvořit <xref:System.Xml.Linq.XElement>, v tomto případě `contacts`:</span><span class="sxs-lookup"><span data-stu-id="70074-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="70074-108">Vytváření s jednoduchým obsahem na XElement</span><span class="sxs-lookup"><span data-stu-id="70074-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="70074-109">Můžete vytvořit <xref:System.Xml.Linq.XElement> , který obsahuje jednoduchý obsah následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="70074-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 <span data-ttu-id="70074-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="70074-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="70074-111">Vytvořit prázdný Element</span><span class="sxs-lookup"><span data-stu-id="70074-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="70074-112">Můžete vytvořit prázdnou <xref:System.Xml.Linq.XElement>, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="70074-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="70074-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="70074-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="70074-114">Použitím vložené výrazy</span><span class="sxs-lookup"><span data-stu-id="70074-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="70074-115">Důležité funkce literálů XML je, že umožňují vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="70074-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="70074-116">Vložené výrazy umožňují vyhodnocení výrazu a vložení výsledků výrazu do stromu XML.</span><span class="sxs-lookup"><span data-stu-id="70074-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="70074-117">Pokud je výraz vyhodnocen jako typ <xref:System.Xml.Linq.XElement>, element je vložen do stromu.</span><span class="sxs-lookup"><span data-stu-id="70074-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="70074-118">Pokud je výraz vyhodnocen jako typ <xref:System.Xml.Linq.XAttribute>, atribut je vložen do stromu.</span><span class="sxs-lookup"><span data-stu-id="70074-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="70074-119">Elementy a atributy můžete vložit do stromu, pouze pokud jsou platné.</span><span class="sxs-lookup"><span data-stu-id="70074-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="70074-120">Je důležité si uvědomit, že pouze jeden výraz můžete přejít do vloženého výrazu.</span><span class="sxs-lookup"><span data-stu-id="70074-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="70074-121">Nelze vložit více příkazů.</span><span class="sxs-lookup"><span data-stu-id="70074-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="70074-122">Pokud výraz se rozpíná za jeden řádek, je nutné použít znak pro pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="70074-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="70074-123">Pokud používáte vložený výraz přidejte existující uzly (včetně prvky) a atributy do nového stromu XML a pokud existující uzly jsou již opatřen podřízeným prvkem, se klonují uzly.</span><span class="sxs-lookup"><span data-stu-id="70074-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="70074-124">Nově naklonované uzly jsou připojené do nového stromu XML.</span><span class="sxs-lookup"><span data-stu-id="70074-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="70074-125">Pokud nejsou nadřazena stávající uzly, uzly připojeny jednoduše do nového stromu XML.</span><span class="sxs-lookup"><span data-stu-id="70074-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="70074-126">V poslední příkladu v tomto tématu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="70074-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="70074-127">Následující příklad používá vložený výraz k vkládání elementů do stromové struktury:</span><span class="sxs-lookup"><span data-stu-id="70074-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 <span data-ttu-id="70074-128">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="70074-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="70074-129">Použitím vložené výrazy pro obsah</span><span class="sxs-lookup"><span data-stu-id="70074-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="70074-130">Slouží k poskytování obsahu elementu, můžete použít vložený výraz:</span><span class="sxs-lookup"><span data-stu-id="70074-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="70074-131">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="70074-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="70074-132">Pomocí dotazu LINQ v vložený výraz</span><span class="sxs-lookup"><span data-stu-id="70074-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="70074-133">Výsledky dotazu LINQ slouží pro obsah elementu:</span><span class="sxs-lookup"><span data-stu-id="70074-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="70074-134">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="70074-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="70074-135">Použitím vložené výrazy pro názvy Wwnn</span><span class="sxs-lookup"><span data-stu-id="70074-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="70074-136">Vložené výrazy můžete použít také k výpočtu názvy atributů, hodnoty atributů, názvy prvků a hodnoty prvků:</span><span class="sxs-lookup"><span data-stu-id="70074-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="70074-137">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="70074-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="70074-138">Klonování versus připojení</span><span class="sxs-lookup"><span data-stu-id="70074-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="70074-139">Jak bylo zmíněno dříve, pokud používáte vložený výraz přidat existující uzly (včetně prvky) a atributy do nového stromu XML, pokud již má nadřazenou existujících uzlů, se klonují uzly a nově naklonované uzly jsou připojené do nového stromu XML.</span><span class="sxs-lookup"><span data-stu-id="70074-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="70074-140">Pokud nejsou nadřazena stávající uzly, jsou jednoduše připojené do nového stromu XML.</span><span class="sxs-lookup"><span data-stu-id="70074-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="70074-141">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="70074-141">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="70074-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70074-142">See also</span></span>

- [<span data-ttu-id="70074-143">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70074-143">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
