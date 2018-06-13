---
title: 'Postupy: vyhledání následníky s konkrétní Element názvu (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: f95551f0c1506a56474d497622b90090cc4c8865
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320229"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="cfe4c-102">Postupy: vyhledání následníky s konkrétní Element názvu (C#)</span><span class="sxs-lookup"><span data-stu-id="cfe4c-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="cfe4c-103">Někdy budete chtít vyhledání všech potomků s konkrétním názvem.</span><span class="sxs-lookup"><span data-stu-id="cfe4c-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="cfe4c-104">Můžete napsat kód, k iteraci v rámci všech následníky, ale je jednodušší použít <xref:System.Xml.Linq.XContainer.Descendants%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="cfe4c-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfe4c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="cfe4c-105">Example</span></span>  
 <span data-ttu-id="cfe4c-106">Následující příklad ukazuje, jak najít následníků na základě názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="cfe4c-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="cfe4c-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cfe4c-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="cfe4c-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="cfe4c-108">Example</span></span>  
 <span data-ttu-id="cfe4c-109">Následující příklad ukazuje stejný dotaz pro formát XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cfe4c-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="cfe4c-110">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="cfe4c-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="cfe4c-111">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="cfe4c-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="cfe4c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfe4c-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A>  
 [<span data-ttu-id="cfe4c-113">Základní dotazy (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cfe4c-113">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
