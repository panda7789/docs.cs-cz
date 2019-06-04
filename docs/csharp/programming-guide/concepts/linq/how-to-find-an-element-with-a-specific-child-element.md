---
title: 'Postupy: Vyhledání elementu s konkrétním podřízeným elementem (C#)'
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 71068774b93581fdd82a0fe57651bc7780ca1ef1
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485568"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="595d7-102">Postupy: Vyhledání elementu s konkrétním podřízeným elementem (C#)</span><span class="sxs-lookup"><span data-stu-id="595d7-102">How to: Find an Element with a Specific Child Element (C#)</span></span>
<span data-ttu-id="595d7-103">Toto téma ukazuje, jak najít konkrétní element, který má podřízený element s určitou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="595d7-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="595d7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="595d7-104">Example</span></span>  
 <span data-ttu-id="595d7-105">Vyhledá v příkladu `Test` element, který má `CommandLine` podřízený element s hodnotou "Examp2.EXE".</span><span class="sxs-lookup"><span data-stu-id="595d7-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="595d7-106">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Otestujte konfiguraci (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="595d7-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="595d7-107">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="595d7-107">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="595d7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="595d7-108">Example</span></span>  
 <span data-ttu-id="595d7-109">Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="595d7-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="595d7-110">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="595d7-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="595d7-111">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Konfigurace testu v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).</span><span class="sxs-lookup"><span data-stu-id="595d7-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="595d7-112">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="595d7-112">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="595d7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="595d7-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="595d7-114">Přehled standardních operátorů dotazu (C#)</span><span class="sxs-lookup"><span data-stu-id="595d7-114">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="595d7-115">Operace projekce (C#)</span><span class="sxs-lookup"><span data-stu-id="595d7-115">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
