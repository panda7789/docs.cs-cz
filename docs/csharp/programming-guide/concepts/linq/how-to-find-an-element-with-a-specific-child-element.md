---
title: Jak najít element s konkrétním podřízeným elementem (C#)
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 0536b1b92d4d7fc18b5d406bbcd24aefc6a840c6
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141146"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="7de47-102">Jak najít element s konkrétním podřízeným elementem (C#)</span><span class="sxs-lookup"><span data-stu-id="7de47-102">How to find an element with a specific child element (C#)</span></span>
<span data-ttu-id="7de47-103">Toto téma ukazuje, jak najít konkrétní prvek, který má podřízený element s konkrétní hodnotou.</span><span class="sxs-lookup"><span data-stu-id="7de47-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7de47-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7de47-104">Example</span></span>  
 <span data-ttu-id="7de47-105">Příklad vyhledá prvek `Test`, který má `CommandLine` podřízený element s hodnotou "Examp2. EXE".</span><span class="sxs-lookup"><span data-stu-id="7de47-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="7de47-106">Tento příklad používá následující dokument XML: [ukázkový soubor XML: testovací konfigurace (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7de47-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="7de47-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7de47-107">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="7de47-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="7de47-108">Example</span></span>  
 <span data-ttu-id="7de47-109">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7de47-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="7de47-110">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7de47-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7de47-111">Tento příklad používá následující dokument XML: [ukázkový soubor XML: konfigurace testu v oboru názvů](./sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="7de47-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="7de47-112">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7de47-112">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="7de47-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7de47-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="7de47-114">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="7de47-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="7de47-115">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="7de47-115">Projection Operations (C#)</span></span>](./projection-operations.md)
