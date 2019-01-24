---
title: 'Postupy: Vyhledání potomků s konkrétním názvem elementu (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 11f13dfc61e837a923cb9709301d89ff6d2149dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530386"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="e6c6e-102">Postupy: Vyhledání potomků s konkrétním názvem elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="e6c6e-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="e6c6e-103">Někdy budete chtít vyhledání všech potomků s konkrétním názvem.</span><span class="sxs-lookup"><span data-stu-id="e6c6e-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="e6c6e-104">Můžete napsat kód k iteraci v rámci všechny následníky, ale je jednodušší použít <xref:System.Xml.Linq.XContainer.Descendants%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="e6c6e-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6c6e-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6c6e-105">Example</span></span>  
 <span data-ttu-id="e6c6e-106">Následující příklad ukazuje, jak vyhledání potomků vycházet z názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="e6c6e-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="e6c6e-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e6c6e-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="e6c6e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6c6e-108">Example</span></span>  
 <span data-ttu-id="e6c6e-109">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e6c6e-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e6c6e-110">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="e6c6e-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="e6c6e-111">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e6c6e-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6c6e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6c6e-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- [<span data-ttu-id="e6c6e-113">Základní dotazy (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e6c6e-113">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
