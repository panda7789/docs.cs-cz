---
title: 'Postupy: Najít následníky s určitým názvem elementu (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 8c859c555109a6f68a6b4290c536b10114620f3d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253699"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="6accb-102">Postupy: Najít následníky s určitým názvem elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="6accb-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="6accb-103">Někdy budete chtít najít všechny následníky s určitým názvem.</span><span class="sxs-lookup"><span data-stu-id="6accb-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="6accb-104">Můžete napsat kód pro iterování všemi následníky, ale je snazší použít <xref:System.Xml.Linq.XContainer.Descendants%2A> osu.</span><span class="sxs-lookup"><span data-stu-id="6accb-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6accb-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="6accb-105">Example</span></span>  
 <span data-ttu-id="6accb-106">Následující příklad ukazuje, jak najít následníky na základě názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="6accb-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="6accb-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6accb-107">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="6accb-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6accb-108">Example</span></span>  
 <span data-ttu-id="6accb-109">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6accb-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="6accb-110">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="6accb-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="6accb-111">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="6accb-111">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="6accb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6accb-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
