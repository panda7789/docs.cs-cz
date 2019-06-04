---
title: 'Postupy: Načtení jednoho atributu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: cfab2cbb80eb330a5fd745871eb272cca0b37798
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486439"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="4c727-102">Postupy: Načtení jednoho atributu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="4c727-102">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="4c727-103">Toto téma vysvětluje, jak načíst jeden atribut elementu, název atributu.</span><span class="sxs-lookup"><span data-stu-id="4c727-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="4c727-104">To je užitečné pro psaní výrazů dotazů, ve které chcete najít element, který se má určitý atribut.</span><span class="sxs-lookup"><span data-stu-id="4c727-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="4c727-105"><xref:System.Xml.Linq.XElement.Attribute%2A> Metodu <xref:System.Xml.Linq.XElement> třídy vrátí <xref:System.Xml.Linq.XAttribute> se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="4c727-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c727-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c727-106">Example</span></span>  
 <span data-ttu-id="4c727-107">V následujícím příkladu <xref:System.Xml.Linq.XElement.Attribute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4c727-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="4c727-108">Tento příklad vyhledá všechny následníky ve stromové struktuře s názvem `Phone`a následně vyhledá atribut s názvem `type`.</span><span class="sxs-lookup"><span data-stu-id="4c727-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="4c727-109">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4c727-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="4c727-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c727-110">Example</span></span>  
 <span data-ttu-id="4c727-111">Pokud chcete načíst hodnotu atributu, lze jej přetypovat, stejně jako u s <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="4c727-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="4c727-112">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="4c727-112">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="4c727-113">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4c727-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="4c727-114">poskytuje explicitní přetypování operátory pro <xref:System.Xml.Linq.XAttribute> třídu `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`a `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="4c727-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c727-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4c727-115">Example</span></span>  
 <span data-ttu-id="4c727-116">Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4c727-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="4c727-117">Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4c727-117">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="4c727-118">Tento kód vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4c727-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c727-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c727-119">See also</span></span>

- [<span data-ttu-id="4c727-120">Osy LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4c727-120">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
