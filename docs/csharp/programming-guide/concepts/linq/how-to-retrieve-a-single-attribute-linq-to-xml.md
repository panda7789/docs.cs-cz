---
title: 'Postupy: Načtení jednoho atributu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4a1be51c7f0e89a8f211ae523eb102282bd9747b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592651"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="693ca-102">Postupy: Načtení jednoho atributu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="693ca-102">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="693ca-103">Toto téma vysvětluje, jak načíst jediný atribut prvku s ohledem na název atributu.</span><span class="sxs-lookup"><span data-stu-id="693ca-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="693ca-104">To je užitečné pro psaní výrazů dotazů, kde chcete najít element, který má konkrétní atribut.</span><span class="sxs-lookup"><span data-stu-id="693ca-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="693ca-105"><xref:System.Xml.Linq.XElement.Attribute%2A> Metoda třídy<xref:System.Xml.Linq.XElement> vrací se<xref:System.Xml.Linq.XAttribute> zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="693ca-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="693ca-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="693ca-106">Example</span></span>  
 <span data-ttu-id="693ca-107">Následující příklad používá <xref:System.Xml.Linq.XElement.Attribute%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="693ca-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="693ca-108">Tento příklad vyhledá všechny následníky ve stromu s názvem `Phone`a pak vyhledá atribut s názvem `type`.</span><span class="sxs-lookup"><span data-stu-id="693ca-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="693ca-109">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="693ca-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="693ca-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="693ca-110">Example</span></span>  
 <span data-ttu-id="693ca-111">Chcete-li načíst hodnotu atributu, můžete jej přetypovat stejným způsobem jako u s <xref:System.Xml.Linq.XElement> objekty.</span><span class="sxs-lookup"><span data-stu-id="693ca-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="693ca-112">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="693ca-112">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="693ca-113">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="693ca-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="693ca-114">poskytuje explicitní operátory přetypování pro <xref:System.Xml.Linq.XAttribute> třídu na `string`, `bool`, `bool?` `int` `uint`,, ,,`uint?` ,`long`, ,`long?` `int?` `ulong`, `ulong?`, ,,`double`, ,`TimeSpan?`,,, ,`DateTime?`,, a`GUID` `decimal?` `double?` `decimal` `float?` `float` `DateTime` `TimeSpan`  `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="693ca-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="693ca-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="693ca-115">Example</span></span>  
 <span data-ttu-id="693ca-116">Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="693ca-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="693ca-117">Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="693ca-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="693ca-118">Tento kód generuje následující výstup:</span><span class="sxs-lookup"><span data-stu-id="693ca-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="693ca-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="693ca-119">See also</span></span>

- [<span data-ttu-id="693ca-120">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="693ca-120">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
