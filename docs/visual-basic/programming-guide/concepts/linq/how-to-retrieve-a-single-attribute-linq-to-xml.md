---
title: 'Postupy: načtení jednoho atributu (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: f56ec18933856d862f9ef9630ce3d33805f96894
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321314"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="d821f-102">Postupy: načtení jednoho atributu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d821f-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d821f-103">Toto téma vysvětluje, jak načíst jediný atribut prvku s ohledem na název atributu.</span><span class="sxs-lookup"><span data-stu-id="d821f-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="d821f-104">To je užitečné pro psaní výrazů dotazů, kde chcete najít element, který má konkrétní atribut.</span><span class="sxs-lookup"><span data-stu-id="d821f-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="d821f-105">Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> třídy <xref:System.Xml.Linq.XElement> vrátí <xref:System.Xml.Linq.XAttribute> se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="d821f-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d821f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d821f-106">Example</span></span>  
 <span data-ttu-id="d821f-107">Následující příklad používá metodu <xref:System.Xml.Linq.XElement.Attribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="d821f-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 <span data-ttu-id="d821f-108">Tento příklad vyhledá všechny následníky ve stromu s názvem `Phone` a pak vyhledá atribut s názvem `type`.</span><span class="sxs-lookup"><span data-stu-id="d821f-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="d821f-109">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d821f-109">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="d821f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d821f-110">Example</span></span>  
 <span data-ttu-id="d821f-111">Pokud chcete načíst hodnotu atributu, můžete jej přetypovat stejným způsobem jako u objektů @no__t 0.</span><span class="sxs-lookup"><span data-stu-id="d821f-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d821f-112">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="d821f-112">The following example demonstrates this.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 <span data-ttu-id="d821f-113">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d821f-113">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d821f-114">poskytuje explicitní operátory přetypování pro třídu <xref:System.Xml.Linq.XAttribute> na `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, 0, 1, 2, 3, 4, 5, 6, 7, 8 , 9, 0, 1, 2, 3 a 4.</span><span class="sxs-lookup"><span data-stu-id="d821f-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d821f-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="d821f-115">Example</span></span>  
 <span data-ttu-id="d821f-116">Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d821f-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="d821f-117">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d821f-117">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="d821f-118">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d821f-118">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="d821f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d821f-119">See also</span></span>

- [<span data-ttu-id="d821f-120">LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d821f-120">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
