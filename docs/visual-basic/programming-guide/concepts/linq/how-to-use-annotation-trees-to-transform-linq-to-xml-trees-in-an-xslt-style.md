---
title: "Postupy: použití poznámek k transformaci technologie LINQ to XML stromy v XSLT stylu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e2e5fce154d5d59657302deb2ce0be80a3bc3ac6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a><span data-ttu-id="ced89-102">Postupy: použití poznámek k transformaci technologie LINQ to XML stromy v XSLT stylu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ced89-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)</span></span>
<span data-ttu-id="ced89-103">Poznámky lze použít pro usnadnění transformací stromu XML.</span><span class="sxs-lookup"><span data-stu-id="ced89-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="ced89-104">Některé dokumentů XML jsou "dokumentu zaměřená na se smíšeným obsahem."</span><span class="sxs-lookup"><span data-stu-id="ced89-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="ced89-105">S takové dokumenty nevíte nutně obrazec podřízené uzly elementu.</span><span class="sxs-lookup"><span data-stu-id="ced89-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="ced89-106">Uzel, který obsahuje text může například vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="ced89-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="ced89-107">Pro jakékoli dané textový uzel, může být libovolný počet podřízených `<b>` a `<i>` elementy.</span><span class="sxs-lookup"><span data-stu-id="ced89-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="ced89-108">Tento přístup rozšiřuje na počet jiných situacích: například stránek, které může obsahovat celou řadu podřízených elementů, například regulární odstavců, odstavců s odrážkami a rastrové obrázky.</span><span class="sxs-lookup"><span data-stu-id="ced89-108">This approach extends to a number of other situations: such as, pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="ced89-109">Buněk v tabulce může obsahovat text, rozevírací seznamy nebo rastrové obrázky.</span><span class="sxs-lookup"><span data-stu-id="ced89-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="ced89-110">Jednou z primární vlastností dokumentu, který je zaměřená na XML neznáte které podřízený element, který bude mít žádné konkrétní elementu.</span><span class="sxs-lookup"><span data-stu-id="ced89-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="ced89-111">Pokud chcete k transformaci elementy ve stromu, kde si nejste jisti nutně mnohem o podřízených prvků, které chcete k transformaci, je tento přístup, který používá poznámky účinnou metodou.</span><span class="sxs-lookup"><span data-stu-id="ced89-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="ced89-112">Souhrn tohoto přístupu je:</span><span class="sxs-lookup"><span data-stu-id="ced89-112">The summary of the approach is:</span></span>  
  
-   <span data-ttu-id="ced89-113">Nejprve opatřit poznámkami elementy ve stromové struktuře s elementem nahrazení.</span><span class="sxs-lookup"><span data-stu-id="ced89-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
-   <span data-ttu-id="ced89-114">Za druhé iterate celý strom, vytvoření nového stromu kde nahraďte každý prvek s jeho poznámky.</span><span class="sxs-lookup"><span data-stu-id="ced89-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="ced89-115">Tento příklad implementuje iterace a vytvoření nového stromu ve funkci s názvem `XForm`.</span><span class="sxs-lookup"><span data-stu-id="ced89-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="ced89-116">Podrobně přístup se skládá z:</span><span class="sxs-lookup"><span data-stu-id="ced89-116">In detail, the approach consists of:</span></span>  
  
