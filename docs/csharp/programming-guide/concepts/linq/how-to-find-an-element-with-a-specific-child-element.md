---
title: 'Postupy: Vyhledání elementu s konkrétním podřízeným elementem (C#)'
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: f007bddcbecc1cb938d05c7d444d29b6047749e8
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253745"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="d19a2-102">Postupy: Vyhledání elementu s konkrétním podřízeným elementem (C#)</span><span class="sxs-lookup"><span data-stu-id="d19a2-102">How to: Find an Element with a Specific Child Element (C#)</span></span>
<span data-ttu-id="d19a2-103">Toto téma ukazuje, jak najít konkrétní prvek, který má podřízený element s konkrétní hodnotou.</span><span class="sxs-lookup"><span data-stu-id="d19a2-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d19a2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d19a2-104">Example</span></span>  
 <span data-ttu-id="d19a2-105">Příklad vyhledá `Test` prvek, který `CommandLine` má podřízený element s hodnotou "Examp2. exe".</span><span class="sxs-lookup"><span data-stu-id="d19a2-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="d19a2-106">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Konfigurace testu (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d19a2-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="d19a2-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d19a2-107">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="d19a2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d19a2-108">Example</span></span>  
 <span data-ttu-id="d19a2-109">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d19a2-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="d19a2-110">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d19a2-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d19a2-111">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Konfigurace testu v oboru názvů](./sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="d19a2-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="d19a2-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d19a2-112">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="d19a2-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d19a2-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="d19a2-114">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="d19a2-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="d19a2-115">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="d19a2-115">Projection Operations (C#)</span></span>](./projection-operations.md)
