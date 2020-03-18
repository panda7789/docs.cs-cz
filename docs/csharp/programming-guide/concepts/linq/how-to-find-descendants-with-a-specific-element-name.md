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
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="510c3-102">Jak najít potomky s určitým názvem prvku (C#)</span><span class="sxs-lookup"><span data-stu-id="510c3-102">How to find descendants with a specific element name (C#)</span></span>
<span data-ttu-id="510c3-103">Někdy chcete najít všechny potomky s určitým názvem.</span><span class="sxs-lookup"><span data-stu-id="510c3-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="510c3-104">Můžete napsat kód iterát přes všechny potomky, ale je <xref:System.Xml.Linq.XContainer.Descendants%2A> jednodušší použít osu.</span><span class="sxs-lookup"><span data-stu-id="510c3-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="510c3-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="510c3-105">Example</span></span>  
 <span data-ttu-id="510c3-106">Následující příklad ukazuje, jak najít potomky na základě názvu prvku.</span><span class="sxs-lookup"><span data-stu-id="510c3-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="510c3-107">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="510c3-107">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="510c3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="510c3-108">Example</span></span>  
 <span data-ttu-id="510c3-109">Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="510c3-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="510c3-110">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="510c3-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="510c3-111">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="510c3-111">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="510c3-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="510c3-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