-   <span data-ttu-id="ced89-117">Spusťte jeden nebo více technologie LINQ to XML dotazů, které vrátí sadu elementů, které chcete z jedné tvaru transformace do jiného.</span><span class="sxs-lookup"><span data-stu-id="ced89-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="ced89-118">Pro každý prvek v dotazu, přidejte nový <xref:System.Xml.Linq.XElement> objektu jako anotaci pro element.</span><span class="sxs-lookup"><span data-stu-id="ced89-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="ced89-119">Tento nový element nahradí element s poznámkami ve stromové struktuře nové, transformovaných.</span><span class="sxs-lookup"><span data-stu-id="ced89-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="ced89-120">Toto je jednoduchý kód pro zápis, jak je ukázáno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="ced89-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
-   <span data-ttu-id="ced89-121">Nového elementu, který je přidán jako poznámky mohou obsahovat nové podřízené uzly; mohl vytvořit podstromu u libovolného požadovaného tvaru.</span><span class="sxs-lookup"><span data-stu-id="ced89-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
-   <span data-ttu-id="ced89-122">Je zvláštní pravidlo: Pokud je podřízený uzel nového elementu v jiný obor názvů, obor názvů, který se skládá pro tento účel (v tomto příkladu je obor názvů `http://www.microsoft.com/LinqToXmlTransform/2007`), pak tento podřízený element není zkopírovány do nového stromu.</span><span class="sxs-lookup"><span data-stu-id="ced89-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="ced89-123">Místo toho, pokud je obor názvů výše uvedené speciální obor názvů a místní název elementu je `ApplyTransforms`, pak uzly podřízené elementu ve stromové struktuře zdroje jsou vstupní a zkopírován do stromu nové (s výjimkou, který podřízené prvky jsou poznámky. sami podle tato pravidla Transformovat).</span><span class="sxs-lookup"><span data-stu-id="ced89-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
-   <span data-ttu-id="ced89-124">Toto je obdobou specifikaci transformací v XSL.</span><span class="sxs-lookup"><span data-stu-id="ced89-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="ced89-125">Dotaz, který vybere sada uzlů je obdobou výraz XPath pro šablonu.</span><span class="sxs-lookup"><span data-stu-id="ced89-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="ced89-126">Kód k vytvoření nové <xref:System.Xml.Linq.XElement> , je uložit jako je podobná konstruktor pořadí v XSL, poznámky a `ApplyTransforms` elementu je v funkce, která se podobá `xsl:apply-templates` element v XSL.</span><span class="sxs-lookup"><span data-stu-id="ced89-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
-   <span data-ttu-id="ced89-127">Jedna z výhod trvá tento přístup – jako jste formulovali dotazy, jsou vždy zápis dotazů ve stromové struktuře beze změny zdroje.</span><span class="sxs-lookup"><span data-stu-id="ced89-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="ced89-128">Nemusí starosti vliv dotazy, které jsou zápisu změn do stromu.</span><span class="sxs-lookup"><span data-stu-id="ced89-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="ced89-129">Transformace stromu</span><span class="sxs-lookup"><span data-stu-id="ced89-129">Transforming a Tree</span></span>  
 <span data-ttu-id="ced89-130">Tento příklad první přejmenuje všechny `Paragraph` uzly do `para`.</span><span class="sxs-lookup"><span data-stu-id="ced89-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
