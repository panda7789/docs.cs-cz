---
title: Jak najít následníky s konkrétním názvem elementu (C#)
description: Naučte se najít všechny následníky s určitým názvem pomocí osy následníků. Podívejte se na příklady kódu a další zdroje informací.
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 96ebf2d10a9ed5e07aab2870142f9869903ad442
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303241"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="a7222-104">Jak najít následníky s konkrétním názvem elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="a7222-104">How to find descendants with a specific element name (C#)</span></span>
<span data-ttu-id="a7222-105">Někdy budete chtít najít všechny následníky s určitým názvem.</span><span class="sxs-lookup"><span data-stu-id="a7222-105">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="a7222-106">Můžete napsat kód pro iterování všemi následníky, ale je snazší použít <xref:System.Xml.Linq.XContainer.Descendants%2A> osu.</span><span class="sxs-lookup"><span data-stu-id="a7222-106">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7222-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7222-107">Example</span></span>  
 <span data-ttu-id="a7222-108">Následující příklad ukazuje, jak najít následníky na základě názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="a7222-108">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="a7222-109">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a7222-109">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="a7222-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7222-110">Example</span></span>  
 <span data-ttu-id="a7222-111">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a7222-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a7222-112">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a7222-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="a7222-113">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a7222-113">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7222-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7222-114">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
