---
title: Atomované XName a objekty XNamespace (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc5066440d87f5485ae9099d7a7f4f5e9e66b4ec
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204273"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Atomované XName a objekty XNamespace (LINQ to XML) (C#)
<xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> objekty jsou *atomické*; to znamená, že pokud obsahují stejný kvalifikovaný název, odkazují na stejný objekt. To má za důsledek přínos pro dotazy: Když porovnáte dva atomické názvy pro rovnost, má základní zprostředkující jazyk pouze určit, zda dva odkazy odkazují na stejný objekt. Podkladový kód nemusí provádět porovnávání řetězců, což by mohlo být časově náročné.  
  
## <a name="atomization-semantics"></a>Sémantika atoming  
 Atoming znamená, že pokud <xref:System.Xml.Linq.XName> mají dva objekty stejný místní název a jsou ve stejném oboru názvů, sdílejí stejnou instanci. Stejným způsobem, pokud mají dva <xref:System.Xml.Linq.XNamespace> objekty stejný identifikátor URI oboru názvů, sdílejí stejnou instanci.  
  
 Pro třídu, která povoluje atomované objekty, konstruktor třídy musí být privátní, nikoli Public. Důvodem je, že pokud byl konstruktor veřejný, mohli byste vytvořit neatomické objekty. <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace>Třídy a <xref:System.Xml.Linq.XNamespace>implementují implicitní operátor převodu pro převod řetězce na nebo. <xref:System.Xml.Linq.XName> Tímto způsobem získáte instanci těchto objektů. Nelze získat instanci pomocí konstruktoru, protože konstruktor je nepřístupný.  
  
 <xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> také implementujte operátory rovnosti a nerovnosti, abyste zjistili, zda jsou dva porovnávané objekty odkazy na stejnou instanci.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří některé <xref:System.Xml.Linq.XElement> objekty a demonstruje, že stejné názvy sdílejí stejnou instanci.  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Jak bylo zmíněno dříve, výhodou objektů Atom je, že pokud použijete jednu z metod osy, která přijímá <xref:System.Xml.Linq.XName> jako parametr, metoda Axis má pouze určit, že dva názvy odkazují na stejnou instanci, aby vybraly požadované prvky.  
  
 Následující příklad předává volání <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> metody, které pak má lepší výkon, protože se jedná o model atoming.  
  
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
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