```vb  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>  
                <Paragraph>More text.</Paragraph>  
            </Root>  
  
        ' Replace Paragraph with p.  
        For Each el In root...<Paragraph>  
            ' same idea as xsl:apply-templates  
            el.AddAnnotation( _  
                <para>  
                    <<%= at %>></>  
                </para>)  
        Next  
  
        ' The XForm function, shown later in this topic, accomplishes the transform  
        Dim newRoot As XElement = XForm(root)  
        Console.WriteLine(newRoot)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ced89-131">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ced89-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="ced89-132">Složitější transformace</span><span class="sxs-lookup"><span data-stu-id="ced89-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="ced89-133">Následující příklad dotazuje stromu a vypočítá průměr a součet `Data` prvky a přidá je do stromu jako nové prvky.</span><span class="sxs-lookup"><span data-stu-id="ced89-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
```vb  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    Sub Main()  
        Dim data As XElement = _  
            <Root>  
                <Data>20</Data>  
                <Data>10</Data>  
                <Data>3</Data>  
            </Root>  
  
        ' While adding annotations, you can query the source tree all you want,  
        ' as the tree is not mutated while annotating.  
        data.AddAnnotation( _  
            <Root>  
                <<%= at %>/>  
                <Average>  
                    <%= _  
                        String.Format("{0:F4}", _  
                        data.Elements("Data") _  
                        .Select(Function(z) CDec(z)).Average()) _  
                    %>  
                </Average>  
                <Sum>  
                    <%= _  
                        data.Elements("Data").Select(Function(z) CInt(z)).Sum() _  
                    %>  
                </Sum>  
            </Root> _  
        )  
  
        Console.WriteLine("Before Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(data)  
        Console.WriteLine(vbNewLine)  
  
        ' The XForm function, shown later in this topic, accomplishes the transform  
        Dim newData As XElement = XForm(data)  
  
        Console.WriteLine("After Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(newData)  
    End Sub  
End Module   
```  
  
 <span data-ttu-id="ced89-134">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ced89-134">This example produces the following output:</span></span>  
  
```  
Before Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
</Root>  
  
After Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
  <Average>11.0000</Average>  
  <Sum>33</Sum>  
</Root>  
```  
  
## <a name="effecting-the-transform"></a><span data-ttu-id="ced89-135">Účinků pro transformaci</span><span class="sxs-lookup"><span data-stu-id="ced89-135">Effecting the Transform</span></span>  
 <span data-ttu-id="ced89-136">Malé funkce, `XForm`, vytvoří novou větev transformovaných ze stromu původní, s poznámkami.</span><span class="sxs-lookup"><span data-stu-id="ced89-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
-   <span data-ttu-id="ced89-137">Kód pseudo pro funkci je poměrně jednoduché:</span><span class="sxs-lookup"><span data-stu-id="ced89-137">The pseudo code for the function is quite simple:</span></span>  
  
```  
The function takes an XElement as an argument and returns an XElement.   
If an element has an XElement annotation, then  
    Return a new XElement  
        The name of the new XElement is the annotation element's name.  
        All attributes are copied from the annotation to the new node.  
        All child nodes are copied from the annotation, with the  
            exception that the special node xf:ApplyTransforms is  
            recognized, and the source element's child nodes are  
            iterated. If the source child node is not an XElement, it  
            is copied to the new tree. If the source child is an  
            XElement, then it is transformed by calling this function  
            recursively.  
If an element is not annotated  
    Return a new XElement  
        The name of the new XElement is the source element's name  
        All attributes are copied from the source element to the  
            destination's element.  
        All child nodes are copied from the source element.  
        If the source child node is not an XElement, it is copied to  
            the new tree. If the source child is an XElement, then it  
            is transformed by calling this function recursively.  
```  
  
 <span data-ttu-id="ced89-138">Toto je implementací této funkce:</span><span class="sxs-lookup"><span data-stu-id="ced89-138">Following is the implementation of this function:</span></span>  
  
```vb  
' Build a transformed XML tree per the annotations.  
Function XForm(ByVal source As XElement) As XElement  
    If source.Annotation(Of XElement)() IsNot Nothing Then  
        Dim anno As XElement = source.Annotation(Of XElement)()  
        Return _  
            <<%= anno.Name.ToString() %>>  
                <%= anno.Attributes() %>  
                <%= anno.Nodes().Select(Function(n As XNode) _  
                    GetSubNodes(n, source)) %>  
            </>  
    Else  
        Return _  
            <<%= source.Name %>>  
                <%= source.Attributes() %>  
                <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>  
            </>  
    End If  
End Function  
  
Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object  
    Dim annoEl As XElement = TryCast(n, XElement)  
    If annoEl IsNot Nothing Then  
        If annoEl.Name = at Then  
            Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))  
        End If  
    End If  
    Return n  
End Function  
  
Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode  
    Dim e2 As XElement = TryCast(n2, XElement)  
    If e2 Is Nothing Then  
        Return n2  
    Else  
        Return XForm(e2)  
    End If  
