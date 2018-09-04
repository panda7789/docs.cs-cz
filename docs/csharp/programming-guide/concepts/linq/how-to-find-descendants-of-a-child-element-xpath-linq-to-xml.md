---
title: 'Postupy: vyhledání potomků podřízeného elementu (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: 2fbb5111cdabac5ecbdc1db43e2ce2f41ebb7303
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523201"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a>Postupy: vyhledání potomků podřízeného elementu (XPath – LINQ to XML) (C#)
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
  
## <a name="see-also"></a>Viz také

- [LINQ to XML pro uživatele jazyka XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
