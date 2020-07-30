---
title: Jak najít následníky podřízeného elementu (XPath-LINQ to XML) (C#)
description: Naučte se najít odvozené prvky podřízeného elementu s konkrétním názvem pomocí výrazu XPath.
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: b8e110abc2e0df99c3fdf6d2846c7cbbc4736c1a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303254"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a>Jak najít následníky podřízeného elementu (XPath-LINQ to XML) (C#)
Toto téma ukazuje, jak získat odvozené prvky podřízeného elementu s konkrétním názvem.  
  
 Výraz XPath je:  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a>Příklad  
 Tento příklad simuluje problémy extrakce textu z reprezentace XML dokumentu zpracování slova. Nejprve vybere všechny `Paragraph` prvky a potom vybere všechny `Text` následníky každého `Paragraph` prvku. Tato možnost nevybere následníky `Text` `Comment` elementu.  
  
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
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  