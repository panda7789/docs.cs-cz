---
title: Jak najít potomky s určitým názvem prvku (C#)
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: b3200a2fdf75dbf52079a2b3d27aa1a88d313406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141078"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a>Jak najít potomky s určitým názvem prvku (C#)
Někdy chcete najít všechny potomky s určitým názvem. Můžete napsat kód iterát přes všechny potomky, ale je <xref:System.Xml.Linq.XContainer.Descendants%2A> jednodušší použít osu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak najít potomky na základě názvu prvku.  
  
```csharp  
XElement root = XElement.Parse(@"<root>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
IEnumerable<string> textSegs =  
    from seg in root.Descendants("t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů. Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Parse(@"<root xmlns='http://www.adatum.com'>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<string> textSegs =  
    from seg in root.Descendants(ad + "t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
