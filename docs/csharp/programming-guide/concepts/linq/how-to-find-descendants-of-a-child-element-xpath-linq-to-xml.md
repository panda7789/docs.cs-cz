---
title: 'Postupy: Najde následníky podřízeného elementu (XPath-LINQ to XML) (C#).'
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: f17d723aa03c45daa4e7e741ea6b14c637537ccf
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253706"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="33013-102">Postupy: Najde následníky podřízeného elementu (XPath-LINQ to XML) (C#).</span><span class="sxs-lookup"><span data-stu-id="33013-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="33013-103">Toto téma ukazuje, jak získat odvozené prvky podřízeného elementu s konkrétním názvem.</span><span class="sxs-lookup"><span data-stu-id="33013-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="33013-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="33013-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="33013-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="33013-105">Example</span></span>  
 <span data-ttu-id="33013-106">Tento příklad simuluje problémy extrakce textu z reprezentace XML dokumentu zpracování slova.</span><span class="sxs-lookup"><span data-stu-id="33013-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="33013-107">Nejprve vybere všechny `Paragraph` prvky a potom vybere všechny `Text` následníky každého `Paragraph` prvku.</span><span class="sxs-lookup"><span data-stu-id="33013-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="33013-108">Tato možnost nevybere následníky `Text` `Comment` elementu.</span><span class="sxs-lookup"><span data-stu-id="33013-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root>  
  <Paragraph>  
    <Text>This is the start of</Text>  
  </Paragraph>  
  <Comment>  
    <Text>This comment is not part of the paragraph text.</Text>  
  </Comment>  
  <Paragraph>  
    <Annotation Emphasis='true'>  
      <Text> a sentence.</Text>  
    </Annotation>  
  </Paragraph>  
  <Paragraph>  
    <Text>  This is a second sentence.</Text>  
  </Paragraph>  
</Root>");  
  
// LINQ to XML query  
string str1 =  
    root  
    .Elements("Paragraph")  
    .Descendants("Text")  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
// XPath expression  
string str2 =  
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))  
    .Cast<XText>()  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
if (str1 == str2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(str2);  
```  
  
 <span data-ttu-id="33013-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="33013-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  