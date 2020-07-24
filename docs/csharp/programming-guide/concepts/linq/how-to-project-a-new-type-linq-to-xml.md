---
title: Jak projektovat nový typ (LINQ to XML) (C#)
description: Naučte se vytvářet dotazy v LINQ to XML v jazyce C#, které vracejí IEnumerable <T> typů kromě XElement, String nebo int, které jsou popsány v jiných příkladech.
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 013ea852a64b77c04ac583b4d9b71e8006cd4976
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104645"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="88537-103">Jak projektovat nový typ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="88537-103">How to project a new type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="88537-104">Další příklady v této části obsahují dotazy, které vracejí výsledky od <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> z `string` a do <xref:System.Collections.Generic.IEnumerable%601> `int` .</span><span class="sxs-lookup"><span data-stu-id="88537-104">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="88537-105">Jedná se o běžné typy výsledků, ale nejsou vhodné pro všechny scénáře.</span><span class="sxs-lookup"><span data-stu-id="88537-105">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="88537-106">V mnoha případech budete chtít, aby dotazy vracely <xref:System.Collections.Generic.IEnumerable%601> nějaký jiný typ.</span><span class="sxs-lookup"><span data-stu-id="88537-106">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="88537-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="88537-107">Example</span></span>

<span data-ttu-id="88537-108">Tento příklad ukazuje, jak vytvořit instanci objektů v `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="88537-108">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="88537-109">Kód nejprve definuje novou třídu s konstruktorem a poté upraví `select` příkaz tak, aby výraz byl novou instancí nové třídy.</span><span class="sxs-lookup"><span data-stu-id="88537-109">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="88537-110">Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="88537-110">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

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

<span data-ttu-id="88537-111">Tento příklad používá <xref:System.Xml.Linq.XContainer.Element%2A> metodu, která byla představena v tématu [jak načíst jeden podřízený prvek (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="88537-111">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to retrieve a single child element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="88537-112">Používá také přetypování k načtení hodnot prvků, které jsou vráceny <xref:System.Xml.Linq.XContainer.Element%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="88537-112">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="88537-113">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="88537-113">This example produces the following output:</span></span>

```output
Lawnmower:1
Baby Monitor:2
```
