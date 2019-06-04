---
title: 'Postupy: Projektování nového typu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 70053a2457005f6751075b33e8e49851d7127446
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486580"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Postupy: Projektování nového typu (LINQ to XML) (C#)
Další příklady v této části ukázaly, dotazy, které vracejí výsledky jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> z `string`, a <xref:System.Collections.Generic.IEnumerable%601> z `int`. Toto jsou běžné typy výsledků, ale nejsou vhodná pro každý scénář. V mnoha případech můžete vrátit dotazech <xref:System.Collections.Generic.IEnumerable%601> nějakého jiného typu.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak vytvořit instanci objektů v `select` klauzuli. Kód nejdřív definuje novou třídu s konstruktorem a pak změní `select` příkaz tak, aby novou instanci třídy nový výraz.  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
  
 V tomto příkladu `M:System.Xml.Linq.XElement.Element` metodu, která byla zavedena v tématu [jak: Načtení jednoho podřízeného elementu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Také používá k načtení hodnoty prvků, které jsou vráceny pomocí přetypování `M:System.Xml.Linq.XElement.Element` metody.  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  