---
title: Atomizované objekty XName a Xnamespace (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 0d21397e6885b892f6ac1904e38bd85a78ae07ab
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487595"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Atomizované objekty XName a Xnamespace (LINQ to XML) (C#)
<xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> objekty jsou *atomizované objekty*; to znamená, pokud obsahují stejné kvalifikovaný název, odkazují na stejný objekt. To poskytuje výhody výkon pro dotazy: Při porovnávání rovnosti dvou atomizované objekty názvy základní převodní jazyk má jenom k určení, zda dva odkazy odkazují na stejný objekt. Základní kód nemusí řetězec porovnání, které by byly časově náročné.  
  
## <a name="atomization-semantics"></a>Sémantika atomizace  
 Atomizace znamená, že pokud dva <xref:System.Xml.Linq.XName> objekty mají stejný název místní a jsou ve stejném oboru názvů, sdílejí stejnou instanci. Stejným způsobem, pokud dva <xref:System.Xml.Linq.XNamespace> objekty mají stejný obor názvů URI, které sdílejí stejnou instanci.  
  
 V případě třídy umožňující atomizované objekty objekty musí být konstruktor pro třídu soukromé, není veřejné. Je to proto, že pokud konstruktor public, můžete vytvořit objekt neatomizovaném. <xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> Operátor implicitního převodu k převedení řetězce na implementaci třídy <xref:System.Xml.Linq.XName> nebo <xref:System.Xml.Linq.XNamespace>. To je, jak získat instanci z těchto objektů. Pomocí konstruktoru, nelze získat instanci, protože konstruktor není dostupný.  
  
 <xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> také implementovat operátory rovnosti a nerovnosti, chcete-li zjistit, zda dva objekty porovnávané jsou odkazy na stejnou instanci.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří některé <xref:System.Xml.Linq.XElement> objektů a ukazuje, že stejné názvy sdílet stejnou instanci.  
  
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
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Jak už bylo zmíněno dříve, výhodou atomizované objekty objekty je, že při použití jedné z metod osy, můžou <xref:System.Xml.Linq.XName> jako parametr metody osy má jenom k určení, že dva názvy odkaz na stejnou instanci k výběru požadované prvky.  
  
 Následující příklad předá <xref:System.Xml.Linq.XName> k <xref:System.Xml.Linq.XContainer.Descendants%2A> volání metody, která pak má lepší výkon z důvodu atomizace vzor.  
  
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
