---
title: Atomized XName a XNamespace objekty (LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc5066440d87f5485ae9099d7a7f4f5e9e66b4ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204273"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Atomized XName a XNamespace objekty (LINQ na XML) (C#)
<xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> předměty jsou *rozprášeny*; to znamená, že pokud obsahují stejný kvalifikovaný název, odkazují na stejný objekt. To přináší výhody výkonu pro dotazy: Při porovnání dvou atomized názvy pro rovnost, základní zprostředkující jazyk má pouze k určení, zda dva odkazy odkazují na stejný objekt. Základní kód nemusí provést porovnání řetězců, což by bylo časově náročné.  
  
## <a name="atomization-semantics"></a>Atomizace sémantiku  
 Atomizace znamená, <xref:System.Xml.Linq.XName> že pokud dva objekty mají stejný místní název a jsou ve stejném oboru názvů, sdílejí stejnou instanci. Stejným způsobem, pokud <xref:System.Xml.Linq.XNamespace> dva objekty mají stejný identifikátor URI oboru názvů, sdílejí stejnou instanci.  
  
 Pro třídu povolit atomized objekty konstruktor pro třídu musí být soukromé, nikoli veřejné. Důvodem je, že pokud konstruktor byly veřejné, můžete vytvořit objekt bez rozprašovaného objektu. <xref:System.Xml.Linq.XName> Třídy <xref:System.Xml.Linq.XNamespace> a implementují implicitní operátor <xref:System.Xml.Linq.XName> převodu k převodu řetězce na nebo <xref:System.Xml.Linq.XNamespace>. Tímto způsobem získáte instanci těchto objektů. Nelze získat instanci pomocí konstruktoru, protože konstruktor je nepřístupný.  
  
 <xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> také implementovat operátory rovnosti a nerovnosti, chcete-li určit, zda dva porovnávané objekty jsou odkazy na stejnou instanci.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří <xref:System.Xml.Linq.XElement> některé objekty a ukazuje, že identické názvy sdílejí stejnou instanci.  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 Tento příklad vytváří následující výstup:  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Jak již bylo zmíněno dříve, výhodou atomizovaných objektů je, že <xref:System.Xml.Linq.XName> při použití jedné z metod osy, které berou jako parametr, metoda osy má pouze určit, že dva názvy odkazují na stejnou instanci pro výběr požadovaných prvků.  
  
 Následující příklad předá <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> volání metody, která pak má lepší výkon z důvodu atomizace vzor.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
