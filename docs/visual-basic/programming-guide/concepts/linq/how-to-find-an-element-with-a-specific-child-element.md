---
title: 'Postupy: Vyhledání elementu s konkrétním podřízeným elementem (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: 4df2f8f55a516665c02d12c3bdf6569601db30c2
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249915"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a><span data-ttu-id="d9968-102">Postupy: Vyhledání elementu s konkrétním podřízeným elementem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9968-102">How to: Find an Element with a Specific Child Element (Visual Basic)</span></span>
<span data-ttu-id="d9968-103">Toto téma ukazuje, jak najít konkrétní prvek, který má podřízený element s konkrétní hodnotou.</span><span class="sxs-lookup"><span data-stu-id="d9968-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9968-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9968-104">Example</span></span>  
 <span data-ttu-id="d9968-105">Příklad vyhledá prvek `Test`, který má podřízený element `CommandLine` s hodnotou "Examp2. EXE".</span><span class="sxs-lookup"><span data-stu-id="d9968-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="d9968-106">Tento příklad používá následující dokument XML: [ukázkový soubor XML: testovací konfigurace (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d9968-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 <span data-ttu-id="d9968-107">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d9968-107">This code produces the following output:</span></span>  
  
```console  
0002  
0006  
```  
  
 <span data-ttu-id="d9968-108">Všimněte si, že v tomto příkladu je použita [vlastnost podřízená osa XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), [vlastnost osy atributu XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)a [vlastnost hodnoty XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="d9968-108">Note that this example uses the [XML Child axis property](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9968-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9968-109">Example</span></span>  
 <span data-ttu-id="d9968-110">Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d9968-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="d9968-111">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d9968-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d9968-112">Tento příklad používá následující dokument XML: [ukázkový soubor XML: konfigurace testu v oboru názvů](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="d9968-112">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="d9968-113">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d9968-113">This code produces the following output:</span></span>  
  
```console  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9968-114">Související témata</span><span class="sxs-lookup"><span data-stu-id="d9968-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="d9968-115">Základní dotazy (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9968-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="d9968-116">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9968-116">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d9968-117">Operace projekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9968-117">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
