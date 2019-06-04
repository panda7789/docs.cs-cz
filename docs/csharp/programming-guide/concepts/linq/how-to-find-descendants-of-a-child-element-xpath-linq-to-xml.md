---
title: 'Postupy: Vyhledání potomků podřízeného elementu (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: a049ede1d533c4afc67892b7889debbe673e51c8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485481"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a>Postupy: Vyhledání potomků podřízeného elementu (XPath – LINQ to XML) (C#)
Toto téma ukazuje, jak získat následnickým elementům podřízeného elementu s konkrétním názvem.  
  
 Výraz XPath je:  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a>Příklad  
 Tento příklad napodobuje problémy s extrahují text z reprezentace XML textovém dokumentu. První vybere všechny `Paragraph` elementy a pak ji vybere všechny `Text` následnickým elementům jednotlivých `Paragraph` elementu. To nevybere následníka `Text` prvky `Comment` elementu.  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
```  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  