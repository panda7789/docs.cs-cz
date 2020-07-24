---
title: Atomované XName a objekty XNamespace (LINQ to XML) (C#)
description: Přečtěte si o atomicky XName a XNamespace objektech a o tom, jak poskytují výkonnostní výhody pro dotazy.
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 305a233adab5c860b5f9509ae25ccc5d633e7957
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104278"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Atomované XName a objekty XNamespace (LINQ to XML) (C#)
<xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> objekty jsou *atomické*; to znamená, že pokud obsahují stejný kvalifikovaný název, odkazují na stejný objekt. To má vliv na výkon pro dotazy: Když porovnáte dva atomické názvy pro rovnost, má základní zprostředkující jazyk pouze určit, zda dva odkazy odkazují na stejný objekt. Podkladový kód nemusí provádět porovnávání řetězců, což by mohlo být časově náročné.  
  
## <a name="atomization-semantics"></a>Sémantika atoming  
 Atoming znamená, že pokud <xref:System.Xml.Linq.XName> mají dva objekty stejný místní název a jsou ve stejném oboru názvů, sdílejí stejnou instanci. Stejným způsobem, pokud <xref:System.Xml.Linq.XNamespace> mají dva objekty stejný identifikátor URI oboru názvů, sdílejí stejnou instanci.  
  
 Pro třídu, která povoluje atomované objekty, konstruktor třídy musí být privátní, nikoli Public. Důvodem je, že pokud byl konstruktor veřejný, mohli byste vytvořit neatomické objekty. <xref:System.Xml.Linq.XName>Třídy a <xref:System.Xml.Linq.XNamespace> implementují implicitní operátor převodu pro převod řetězce na <xref:System.Xml.Linq.XName> nebo <xref:System.Xml.Linq.XNamespace> . Tímto způsobem získáte instanci těchto objektů. Nelze získat instanci pomocí konstruktoru, protože konstruktor je nepřístupný.  
  
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
  
 Následující příklad předává <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> volání metody, které pak má lepší výkon, protože se jedná o model atoming.  
  
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
