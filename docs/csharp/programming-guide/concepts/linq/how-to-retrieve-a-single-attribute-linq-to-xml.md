---
title: Jak načíst jeden atribut (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 830a7be24702b6037ac62471060fbe49d8ded598
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168710"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="83a41-102">Jak načíst jeden atribut (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="83a41-102">How to retrieve a single attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="83a41-103">Toto téma vysvětluje, jak načíst jeden atribut prvku, vzhledem k názvu atributu.</span><span class="sxs-lookup"><span data-stu-id="83a41-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="83a41-104">To je užitečné pro psaní výrazů dotazu, kde chcete najít prvek, který má určitý atribut.</span><span class="sxs-lookup"><span data-stu-id="83a41-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="83a41-105">Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> třídy <xref:System.Xml.Linq.XElement> vrátí <xref:System.Xml.Linq.XAttribute> se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="83a41-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83a41-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="83a41-106">Example</span></span>  
 <span data-ttu-id="83a41-107">Následující příklad používá <xref:System.Xml.Linq.XElement.Attribute%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="83a41-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="83a41-108">Tento příklad vyhledá všechny potomky `Phone`ve stromu s `type`názvem a potom najde atribut s názvem .</span><span class="sxs-lookup"><span data-stu-id="83a41-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="83a41-109">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="83a41-109">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="83a41-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="83a41-110">Example</span></span>  
 <span data-ttu-id="83a41-111">Pokud chcete načíst hodnotu atributu, můžete ho přetypovat, <xref:System.Xml.Linq.XElement> stejně jako u objektů.</span><span class="sxs-lookup"><span data-stu-id="83a41-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="83a41-112">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="83a41-112">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="83a41-113">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="83a41-113">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="83a41-114">poskytuje explicitní operátory <xref:System.Xml.Linq.XAttribute> přetypážení `int?` `uint`pro `uint?`třídu `ulong` `ulong?`do `float` `float?` `double` `double?` `decimal` `decimal?` `string`, `bool` `bool?`, `int`, , , , `GUID?` `long` `long?`, , , , , , , , `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, , a .</span><span class="sxs-lookup"><span data-stu-id="83a41-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83a41-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="83a41-115">Example</span></span>  
 <span data-ttu-id="83a41-116">Následující příklad ukazuje stejný kód pro atribut, který je v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="83a41-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="83a41-117">Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="83a41-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="83a41-118">Výsledkem tohoto kódu je následující výstup:</span><span class="sxs-lookup"><span data-stu-id="83a41-118">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="83a41-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="83a41-119">See also</span></span>

- [<span data-ttu-id="83a41-120">LINQ na osy XML (C#)</span><span class="sxs-lookup"><span data-stu-id="83a41-120">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
