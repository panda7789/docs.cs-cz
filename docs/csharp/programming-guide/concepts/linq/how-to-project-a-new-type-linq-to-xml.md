---
title: Jak promítnout nový typ (LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 5205a0c56651271dea0181ed96518c0e9d7f95f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168990"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="5c924-102">Jak promítnout nový typ (LINQ na XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="5c924-102">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="5c924-103">Další příklady v této části ukázaly dotazy, které `string`vracejí <xref:System.Collections.Generic.IEnumerable%601> `int`výsledky <xref:System.Collections.Generic.IEnumerable%601> od , <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> z , a .</span><span class="sxs-lookup"><span data-stu-id="5c924-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="5c924-104">Jedná se o běžné typy výsledků, ale nejsou vhodné pro každý scénář.</span><span class="sxs-lookup"><span data-stu-id="5c924-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="5c924-105">V mnoha případech budete chtít, aby <xref:System.Collections.Generic.IEnumerable%601> vaše dotazy vrátit jiný typ.</span><span class="sxs-lookup"><span data-stu-id="5c924-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="5c924-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c924-106">Example</span></span>

<span data-ttu-id="5c924-107">Tento příklad ukazuje, jak vytvořit instanci objektů v `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="5c924-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="5c924-108">Kód nejprve definuje novou třídu s konstruktorem a `select` poté upraví příkaz tak, aby výraz byl novou instancí nové třídy.</span><span class="sxs-lookup"><span data-stu-id="5c924-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="5c924-109">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Typický nákupní objednávka (LINQ to XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)</span><span class="sxs-lookup"><span data-stu-id="5c924-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
        XElement po = XElement.Load("PurchaseOrder.xml");
  
        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );
  
        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

<span data-ttu-id="5c924-110">Tento příklad <xref:System.Xml.Linq.XContainer.Element%2A> používá metodu, která byla zavedena v tématu [Jak načíst jeden podřízený prvek (LINQ do XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5c924-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="5c924-111">Používá také přetypování k načtení hodnot prvků, <xref:System.Xml.Linq.XContainer.Element%2A> které jsou vráceny metodou.</span><span class="sxs-lookup"><span data-stu-id="5c924-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="5c924-112">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5c924-112">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
