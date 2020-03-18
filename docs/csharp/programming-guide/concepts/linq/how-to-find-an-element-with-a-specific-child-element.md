---
title: Jak najít prvek s určitým podřízeným prvkem (C#)
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 0536b1b92d4d7fc18b5d406bbcd24aefc6a840c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141146"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="4dce9-102">Jak najít prvek s určitým podřízeným prvkem (C#)</span><span class="sxs-lookup"><span data-stu-id="4dce9-102">How to find an element with a specific child element (C#)</span></span>
<span data-ttu-id="4dce9-103">Toto téma ukazuje, jak najít konkrétní prvek, který má podřízený prvek s určitou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="4dce9-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dce9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4dce9-104">Example</span></span>  
 <span data-ttu-id="4dce9-105">Příklad vyhledá `Test` prvek, který `CommandLine` má podřízený prvek s hodnotou "Examp2.EXE".</span><span class="sxs-lookup"><span data-stu-id="4dce9-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="4dce9-106">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Test Configuration (LINQ to XML).](./sample-xml-file-test-configuration-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="4dce9-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="4dce9-107">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4dce9-107">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="4dce9-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="4dce9-108">Example</span></span>  
 <span data-ttu-id="4dce9-109">Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4dce9-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="4dce9-110">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4dce9-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="4dce9-111">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Testovat konfiguraci v oboru názvů](./sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="4dce9-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="4dce9-112">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4dce9-112">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="4dce9-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="4dce9-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="4dce9-114">Standardní operátory dotazů – přehled (C#)</span><span class="sxs-lookup"><span data-stu-id="4dce9-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="4dce9-115">Projekční operace (C#)</span><span class="sxs-lookup"><span data-stu-id="4dce9-115">Projection Operations (C#)</span></span>](./projection-operations.md)
