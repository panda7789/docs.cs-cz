---
title: 'Postupy: načtení jednoho atributu (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 02afbc987cf9f55d16bb56912f3eaf45cd8c9a37
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347567"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="3ecc5-102">Postupy: načtení jednoho atributu (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ecc5-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="3ecc5-103">Toto téma vysvětluje, jak načíst jediný atribut prvku s ohledem na název atributu.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="3ecc5-104">To je užitečné pro psaní výrazů dotazů, kde chcete najít element, který má konkrétní atribut.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="3ecc5-105">Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> třídy <xref:System.Xml.Linq.XElement> vrací <xref:System.Xml.Linq.XAttribute> se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ecc5-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ecc5-106">Example</span></span>  
 <span data-ttu-id="3ecc5-107">Následující příklad používá metodu <xref:System.Xml.Linq.XElement.Attribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="3ecc5-108">Tento příklad vyhledá všechny následníky ve stromu s názvem `Phone`a poté vyhledá atribut s názvem `type`.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="3ecc5-109">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3ecc5-109">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="3ecc5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ecc5-110">Example</span></span>  
 <span data-ttu-id="3ecc5-111">Pokud chcete načíst hodnotu atributu, můžete jej přetypovat stejným způsobem jako u objektů <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="3ecc5-112">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-112">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="3ecc5-113">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3ecc5-113">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="3ecc5-114">poskytuje explicitní operátory přetypování pro třídu <xref:System.Xml.Linq.XAttribute> na `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID``GUID?`</span><span class="sxs-lookup"><span data-stu-id="3ecc5-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ecc5-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ecc5-115">Example</span></span>  
 <span data-ttu-id="3ecc5-116">Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3ecc5-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="3ecc5-117">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3ecc5-117">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="3ecc5-118">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3ecc5-118">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ecc5-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ecc5-119">See also</span></span>

- [<span data-ttu-id="3ecc5-120">LINQ to XML osy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ecc5-120">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
