---
title: 'Postupy: načtení jeden atribut (technologie LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 55da36099af72259a4e72205f142ab855f000c4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321285"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="49cbe-102">Postupy: načtení jeden atribut (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="49cbe-102">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="49cbe-103">Toto téma vysvětluje, jak načíst jeden atribut elementu, název atributu.</span><span class="sxs-lookup"><span data-stu-id="49cbe-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="49cbe-104">To je užitečné pro zápis výrazy dotazů, ve které chcete najít element, který obsahuje konkrétní atribut.</span><span class="sxs-lookup"><span data-stu-id="49cbe-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="49cbe-105"><xref:System.Xml.Linq.XElement.Attribute%2A> Metodu <xref:System.Xml.Linq.XElement> vrací <xref:System.Xml.Linq.XAttribute> se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="49cbe-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49cbe-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="49cbe-106">Example</span></span>  
 <span data-ttu-id="49cbe-107">Následující příklad používá <xref:System.Xml.Linq.XElement.Attribute%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="49cbe-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="49cbe-108">Tento příklad vyhledá všech potomků ve stromové struktuře s názvem `Phone`a pak najde atribut s názvem `type`.</span><span class="sxs-lookup"><span data-stu-id="49cbe-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="49cbe-109">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="49cbe-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="49cbe-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="49cbe-110">Example</span></span>  
 <span data-ttu-id="49cbe-111">Pokud chcete k načtení hodnoty atributu, může odevzdat stejným způsobem jako s <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="49cbe-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="49cbe-112">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="49cbe-112">The following example demonstrates this.</span></span>  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =   
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 <span data-ttu-id="49cbe-113">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="49cbe-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="49cbe-114"> poskytuje explicitní přetypování operátory <xref:System.Xml.Linq.XAttribute> třídy k `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`a `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="49cbe-114"> provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49cbe-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="49cbe-115">Example</span></span>  
 <span data-ttu-id="49cbe-116">Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="49cbe-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="49cbe-117">Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="49cbe-117">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 <span data-ttu-id="49cbe-118">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="49cbe-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="49cbe-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="49cbe-119">See Also</span></span>  
 [<span data-ttu-id="49cbe-120">Technologie LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="49cbe-120">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
