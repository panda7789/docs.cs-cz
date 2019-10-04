---
title: 'Postupy: práce se slovníky pomocí LINQ to XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: 9773b926d16b51ea912792b0f348a26a9a3c7a29
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835087"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a><span data-ttu-id="b397c-102">Postupy: práce se slovníky pomocí LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b397c-102">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="b397c-103">Je často vhodné převést odrůdy datových struktur do XML a vrátit se do jiných datových struktur.</span><span class="sxs-lookup"><span data-stu-id="b397c-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="b397c-104">Toto téma ukazuje konkrétní implementaci tohoto obecného přístupu převodem <xref:System.Collections.Generic.Dictionary%602> na XML a zpět.</span><span class="sxs-lookup"><span data-stu-id="b397c-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b397c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b397c-105">Example</span></span>  
 <span data-ttu-id="b397c-106">Tento příklad používá literály XML a dotaz ve vloženém výrazu.</span><span class="sxs-lookup"><span data-stu-id="b397c-106">This example uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="b397c-107">Dotaz projektuje nové objekty @no__t 0, které se pak stanou novým obsahem pro objekt `Root` <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b397c-107">The query projects new <xref:System.Xml.Linq.XElement> objects, which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="b397c-108">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b397c-108">This code produces the following output:</span></span>  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="b397c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b397c-109">Example</span></span>  
 <span data-ttu-id="b397c-110">Následující kód vytvoří slovník z XML.</span><span class="sxs-lookup"><span data-stu-id="b397c-110">The following code creates a dictionary from XML.</span></span>  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 <span data-ttu-id="b397c-111">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b397c-111">This code produces the following output:</span></span>  
  
```console  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="b397c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b397c-112">See also</span></span>

- [<span data-ttu-id="b397c-113">Projekce a transformace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b397c-113">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
