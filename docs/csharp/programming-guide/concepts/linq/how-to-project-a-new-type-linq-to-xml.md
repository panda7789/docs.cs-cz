---
title: 'Postupy: Projekt a nový typ (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 2bb521d1445dcecdad8b9c7b28bed90e1e38c8e8
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012930"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="ae183-102">Postupy: Projekt a nový typ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ae183-102">How to: Project a New Type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="ae183-103">Další příklady v této části obsahují dotazy, které vracejí <xref:System.Collections.Generic.IEnumerable%601> výsledky `int` <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> od, z `string`a do <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="ae183-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="ae183-104">Jedná se o běžné typy výsledků, ale nejsou vhodné pro všechny scénáře.</span><span class="sxs-lookup"><span data-stu-id="ae183-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="ae183-105">V mnoha případech budete chtít, aby dotazy vracely <xref:System.Collections.Generic.IEnumerable%601> nějaký jiný typ.</span><span class="sxs-lookup"><span data-stu-id="ae183-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="ae183-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae183-106">Example</span></span>

<span data-ttu-id="ae183-107">Tento příklad ukazuje, jak vytvořit instanci objektů v `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ae183-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="ae183-108">Kód nejprve definuje novou třídu s konstruktorem a poté upraví `select` příkaz tak, aby výraz byl novou instancí nové třídy.</span><span class="sxs-lookup"><span data-stu-id="ae183-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="ae183-109">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="ae183-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="ae183-110">Tento příklad používá <xref:System.Xml.Linq.XContainer.Element%2A> metodu, která byla představena v tématu [postupy: Načtení jednoho podřízeného elementu (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ae183-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="ae183-111">Používá také přetypování k načtení hodnot prvků, které jsou vráceny <xref:System.Xml.Linq.XContainer.Element%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="ae183-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="ae183-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ae183-112">This example produces the following output:</span></span>

```console
Lawnmower:1
Baby Monitor:2
```
