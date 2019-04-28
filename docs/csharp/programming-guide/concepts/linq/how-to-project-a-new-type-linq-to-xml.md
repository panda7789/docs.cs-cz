---
title: 'Postupy: Projektování nového typu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: eefe645f376f8f52a94b94cdd49640e165a69aae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667857"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="bc8b7-102">Postupy: Projektování nového typu (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bc8b7-102">How to: Project a New Type (LINQ to XML) (C#)</span></span>
<span data-ttu-id="bc8b7-103">Další příklady v této části ukázaly, dotazy, které vracejí výsledky jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string`, a <xref:System.Collections.Generic.IEnumerable%601> z `int`.</span><span class="sxs-lookup"><span data-stu-id="bc8b7-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="bc8b7-104">Toto jsou běžné typy výsledků, ale nejsou vhodná pro každý scénář.</span><span class="sxs-lookup"><span data-stu-id="bc8b7-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="bc8b7-105">V mnoha případech můžete vrátit dotazech <xref:System.Collections.Generic.IEnumerable%601> nějakého jiného typu.</span><span class="sxs-lookup"><span data-stu-id="bc8b7-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc8b7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc8b7-106">Example</span></span>  
 <span data-ttu-id="bc8b7-107">Tento příklad ukazuje, jak vytvořit instanci objektů v `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="bc8b7-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="bc8b7-108">Kód nejdřív definuje novou třídu s konstruktorem a pak změní `select` příkaz tak, aby novou instanci třídy nový výraz.</span><span class="sxs-lookup"><span data-stu-id="bc8b7-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="bc8b7-109">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="bc8b7-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
class NameQty {  
    public string name;  
    public int qty;  
    public NameQty(string n, int q)  
    {  
        name = n;  
        qty = q;  
    }  
};  
  
class Program {  
    public static void Main() {  
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
  
 <span data-ttu-id="bc8b7-110">V tomto příkladu `M:System.Xml.Linq.XElement.Element` metodu, která byla zavedena v tématu [jak: Načtení jednoho podřízeného elementu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bc8b7-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="bc8b7-111">Také používá k načtení hodnoty prvků, které jsou vráceny pomocí přetypování `M:System.Xml.Linq.XElement.Element` metody.</span><span class="sxs-lookup"><span data-stu-id="bc8b7-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="bc8b7-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="bc8b7-112">This example produces the following output:</span></span>  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc8b7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc8b7-113">See also</span></span>

- [<span data-ttu-id="bc8b7-114">Projekce a transformace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bc8b7-114">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
