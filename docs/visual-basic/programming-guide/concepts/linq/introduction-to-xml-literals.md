---
title: "Úvod do literálů XML v Visual Basic2"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7ac96691b5b9274f67039f36bbdbfaf8abd03705
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="f4486-102">Úvod do literálů XML v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4486-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="f4486-103">Tato část obsahuje informace o vytváření stromů XML v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4486-103">This section provides information about creating XML trees in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="f4486-104">Informace o použití výsledky dotazů LINQ jako obsah pro strom XML najdete v tématu [funkční konstrukce (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f4486-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="f4486-105">Další informace o literálech XML v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], najdete v části [Přehled technologie LINQ to XML v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f4486-105">For more information on XML literals in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], see [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="f4486-106">Vytváření stromů XML</span><span class="sxs-lookup"><span data-stu-id="f4486-106">Creating XML Trees</span></span>  
 <span data-ttu-id="f4486-107">Následující příklad ukazuje, jak vytvořit <xref:System.Xml.Linq.XElement>, v takovém případě `contacts`:</span><span class="sxs-lookup"><span data-stu-id="f4486-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="f4486-108">Vytvoření XElement s jednoduchým obsahem</span><span class="sxs-lookup"><span data-stu-id="f4486-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="f4486-109">Můžete vytvořit <xref:System.Xml.Linq.XElement> obsahující jednoduchým obsahem, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f4486-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 <span data-ttu-id="f4486-110">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f4486-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="f4486-111">Vytvoření prázdného prvku</span><span class="sxs-lookup"><span data-stu-id="f4486-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="f4486-112">Můžete vytvořit prázdnou <xref:System.Xml.Linq.XElement>, a to takto:</span><span class="sxs-lookup"><span data-stu-id="f4486-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="f4486-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f4486-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="f4486-114">Pomocí vložené výrazy</span><span class="sxs-lookup"><span data-stu-id="f4486-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="f4486-115">Důležitou součást literálů XML je, že umožňují vložené výrazy.</span><span class="sxs-lookup"><span data-stu-id="f4486-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="f4486-116">Vložené výrazy umožňují vyhodnocení výrazu a vložit výsledky výraz do stromu XML.</span><span class="sxs-lookup"><span data-stu-id="f4486-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="f4486-117">Pokud je výsledkem typu <xref:System.Xml.Linq.XElement>, element budou vložena do stromu.</span><span class="sxs-lookup"><span data-stu-id="f4486-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="f4486-118">Pokud je výsledkem typu <xref:System.Xml.Linq.XAttribute>, atribut se vloží do stromu.</span><span class="sxs-lookup"><span data-stu-id="f4486-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="f4486-119">Elementy a atributy můžete vložit do stromu jenom tam, kde jsou platné.</span><span class="sxs-lookup"><span data-stu-id="f4486-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="f4486-120">Je důležité si uvědomit, že pouze jeden výraz můžete přejít do embedded výrazu.</span><span class="sxs-lookup"><span data-stu-id="f4486-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="f4486-121">Nelze vložit více příkazů.</span><span class="sxs-lookup"><span data-stu-id="f4486-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="f4486-122">Pokud výraz přesahuje jeden řádek, je nutné použít znak pokračování řádku.</span><span class="sxs-lookup"><span data-stu-id="f4486-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="f4486-123">Používáte-li přidat existující uzly (včetně elementů) a atributy, které mají novou větev XML a pokud jsou na uzlech existujícího již nadřazena embedded výrazu, můžete se klonují uzly.</span><span class="sxs-lookup"><span data-stu-id="f4486-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="f4486-124">Nově naklonovaný uzly jsou připojené k nové stromu XML.</span><span class="sxs-lookup"><span data-stu-id="f4486-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="f4486-125">Pokud nejsou na uzlech existujícího nadřazena, uzly jsou jednoduše připojit ke stromu nové XML.</span><span class="sxs-lookup"><span data-stu-id="f4486-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="f4486-126">Poslední příklad v tomto tématu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="f4486-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="f4486-127">Následující příklad používá výraz embedded vložení prvku do stromu:</span><span class="sxs-lookup"><span data-stu-id="f4486-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
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
  
 <span data-ttu-id="f4486-128">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f4486-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="f4486-129">Pomocí vložené výrazy pro obsah</span><span class="sxs-lookup"><span data-stu-id="f4486-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="f4486-130">Výraz embedded můžete použít k poskytování obsahu elementu:</span><span class="sxs-lookup"><span data-stu-id="f4486-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="f4486-131">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f4486-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="f4486-132">Použití v Embedded výrazu dotazu LINQ</span><span class="sxs-lookup"><span data-stu-id="f4486-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="f4486-133">Výsledky dotazu LINQ můžete použít pro obsah elementu:</span><span class="sxs-lookup"><span data-stu-id="f4486-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="f4486-134">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f4486-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="f4486-135">Použití vložené výrazy pro názvy</span><span class="sxs-lookup"><span data-stu-id="f4486-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="f4486-136">Vložené výrazy můžete také použít k výpočtu názvy atributů, hodnoty atributu, elementu názvy a hodnoty element:</span><span class="sxs-lookup"><span data-stu-id="f4486-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
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
  
 <span data-ttu-id="f4486-137">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f4486-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="f4486-138">Klonování vs. Připojení</span><span class="sxs-lookup"><span data-stu-id="f4486-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="f4486-139">Jak je uvedeno výše, pokud používáte embedded výrazu přidejte existující uzly (včetně elementů) a atributy novou větev XML, pokud jsou na uzlech existujícího již nadřazena, uzly jsou klonovat a nově naklonovaný uzly jsou připojené k nové stromu XML.</span><span class="sxs-lookup"><span data-stu-id="f4486-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="f4486-140">Pokud nejsou na uzlech existujícího nadřazena, jsou jednoduše připojené k nové stromu XML.</span><span class="sxs-lookup"><span data-stu-id="f4486-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
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
  
 <span data-ttu-id="f4486-141">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f4486-141">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4486-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4486-142">See Also</span></span>  
 [<span data-ttu-id="f4486-143">Vytváření stromů XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4486-143">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
