---
title: 'Postupy: Vyhledání elementu s konkrétním podřízeným elementem (C#)'
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: a2ff30ebfc8936d351358f77c0655eb584e6d390
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710086"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="c1d1e-102">Postupy: Vyhledání elementu s konkrétním podřízeným elementem (C#)</span><span class="sxs-lookup"><span data-stu-id="c1d1e-102">How to: Find an Element with a Specific Child Element (C#)</span></span>
<span data-ttu-id="c1d1e-103">Toto téma ukazuje, jak najít konkrétní prvek, který má podřízený element s konkrétní hodnotou.</span><span class="sxs-lookup"><span data-stu-id="c1d1e-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1d1e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1d1e-104">Example</span></span>  
 <span data-ttu-id="c1d1e-105">Příklad vyhledá `Test` prvek, který `CommandLine` má podřízený element s hodnotou "Examp2. exe".</span><span class="sxs-lookup"><span data-stu-id="c1d1e-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="c1d1e-106">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Konfigurace testu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c1d1e-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="c1d1e-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c1d1e-107">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="c1d1e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1d1e-108">Example</span></span>  
 <span data-ttu-id="c1d1e-109">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c1d1e-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="c1d1e-110">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c1d1e-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c1d1e-111">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Konfigurace testu v oboru názvů](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="c1d1e-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="c1d1e-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c1d1e-112">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1d1e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1d1e-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="c1d1e-114">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="c1d1e-114">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="c1d1e-115">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="c1d1e-115">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
