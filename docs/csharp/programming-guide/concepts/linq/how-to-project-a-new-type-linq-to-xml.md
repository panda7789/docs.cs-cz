---
title: Jak projektovat nový typ (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 3a54677fa0fa2845dd635f89ddb7ed1c5c279e03
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345723"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="539a9-102">Jak projektovat nový typ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="539a9-102">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="539a9-103">Další příklady v této části obsahují dotazy, které vracejí výsledky jako <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> `string`a <xref:System.Collections.Generic.IEnumerable%601> `int`.</span><span class="sxs-lookup"><span data-stu-id="539a9-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="539a9-104">Jedná se o běžné typy výsledků, ale nejsou vhodné pro všechny scénáře.</span><span class="sxs-lookup"><span data-stu-id="539a9-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="539a9-105">V mnoha případech budete chtít, aby dotazy vracely <xref:System.Collections.Generic.IEnumerable%601> nějakého jiného typu.</span><span class="sxs-lookup"><span data-stu-id="539a9-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="539a9-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="539a9-106">Example</span></span>

<span data-ttu-id="539a9-107">Tento příklad ukazuje, jak vytvořit instanci objektů v klauzuli `select`.</span><span class="sxs-lookup"><span data-stu-id="539a9-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="539a9-108">Kód nejprve definuje novou třídu s konstruktorem a poté upraví příkaz `select` tak, aby výraz byl novou instancí nové třídy.</span><span class="sxs-lookup"><span data-stu-id="539a9-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="539a9-109">Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="539a9-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="539a9-110">Tento příklad používá metodu <xref:System.Xml.Linq.XContainer.Element%2A>, která byla představena v tématu [jak načíst jeden podřízený prvek (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="539a9-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="539a9-111">Používá také přetypování k načtení hodnot prvků, které jsou vráceny metodou <xref:System.Xml.Linq.XContainer.Element%2A>.</span><span class="sxs-lookup"><span data-stu-id="539a9-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="539a9-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="539a9-112">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
