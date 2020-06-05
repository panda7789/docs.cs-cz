---
title: 'Postupy: Transformace stromů LINQ to XML ve stylu XSLT pomocí poznámek'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: 099457eaab8c80605138d7e67d7bc2823e316234
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364445"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a><span data-ttu-id="520ad-102">Postupy: použití poznámek k transformaci LINQ to XMLch stromů ve stylu XSLT (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="520ad-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)</span></span>

<span data-ttu-id="520ad-103">Poznámky lze použít k usnadnění transformací stromu XML.</span><span class="sxs-lookup"><span data-stu-id="520ad-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>

<span data-ttu-id="520ad-104">Některé dokumenty XML jsou "dokumenty orientované na smíšený obsah".</span><span class="sxs-lookup"><span data-stu-id="520ad-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="520ad-105">S takovými dokumenty nemusíte nutně znát tvar podřízených uzlů prvku.</span><span class="sxs-lookup"><span data-stu-id="520ad-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="520ad-106">Například uzel, který obsahuje text, může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="520ad-106">For instance, a node that contains text may look like this:</span></span>

```xml
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>
```

<span data-ttu-id="520ad-107">Pro libovolný daný textový uzel může existovat libovolný počet podřízených `<b>` `<i>` prvků a.</span><span class="sxs-lookup"><span data-stu-id="520ad-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="520ad-108">Tento přístup se rozšiřuje na řadu dalších situací: například stránky, které mohou obsahovat různé podřízené prvky, jako jsou například běžné odstavce, odstavce s odrážkami a rastry.</span><span class="sxs-lookup"><span data-stu-id="520ad-108">This approach extends to a number of other situations: such as, pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="520ad-109">Buňky v tabulce mohou obsahovat text, rozevírací seznamy nebo rastrové obrázky.</span><span class="sxs-lookup"><span data-stu-id="520ad-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="520ad-110">Jednou z hlavních charakteristik XML orientovaného dokumentu je, že nevíte, který podřízený prvek bude mít konkrétní prvek.</span><span class="sxs-lookup"><span data-stu-id="520ad-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>

<span data-ttu-id="520ad-111">Pokud chcete transformovat prvky ve stromové struktuře, kde nevíte nutně o podřízených objektech prvků, které chcete transformovat, pak tento přístup, který používá poznámky, představuje účinný přístup.</span><span class="sxs-lookup"><span data-stu-id="520ad-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>

<span data-ttu-id="520ad-112">Souhrn tohoto přístupu:</span><span class="sxs-lookup"><span data-stu-id="520ad-112">The summary of the approach is:</span></span>

- <span data-ttu-id="520ad-113">Nejprve opatřit poznámkami prvky ve stromové struktuře náhradním elementem.</span><span class="sxs-lookup"><span data-stu-id="520ad-113">First, annotate elements in the tree with a replacement element.</span></span>

- <span data-ttu-id="520ad-114">Potom Iterujte celý strom a vytvořte nový strom, ve kterém nahradíte jednotlivé prvky jeho anotací.</span><span class="sxs-lookup"><span data-stu-id="520ad-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="520ad-115">Tento příklad implementuje iteraci a vytvoření nového stromu ve funkci s názvem `XForm` .</span><span class="sxs-lookup"><span data-stu-id="520ad-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>

<span data-ttu-id="520ad-116">Tento přístup se skládá z těchto možností:</span><span class="sxs-lookup"><span data-stu-id="520ad-116">In detail, the approach consists of:</span></span>

- <span data-ttu-id="520ad-117">Proveďte jeden nebo více LINQ to XML dotazů, které vracejí sadu prvků, které chcete transformovat z jednoho obrazce na jiný.</span><span class="sxs-lookup"><span data-stu-id="520ad-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="520ad-118">Pro každý prvek v dotazu přidejte nový <xref:System.Xml.Linq.XElement> objekt jako anotaci k elementu.</span><span class="sxs-lookup"><span data-stu-id="520ad-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="520ad-119">Tento nový element nahradí element s poznámkou v novém, transformované stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="520ad-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="520ad-120">Toto je jednoduchý kód pro zápis, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="520ad-120">This is simple code to write, as demonstrated by the example.</span></span>

