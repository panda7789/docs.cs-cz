---
title: 'Postupy: Transformace stromů LINQ to XML ve stylu XSLT pomocí poznámek (C#)'
ms.date: 07/20/2015
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: ddb85194df540b13d64e83b1eb8852271b7e04b1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64597882"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a><span data-ttu-id="3fc4c-102">Postupy: Transformace stromů LINQ to XML ve stylu XSLT pomocí poznámek (C#)</span><span class="sxs-lookup"><span data-stu-id="3fc4c-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (C#)</span></span>
<span data-ttu-id="3fc4c-103">Poznámky lze použít k usnadnění transformace stromu XML.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="3fc4c-104">Některé dokumenty XML jsou "dokumentu se smíšeným obsahem na střed."</span><span class="sxs-lookup"><span data-stu-id="3fc4c-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="3fc4c-105">Pomocí těchto dokumentů neznáte nutně tvar podřízené uzly element.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="3fc4c-106">Uzel, který obsahuje text může například vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="3fc4c-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="3fc4c-107">Pro libovolný uzel daný text může být libovolný počet podřízených `<b>` a `<i>` elementy.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="3fc4c-108">Tento přístup se rozšiřuje na celou řadou dalších situacích, jako jsou například stránky, které může obsahovat různé podřízené prvky, jako jsou pravidelné odstavce, odstavců s odrážkami a rastrové obrázky.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-108">This approach extends to a number of other situations, such as pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="3fc4c-109">Buněk v tabulce můžou obsahovat text, rozevírací seznamy nebo rastrové obrázky.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="3fc4c-110">Jeden z primární vlastnosti dokumentu, který zaměřenou na XML je, že si nejste jisti které podřízený element bude mít žádné konkrétní elementu.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="3fc4c-111">Pokud chcete pro transformaci prvků ve stromové struktuře, pokud neznáte nutně téměř podřízené prvky, které chcete transformovat, je tento přístup, který používá poznámky efektivního přístupu.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="3fc4c-112">Přehled přístupu je:</span><span class="sxs-lookup"><span data-stu-id="3fc4c-112">The summary of the approach is:</span></span>  
  
- <span data-ttu-id="3fc4c-113">Nejprve opatřit poznámkami elementů stromu s náhradní elementem.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
- <span data-ttu-id="3fc4c-114">Za druhé Iterujte přes celý strom vytváření větve, ve kterém nahradíte každý prvek jeho poznámky.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="3fc4c-115">V tomto příkladu implementuje iterace a vytvoření nové větve ve funkci s názvem `XForm`.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="3fc4c-116">Tento přístup se skládá z podrobně:</span><span class="sxs-lookup"><span data-stu-id="3fc4c-116">In detail, the approach consists of:</span></span>  
  
- <span data-ttu-id="3fc4c-117">Spusťte jeden nebo více dotazech LINQ to XML, které vracejí sadu elementů, které chcete transformovat z jednoho obrazce.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="3fc4c-118">Pro každý prvek v dotazu, přidejte novou <xref:System.Xml.Linq.XElement> objektu jako poznámka k elementu.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="3fc4c-119">Tento nový prvek nahradí s poznámkami element ve stromové struktuře nové, transformovaný.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="3fc4c-120">Toto je jednoduchý kód pro zápis, jak je ukázáno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
- <span data-ttu-id="3fc4c-121">Nový element, který je přidán jako nové podřízené uzly; může obsahovat anotaci mohl vytvořit podstromě s libovolný požadovaný tvar.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
- <span data-ttu-id="3fc4c-122">Existuje pravidlo speciální: Pokud je podřízený uzel nového elementu v různých názvů, obor názvů, která je pro tento účel (v tomto příkladu je obor názvů `http://www.microsoft.com/LinqToXmlTransform/2007`), pak tento podřízený prvek není zkopírován do nového stromu.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="3fc4c-123">Místo toho, pokud obor názvů je uvedené výš speciální obor názvů a místní název elementu, který je `ApplyTransforms`, pak jsou podřízené uzly element ve stromové struktuře zdroj provést iteraci a zkopírovány do nového stromu (s výjimkou, která podřízené prvky jsou opatřeny poznámkami samotné transformovány podle těchto pravidel).</span><span class="sxs-lookup"><span data-stu-id="3fc4c-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
- <span data-ttu-id="3fc4c-124">To je obdobou specifikace transformace v XSL.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="3fc4c-125">Dotaz, který vybere sada uzlů je obdobou výraz XPath pro šablonu.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="3fc4c-126">Kód pro vytvoření nového <xref:System.Xml.Linq.XElement> , který je uložený jako poznámka je obdobou konstruktoru pořadí v XSL a `ApplyTransforms` element je obdobou v funkce, která se `xsl:apply-templates` prvek XSL.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
- <span data-ttu-id="3fc4c-127">Jednou z výhod použití tohoto postupu – jako jste formulovali dotazy, jsou vždy zápis dotazů ve stromové struktuře bez úprav zdroje.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="3fc4c-128">Můžete se nemusí starat o vlivu dotazy, které jsou zápisu změn do stromové struktury.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="3fc4c-129">Transformace stromu</span><span class="sxs-lookup"><span data-stu-id="3fc4c-129">Transforming a Tree</span></span>  
 <span data-ttu-id="3fc4c-130">Tento první příklad přejmenuje všechny `Paragraph` uzly `para`.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
```csharp  
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
XName at = xf + "ApplyTransforms";  
  
XElement root = XElement.Parse(@"  
<Root>  
    <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>  
    <Paragraph>More text.</Paragraph>  
</Root>");  
  
// replace Paragraph with para  
foreach (var el in root.Descendants("Paragraph"))  
    el.AddAnnotation(  
        new XElement("para",  
            // same idea as xsl:apply-templates  
            new XElement(xf + "ApplyTransforms")  
        )  
    );  
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newRoot = XForm(root);  
  
Console.WriteLine(newRoot);  
```  
  
 <span data-ttu-id="3fc4c-131">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3fc4c-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="3fc4c-132">Složitější transformace</span><span class="sxs-lookup"><span data-stu-id="3fc4c-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="3fc4c-133">V následujícím příkladu dotazuje stromu a vypočítá průměr a součet `Data` elementy a přidá je do stromu jako nové prvky.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
```csharp  
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
XName at = xf + "ApplyTransforms";  
  
XElement data = new XElement("Root",  
    new XElement("Data", 20),  
    new XElement("Data", 10),  
    new XElement("Data", 3)  
);  
  
// while adding annotations, you can query the source tree all you want,  
// as the tree is not mutated while annotating.
var avg = data.Elements("Data").Select(z => (Decimal)z).Average();
data.AddAnnotation(  
    new XElement("Root",  
        new XElement(xf + "ApplyTransforms"),  
        new XElement("Average", $"{avg:F4}"),
        new XElement("Sum",  
            data  
            .Elements("Data")  
            .Select(z => (int)z)  
            .Sum()  
        )  
    )  
);  
  
Console.WriteLine("Before Transform");  
Console.WriteLine("----------------");  
Console.WriteLine(data);  
Console.WriteLine();  
Console.WriteLine();  
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newData = XForm(data);  
  
Console.WriteLine("After Transform");  
Console.WriteLine("----------------");  
Console.WriteLine(newData);  
```  
  
 <span data-ttu-id="3fc4c-134">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3fc4c-134">This example produces the following output:</span></span>  
  
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
  
## <a name="effecting-the-transform"></a><span data-ttu-id="3fc4c-135">Několikrát transformace</span><span class="sxs-lookup"><span data-stu-id="3fc4c-135">Effecting the Transform</span></span>  
 <span data-ttu-id="3fc4c-136">Malé funkce `XForm`, vytvoří transformovaný větve ze stromu původní, s poznámkami.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
- <span data-ttu-id="3fc4c-137">Pseudo kód pro funkci je poměrně jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="3fc4c-137">The pseudo code for the function is quite simple:</span></span>  
  
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
  
 <span data-ttu-id="3fc4c-138">Tady je implementace této funkce:</span><span class="sxs-lookup"><span data-stu-id="3fc4c-138">Following is the implementation of this function:</span></span>  
  
```csharp  
// Build a transformed XML tree per the annotations  
static XElement XForm(XElement source)  
{  
    XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
    XName at = xf + "ApplyTransforms";  
  
    if (source.Annotation<XElement>() != null)  
    {  
        XElement anno = source.Annotation<XElement>();  
        return new XElement(anno.Name,  
            anno.Attributes(),  
            anno  
            .Nodes()  
            .Select(  
                (XNode n) =>  
                {  
                    XElement annoEl = n as XElement;  
                    if (annoEl != null)  
                    {  
                        if (annoEl.Name == at)  
                            return (object)(  
                                source.Nodes()  
                                .Select(  
                                    (XNode n2) =>  
                                    {  
                                        XElement e2 = n2 as XElement;  
                                        if (e2 == null)  
                                            return n2;  
                                        else  
                                            return XForm(e2);  
                                    }  
                                )  
                            );  
                        else  
                            return n;  
                    }  
                    else  
                        return n;  
                }  
            )  
        );  
    }  
    else  
    {  
        return new XElement(source.Name,  
            source.Attributes(),  
            source  
                .Nodes()  
                .Select(n =>  
                {  
                    XElement el = n as XElement;  
                    if (el == null)  
                        return n;  
                    else  
                        return XForm(el);  
                }  
                )  
        );  
    }  
}   
```  
  
## <a name="complete-example"></a><span data-ttu-id="3fc4c-139">Kompletní příklad</span><span class="sxs-lookup"><span data-stu-id="3fc4c-139">Complete Example</span></span>  
 <span data-ttu-id="3fc4c-140">Následující kód je kompletní příklad, který zahrnuje `XForm` funkce.</span><span class="sxs-lookup"><span data-stu-id="3fc4c-140">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="3fc4c-141">Obsahuje některé typické použití tohoto typu transformace:</span><span class="sxs-lookup"><span data-stu-id="3fc4c-141">It includes a few of the typical uses of this type of transform:</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Xml;  
using System.Xml.Linq;  
  
class Program  
{  
    static XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
    static XName at = xf + "ApplyTransforms";  
  
    // Build a transformed XML tree per the annotations  
    static XElement XForm(XElement source)  
    {  
        if (source.Annotation<XElement>() != null)  
        {  
            XElement anno = source.Annotation<XElement>();  
            return new XElement(anno.Name,  
                anno.Attributes(),  
                anno  
                .Nodes()  
                .Select(  
                    (XNode n) =>  
                    {  
                        XElement annoEl = n as XElement;  
                        if (annoEl != null)  
                        {  
                            if (annoEl.Name == at)  
                                return (object)(  
                                    source.Nodes()  
                                    .Select(  
                                        (XNode n2) =>  
                                        {  
                                            XElement e2 = n2 as XElement;  
                                            if (e2 == null)  
                                                return n2;  
                                            else  
                                                return XForm(e2);  
                                        }  
                                    )  
                                );  
                            else  
                                return n;  
                        }  
                        else  
                            return n;  
                    }  
                )  
            );  
        }  
        else  
        {  
            return new XElement(source.Name,  
                source.Attributes(),  
                source  
                    .Nodes()  
                    .Select(n =>  
                    {  
                        XElement el = n as XElement;  
                        if (el == null)  
                            return n;  
                        else  
                            return XForm(el);  
                    }  
                    )  
            );  
        }  
    }  
  
    static void Main(string[] args)  
    {  
        XElement root = new XElement("Root",  
            new XComment("A comment"),  
            new XAttribute("Att1", 123),  
            new XElement("Child", 1),  
            new XElement("Child", 2),  
            new XElement("Other",  
                new XElement("GC", 3),  
                new XElement("GC", 4)  
            ),  
            XElement.Parse(  
              "<SomeMixedContent>This is <i>an</i> element that " +  
              "<b>has</b> some mixed content</SomeMixedContent>"),  
            new XElement("AnUnchangedElement", 42)  
        );  
  
        // each of the following serves the same semantic purpose as  
        // XSLT templates and sequence constructors  
  
        // replace Child with NewChild  
        foreach (var el in root.Elements("Child"))  
            el.AddAnnotation(new XElement("NewChild", (string)el));  
  
        // replace first GC with GrandChild, add an attribute  
        foreach (var el in root.Descendants("GC").Take(1))  
            el.AddAnnotation(  
                new XElement("GrandChild",  
                    new XAttribute("ANewAttribute", 999),  
                    (string)el  
                )  
            );  
  
        // replace Other with NewOther, add new child elements around original content  
        foreach (var el in root.Elements("Other"))  
            el.AddAnnotation(  
                new XElement("NewOther",  
                    new XElement("MyNewChild", 1),  
                    // same idea as xsl:apply-templates  
                    new XElement(xf + "ApplyTransforms"),  
                    new XElement("ChildThatComesAfter")  
                )  
            );  
  
        // change name of element that has mixed content  
        root.Descendants("SomeMixedContent").First().AddAnnotation(  
            new XElement("MixedContent",  
                new XElement(xf + "ApplyTransforms")  
            )  
        );  
  
        // replace <b> with <Bold>  
        foreach (var el in root.Descendants("b"))  
            el.AddAnnotation(  
                new XElement("Bold",  
                    new XElement(xf + "ApplyTransforms")  
                )  
            );  
  
        // replace <i> with <Italic>  
        foreach (var el in root.Descendants("i"))  
            el.AddAnnotation(  
                new XElement("Italic",  
                    new XElement(xf + "ApplyTransforms")  
                )  
            );  
  
        Console.WriteLine("Before Transform");  
        Console.WriteLine("----------------");  
        Console.WriteLine(root);  
        Console.WriteLine();  
        Console.WriteLine();  
        XElement newRoot = XForm(root);  
  
        Console.WriteLine("After Transform");  
        Console.WriteLine("----------------");  
        Console.WriteLine(newRoot);  
    }  
}  
```  
  
 <span data-ttu-id="3fc4c-142">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3fc4c-142">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3fc4c-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fc4c-143">See also</span></span>

- [<span data-ttu-id="3fc4c-144">Pokročilé technologie LINQ to XML programování (C#)</span><span class="sxs-lookup"><span data-stu-id="3fc4c-144">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