End Function  
```  
  
## <a name="complete-example"></a><span data-ttu-id="ced89-139">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="ced89-139">Complete Example</span></span>  
 <span data-ttu-id="ced89-140">Následující kód je kompletní příklad, který obsahuje `XForm` funkce.</span><span class="sxs-lookup"><span data-stu-id="ced89-140">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="ced89-141">Obsahuje několik typické použití tohoto typu transformace:</span><span class="sxs-lookup"><span data-stu-id="ced89-141">It includes a few of the typical uses of this type of transform:</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Linq  
Imports System.Text  
Imports System.Xml  
Imports System.Xml.Linq  
  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    ' Build a transformed XML tree per the annotations.  
    Function XForm(ByVal source As XElement) As XElement  
        If source.Annotation(Of XElement)() IsNot Nothing Then  
            Dim anno As XElement = source.Annotation(Of XElement)()  
            Return _  
                <<%= anno.Name.ToString() %>>  
                    <%= anno.Attributes() %>  
                    <%= anno.Nodes().Select(Function(n As XNode) _  
                        GetSubNodes(n, source)) %>  
                </>  
        Else  
            Return _  
                <<%= source.Name %>>  
                    <%= source.Attributes() %>  
                    <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>  
                </>  
        End If  
    End Function  
  
    Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object  
        Dim annoEl As XElement = TryCast(n, XElement)  
        If annoEl IsNot Nothing Then  
            If annoEl.Name = at Then  
                Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))  
            End If  
        End If  
        Return n  
    End Function  
  
    Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode  
        Dim e2 As XElement = TryCast(n2, XElement)  
        If e2 Is Nothing Then  
            Return n2  
        Else  
            Return XForm(e2)  
        End If  
    End Function  
  
    Sub Main()  
        Dim root As XElement = _  
<Root Att1='123'>  
    <!--A comment-->  
    <Child>1</Child>  
    <Child>2</Child>  
    <Other>  
        <GC>3</GC>  
        <GC>4</GC>  
    </Other>  
    <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>  
    <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
  
        ' Each of the following serves the same semantic purpose as  
        ' XSLT templates and sequence constructors.  
  
        ' Replace Child with NewChild.  
        For Each el In root.<Child>  
            el.AddAnnotation(<NewChild><%= CStr(el) %></NewChild>)  
        Next  
  
        ' Replace first GC with GrandChild, add an attribute.  
        For Each el In root...<GC>.Take(1)  
            el.AddAnnotation(<GrandChild ANewAttribute='999'><%= CStr(el) %></GrandChild>)  
        Next  
  
        ' Replace Other with NewOther, add new child elements around original content.  
        For Each el In root.<Other>  
            el.AddAnnotation( _  
                <NewOther>  
                    <MyNewChild>1</MyNewChild>  
                    <<%= at %>></>  
                    <ChildThatComesAfter/>  
                </NewOther>)  
        Next  
  
        ' Change name of element that has mixed content.  
        root...<SomeMixedContent>(0).AddAnnotation( _  
                <MixedContent><<%= at %>></></MixedContent>)  
  
        ' Replace <b> with <Bold>.  
        For Each el In root...<b>  
            el.AddAnnotation(<Bold><<%= at %>></></Bold>)  
        Next  
  
        ' Replace <i> with <Italic>.  
        For Each el In root...<i>  
            el.AddAnnotation(<Italic><<%= at %>></></Italic>)  
        Next  
  
        Console.WriteLine("Before Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(root)  
        Console.WriteLine(vbNewLine)  
        Dim newRoot As XElement = XForm(root)  
  
        Console.WriteLine("After Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(newRoot)  
    End Sub  
End Module   
```  
  
 <span data-ttu-id="ced89-142">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ced89-142">This example produces the following output:</span></span>  
  
```  
Before Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <Child>1</Child>  
  <Child>2</Child>  
  <Other>  
    <GC>3</GC>  
    <GC>4</GC>  
  </Other>  
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
  
After Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <NewChild>1</NewChild>  
  <NewChild>2</NewChild>  
  <NewOther>  
    <MyNewChild>1</MyNewChild>  
    <GrandChild ANewAttribute="999">3</GrandChild>  
    <GC>4</GC>  
    <ChildThatComesAfter />  
  </NewOther>  
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ced89-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="ced89-143">See Also</span></span>  
 [<span data-ttu-id="ced89-144">Pokročilé technologie LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ced89-144">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