- <span data-ttu-id="520ad-121">Nový prvek, který je přidán jako anotace, může obsahovat nové podřízené uzly; může vytvořit dílčí strom s libovolným požadovaným tvarem.</span><span class="sxs-lookup"><span data-stu-id="520ad-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>

- <span data-ttu-id="520ad-122">Existuje zvláštní pravidlo: Pokud je podřízený uzel nového prvku v jiném oboru názvů, vytvoří se obor názvů, který je vytvořen pro tento účel (v tomto příkladu je v tomto příkladu obor názvů `http://www.microsoft.com/LinqToXmlTransform/2007` ), pak tento podřízený element není zkopírován do nového stromu.</span><span class="sxs-lookup"><span data-stu-id="520ad-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="520ad-123">Místo toho, pokud je tento obor názvů výše zmíněným speciálním oborem názvů a místní název elementu je `ApplyTransforms` , pak se v podřízených uzlech elementu ve stromu zdrojového kódu prochází a zkopírují se do nového stromu (s výjimkou, že se podřízené prvky s poznámkami samy transformují podle těchto pravidel).</span><span class="sxs-lookup"><span data-stu-id="520ad-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>

- <span data-ttu-id="520ad-124">To je trochu podobné určení transformací v prvku XSL.</span><span class="sxs-lookup"><span data-stu-id="520ad-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="520ad-125">Dotaz, který vybere sadu uzlů, je podobný výrazu XPath pro šablonu.</span><span class="sxs-lookup"><span data-stu-id="520ad-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="520ad-126">Kód pro vytvoření nového <xref:System.Xml.Linq.XElement> , který je uložen jako anotace, je podobný konstruktoru sekvence v prvku xsl a `ApplyTransforms` element je podobný funkci `xsl:apply-templates` elementu v prvku xsl.</span><span class="sxs-lookup"><span data-stu-id="520ad-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>

- <span data-ttu-id="520ad-127">Jednou z výhod tohoto přístupu – při formulování dotazů vždy zapisujete dotazy na neupravený zdrojový strom.</span><span class="sxs-lookup"><span data-stu-id="520ad-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="520ad-128">Nemusíte si dělat starosti s tím, jak změny stromu ovlivňují dotazy, které píšete.</span><span class="sxs-lookup"><span data-stu-id="520ad-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>

## <a name="transforming-a-tree"></a><span data-ttu-id="520ad-129">Transformace stromu</span><span class="sxs-lookup"><span data-stu-id="520ad-129">Transforming a Tree</span></span>

<span data-ttu-id="520ad-130">Tento první příklad přejmenuje všechny `Paragraph` uzly na `para` :</span><span class="sxs-lookup"><span data-stu-id="520ad-130">This first example renames all `Paragraph` nodes to `para`:</span></span>

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

 <span data-ttu-id="520ad-131">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="520ad-131">This example produces the following output:</span></span>

```xml
<Root>
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>
  <para>More text.</para>
</Root>
```

## <a name="a-more-complicated-transform"></a><span data-ttu-id="520ad-132">Složitější transformace</span><span class="sxs-lookup"><span data-stu-id="520ad-132">A more complicated transform</span></span>

<span data-ttu-id="520ad-133">Následující příklad dotazuje strom a vypočítá průměr a součet `Data` prvků a přidá je do stromu jako nové prvky.</span><span class="sxs-lookup"><span data-stu-id="520ad-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>

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

<span data-ttu-id="520ad-134">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="520ad-134">This example produces the following output:</span></span>

