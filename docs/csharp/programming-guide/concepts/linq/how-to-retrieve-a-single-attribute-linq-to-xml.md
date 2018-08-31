---
title: 'Postupy: Načtení jednoho atributu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 55da36099af72259a4e72205f142ab855f000c4f
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43252782"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="c5de7-102">Postupy: Načtení jednoho atributu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c5de7-102">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="c5de7-103">Toto téma vysvětluje, jak načíst jeden atribut elementu, název atributu.</span><span class="sxs-lookup"><span data-stu-id="c5de7-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="c5de7-104">To je užitečné pro psaní výrazů dotazů, ve které chcete najít element, který se má určitý atribut.</span><span class="sxs-lookup"><span data-stu-id="c5de7-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="c5de7-105"><xref:System.Xml.Linq.XElement.Attribute%2A> Metodu <xref:System.Xml.Linq.XElement> třídy vrátí <xref:System.Xml.Linq.XAttribute> se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="c5de7-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5de7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5de7-106">Example</span></span>  
 <span data-ttu-id="c5de7-107">V následujícím příkladu <xref:System.Xml.Linq.XElement.Attribute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c5de7-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="c5de7-108">Tento příklad vyhledá všechny následníky ve stromové struktuře s názvem `Phone`a následně vyhledá atribut s názvem `type`.</span><span class="sxs-lookup"><span data-stu-id="c5de7-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="c5de7-109">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c5de7-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="c5de7-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5de7-110">Example</span></span>  
 <span data-ttu-id="c5de7-111">Pokud chcete načíst hodnotu atributu, lze jej přetypovat, stejně jako u s <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="c5de7-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="c5de7-112">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="c5de7-112">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="c5de7-113">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c5de7-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c5de7-114"> poskytuje explicitní přetypování operátory pro <xref:System.Xml.Linq.XAttribute> třídu `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`a `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="c5de7-114"> provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5de7-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5de7-115">Example</span></span>  
 <span data-ttu-id="c5de7-116">Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c5de7-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="c5de7-117">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="c5de7-117">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="c5de7-118">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c5de7-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5de7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5de7-119">See Also</span></span>  
 [<span data-ttu-id="c5de7-120">Osy LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c5de7-120">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
