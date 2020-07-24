---
title: Jak načíst jediný atribut (LINQ to XML) (C#)
description: Naučte se, jak použít LINQ to XML načíst jeden atribut prvku v jazyce C# s ohledem na název atributu.
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4efcae5324ad5a2e4664e68e35e15ec2053daece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103428"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="3aeae-103">Jak načíst jediný atribut (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3aeae-103">How to retrieve a single attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="3aeae-104">Toto téma vysvětluje, jak načíst jediný atribut prvku s ohledem na název atributu.</span><span class="sxs-lookup"><span data-stu-id="3aeae-104">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="3aeae-105">To je užitečné pro psaní výrazů dotazů, kde chcete najít element, který má konkrétní atribut.</span><span class="sxs-lookup"><span data-stu-id="3aeae-105">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="3aeae-106"><xref:System.Xml.Linq.XElement.Attribute%2A>Metoda <xref:System.Xml.Linq.XElement> třídy vrací se <xref:System.Xml.Linq.XAttribute> zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="3aeae-106">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aeae-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="3aeae-107">Example</span></span>  
 <span data-ttu-id="3aeae-108">Následující příklad používá <xref:System.Xml.Linq.XElement.Attribute%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="3aeae-108">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="3aeae-109">Tento příklad vyhledá všechny následníky ve stromu s názvem `Phone` a pak vyhledá atribut s názvem `type` .</span><span class="sxs-lookup"><span data-stu-id="3aeae-109">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="3aeae-110">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3aeae-110">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="3aeae-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="3aeae-111">Example</span></span>  
 <span data-ttu-id="3aeae-112">Chcete-li načíst hodnotu atributu, můžete jej přetypovat stejným způsobem jako u s <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="3aeae-112">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="3aeae-113">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="3aeae-113">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="3aeae-114">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3aeae-114">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="3aeae-115">poskytuje explicitní operátory přetypování pro <xref:System.Xml.Linq.XAttribute> třídu na `string` , `bool` ,,, `bool?` `int` `int?` , `uint` , `uint?` , `long` , `long?` , `ulong` , `ulong?` , `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` , `DateTime` `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,, a.</span><span class="sxs-lookup"><span data-stu-id="3aeae-115">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aeae-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="3aeae-116">Example</span></span>  
 <span data-ttu-id="3aeae-117">Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3aeae-117">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="3aeae-118">Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3aeae-118">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="3aeae-119">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3aeae-119">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="3aeae-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="3aeae-120">See also</span></span>

- [<span data-ttu-id="3aeae-121">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="3aeae-121">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
