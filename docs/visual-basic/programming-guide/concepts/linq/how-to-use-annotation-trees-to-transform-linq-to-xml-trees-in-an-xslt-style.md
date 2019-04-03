---
title: 'Postupy: Použití anotací transformace stromů LINQ to XML ve stylu XSLT (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: a8db5f9dc29b4053321c81c9da58e12610ef63c7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824868"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a><span data-ttu-id="1a0c9-102">Postupy: Použití anotací transformace stromů LINQ to XML ve stylu XSLT (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a0c9-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)</span></span>
<span data-ttu-id="1a0c9-103">Poznámky lze použít k usnadnění transformace stromu XML.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="1a0c9-104">Některé dokumenty XML jsou "dokumentu se smíšeným obsahem na střed."</span><span class="sxs-lookup"><span data-stu-id="1a0c9-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="1a0c9-105">Pomocí těchto dokumentů neznáte nutně tvar podřízené uzly element.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="1a0c9-106">Uzel, který obsahuje text může například vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="1a0c9-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="1a0c9-107">Pro libovolný uzel daný text může být libovolný počet podřízených `<b>` a `<i>` elementy.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="1a0c9-108">Tento přístup se rozšiřuje na celou řadou dalších situacích: například stránky, které může obsahovat různé podřízené prvky, jako jsou pravidelné odstavce, odstavců s odrážkami a rastrové obrázky.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-108">This approach extends to a number of other situations: such as, pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="1a0c9-109">Buněk v tabulce můžou obsahovat text, rozevírací seznamy nebo rastrové obrázky.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="1a0c9-110">Jeden z primární vlastnosti dokumentu, který zaměřenou na XML je, že si nejste jisti které podřízený element bude mít žádné konkrétní elementu.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="1a0c9-111">Pokud chcete pro transformaci prvků ve stromové struktuře, pokud neznáte nutně téměř podřízené prvky, které chcete transformovat, je tento přístup, který používá poznámky efektivního přístupu.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="1a0c9-112">Přehled přístupu je:</span><span class="sxs-lookup"><span data-stu-id="1a0c9-112">The summary of the approach is:</span></span>  
  
-   <span data-ttu-id="1a0c9-113">Nejprve opatřit poznámkami elementů stromu s náhradní elementem.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
-   <span data-ttu-id="1a0c9-114">Za druhé Iterujte přes celý strom vytváření větve, ve kterém nahradíte každý prvek jeho poznámky.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="1a0c9-115">V tomto příkladu implementuje iterace a vytvoření nové větve ve funkci s názvem `XForm`.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="1a0c9-116">Tento přístup se skládá z podrobně:</span><span class="sxs-lookup"><span data-stu-id="1a0c9-116">In detail, the approach consists of:</span></span>  
  
-   <span data-ttu-id="1a0c9-117">Spusťte jeden nebo více dotazech LINQ to XML, které vracejí sadu elementů, které chcete transformovat z jednoho obrazce.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="1a0c9-118">Pro každý prvek v dotazu, přidejte novou <xref:System.Xml.Linq.XElement> objektu jako poznámka k elementu.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="1a0c9-119">Tento nový prvek nahradí s poznámkami element ve stromové struktuře nové, transformovaný.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="1a0c9-120">Toto je jednoduchý kód pro zápis, jak je ukázáno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
-   <span data-ttu-id="1a0c9-121">Nový element, který je přidán jako nové podřízené uzly; může obsahovat anotaci mohl vytvořit podstromě s libovolný požadovaný tvar.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
-   <span data-ttu-id="1a0c9-122">Existuje pravidlo speciální: Pokud je podřízený uzel nového elementu v různých názvů, obor názvů, která je pro tento účel (v tomto příkladu je obor názvů `http://www.microsoft.com/LinqToXmlTransform/2007`), pak tento podřízený prvek není zkopírován do nového stromu.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="1a0c9-123">Místo toho, pokud obor názvů je uvedené výš speciální obor názvů a místní název elementu, který je `ApplyTransforms`, pak jsou podřízené uzly element ve stromové struktuře zdroj provést iteraci a zkopírovány do nového stromu (s výjimkou, která podřízené prvky jsou opatřeny poznámkami samotné transformovány podle těchto pravidel).</span><span class="sxs-lookup"><span data-stu-id="1a0c9-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
-   <span data-ttu-id="1a0c9-124">To je obdobou specifikace transformace v XSL.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="1a0c9-125">Dotaz, který vybere sada uzlů je obdobou výraz XPath pro šablonu.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="1a0c9-126">Kód pro vytvoření nového <xref:System.Xml.Linq.XElement> , který je uložený jako poznámka je obdobou konstruktoru pořadí v XSL a `ApplyTransforms` element je obdobou v funkce, která se `xsl:apply-templates` prvek XSL.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
-   <span data-ttu-id="1a0c9-127">Jednou z výhod použití tohoto postupu – jako jste formulovali dotazy, jsou vždy zápis dotazů ve stromové struktuře bez úprav zdroje.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="1a0c9-128">Můžete se nemusí starat o vlivu dotazy, které jsou zápisu změn do stromové struktury.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="1a0c9-129">Transformace stromu</span><span class="sxs-lookup"><span data-stu-id="1a0c9-129">Transforming a Tree</span></span>  
 <span data-ttu-id="1a0c9-130">Tento první příklad přejmenuje všechny `Paragraph` uzly `para`.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
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
  
 <span data-ttu-id="1a0c9-131">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1a0c9-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="1a0c9-132">Složitější transformace</span><span class="sxs-lookup"><span data-stu-id="1a0c9-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="1a0c9-133">V následujícím příkladu dotazuje stromu a vypočítá průměr a součet `Data` elementy a přidá je do stromu jako nové prvky.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
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
  
 <span data-ttu-id="1a0c9-134">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1a0c9-134">This example produces the following output:</span></span>  
  
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
  
## <a name="effecting-the-transform"></a><span data-ttu-id="1a0c9-135">Několikrát transformace</span><span class="sxs-lookup"><span data-stu-id="1a0c9-135">Effecting the Transform</span></span>  
 <span data-ttu-id="1a0c9-136">Malé funkce `XForm`, vytvoří transformovaný větve ze stromu původní, s poznámkami.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
-   <span data-ttu-id="1a0c9-137">Pseudo kód pro funkci je poměrně jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="1a0c9-137">The pseudo code for the function is quite simple:</span></span>  
  
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
  
 <span data-ttu-id="1a0c9-138">Tady je implementace této funkce:</span><span class="sxs-lookup"><span data-stu-id="1a0c9-138">Following is the implementation of this function:</span></span>  
  
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
  
## <a name="complete-example"></a><span data-ttu-id="1a0c9-139">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="1a0c9-139">Complete Example</span></span>  
 <span data-ttu-id="1a0c9-140">Následující kód je kompletní příklad, který zahrnuje `XForm` funkce.</span><span class="sxs-lookup"><span data-stu-id="1a0c9-140">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="1a0c9-141">Obsahuje některé typické použití tohoto typu transformace:</span><span class="sxs-lookup"><span data-stu-id="1a0c9-141">It includes a few of the typical uses of this type of transform:</span></span>  
  
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
  
 <span data-ttu-id="1a0c9-142">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="1a0c9-142">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1a0c9-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a0c9-143">See also</span></span>

- [<span data-ttu-id="1a0c9-144">Pokročilé technologie LINQ to XML programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a0c9-144">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
