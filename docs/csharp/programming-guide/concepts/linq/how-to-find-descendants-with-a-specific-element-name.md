---
title: 'Postupy: Vyhledání potomků s konkrétním názvem elementu (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: c54b3c6a01459781b8ed9d5495bf9eb8937363fa
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486755"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="c12d5-102">Postupy: Vyhledání potomků s konkrétním názvem elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="c12d5-102">How to: Find Descendants with a Specific Element Name (C#)</span></span>
<span data-ttu-id="c12d5-103">Někdy budete chtít vyhledání všech potomků s konkrétním názvem.</span><span class="sxs-lookup"><span data-stu-id="c12d5-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="c12d5-104">Můžete napsat kód k iteraci v rámci všechny následníky, ale je jednodušší použít <xref:System.Xml.Linq.XContainer.Descendants%2A> osy.</span><span class="sxs-lookup"><span data-stu-id="c12d5-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c12d5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c12d5-105">Example</span></span>  
 <span data-ttu-id="c12d5-106">Následující příklad ukazuje, jak vyhledání potomků vycházet z názvu elementu.</span><span class="sxs-lookup"><span data-stu-id="c12d5-106">The following example shows how to find descendants based on the element name.</span></span>  
  
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
  
 <span data-ttu-id="c12d5-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c12d5-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="c12d5-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c12d5-108">Example</span></span>  
 <span data-ttu-id="c12d5-109">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c12d5-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="c12d5-110">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c12d5-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="c12d5-111">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c12d5-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="c12d5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c12d5-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