```console
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

## <a name="effecting-the-transform"></a><span data-ttu-id="520ad-135">Ovlivnění transformace</span><span class="sxs-lookup"><span data-stu-id="520ad-135">Effecting the transform</span></span>

<span data-ttu-id="520ad-136">Malá funkce, `XForm` vytvoří novou transformované stromovou strukturu z původního pokomentovaného stromu.</span><span class="sxs-lookup"><span data-stu-id="520ad-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>

<span data-ttu-id="520ad-137">Pseudo kód pro funkci je poměrně jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="520ad-137">The pseudo code for the function is quite simple:</span></span>

> <span data-ttu-id="520ad-138">Funkce přebírá jako argument XElement a vrátí XElement.</span><span class="sxs-lookup"><span data-stu-id="520ad-138">The function takes an XElement as an argument and returns an XElement.</span></span>
>
> <span data-ttu-id="520ad-139">Pokud má element anotaci XElement, vraťte novou XElement:</span><span class="sxs-lookup"><span data-stu-id="520ad-139">If an element has an XElement annotation, then return a new XElement:</span></span>
>
> - <span data-ttu-id="520ad-140">Název nového XElement je název prvku poznámky.</span><span class="sxs-lookup"><span data-stu-id="520ad-140">The name of the new XElement is the annotation element's name.</span></span>
> - <span data-ttu-id="520ad-141">Všechny atributy jsou zkopírovány z poznámky do nového uzlu.</span><span class="sxs-lookup"><span data-stu-id="520ad-141">All attributes are copied from the annotation to the new node.</span></span>
> - <span data-ttu-id="520ad-142">Všechny podřízené uzly jsou zkopírovány z anotace s výjimkou, že speciální uzel XF: ApplyTransforms je rozpoznán a podřízené uzly zdrojového elementu jsou iterace.</span><span class="sxs-lookup"><span data-stu-id="520ad-142">All child nodes are copied from the annotation, with the exception that the special node xf:ApplyTransforms is recognized, and the source element's child nodes are iterated.</span></span> <span data-ttu-id="520ad-143">Pokud zdrojový podřízený uzel není XElement, je zkopírován do nového stromu.</span><span class="sxs-lookup"><span data-stu-id="520ad-143">If the source child node is not an XElement, it is copied to the new tree.</span></span> <span data-ttu-id="520ad-144">Pokud je zdrojový podřízený objekt XElement, je transformované voláním této funkce rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="520ad-144">If the source child is an XElement, then it is transformed by calling this function recursively.</span></span>
>
> <span data-ttu-id="520ad-145">Pokud element není opatřen poznámkami:</span><span class="sxs-lookup"><span data-stu-id="520ad-145">If an element is not annotated:</span></span>
>
> - <span data-ttu-id="520ad-146">Vrátit novou XElement</span><span class="sxs-lookup"><span data-stu-id="520ad-146">Return a new XElement</span></span>
>   - <span data-ttu-id="520ad-147">Název nového XElement je název zdrojového elementu.</span><span class="sxs-lookup"><span data-stu-id="520ad-147">The name of the new XElement is the source element's name.</span></span>
>   - <span data-ttu-id="520ad-148">Všechny atributy jsou zkopírovány ze zdrojového elementu do elementu cíle.</span><span class="sxs-lookup"><span data-stu-id="520ad-148">All attributes are copied from the source element to the destination's element.</span></span>
>   - <span data-ttu-id="520ad-149">Všechny podřízené uzly jsou zkopírovány ze zdrojového elementu.</span><span class="sxs-lookup"><span data-stu-id="520ad-149">All child nodes are copied from the source element.</span></span>
>   - <span data-ttu-id="520ad-150">Pokud zdrojový podřízený uzel není XElement, je zkopírován do nového stromu.</span><span class="sxs-lookup"><span data-stu-id="520ad-150">If the source child node is not an XElement, it is copied to the new tree.</span></span> <span data-ttu-id="520ad-151">Pokud je zdrojový podřízený objekt XElement, je transformované voláním této funkce rekurzivně.</span><span class="sxs-lookup"><span data-stu-id="520ad-151">If the source child is an XElement, then it is transformed by calling this function recursively.</span></span>

<span data-ttu-id="520ad-152">Následující kód je implementace této funkce:</span><span class="sxs-lookup"><span data-stu-id="520ad-152">The following code is the implementation of this function:</span></span>

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

## <a name="complete-example"></a><span data-ttu-id="520ad-153">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="520ad-153">Complete example</span></span>

<span data-ttu-id="520ad-154">Následující kód je kompletní příklad, který obsahuje `XForm` funkci.</span><span class="sxs-lookup"><span data-stu-id="520ad-154">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="520ad-155">Obsahuje několik typických použití tohoto typu transformace:</span><span class="sxs-lookup"><span data-stu-id="520ad-155">It includes a few of the typical uses of this type of transform:</span></span>

```vb
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

<span data-ttu-id="520ad-156">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="520ad-156">This example produces the following output:</span></span>

```console
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

## <a name="see-also"></a><span data-ttu-id="520ad-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="520ad-157">See also</span></span>

- [<span data-ttu-id="520ad-158">Rozšířené programování LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="520ad-158">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
