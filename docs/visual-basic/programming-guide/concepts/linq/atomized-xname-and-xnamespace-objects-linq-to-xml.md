---
title: Atomizované objekty XName a Xnamespace (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: fe0c4429c89e0028b3b012c87684bd14048de27a
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843439"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Atomizované objekty XName a Xnamespace (LINQ to XML) (Visual Basic)

<xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> objekty jsou *atomizované objekty*; to znamená, pokud obsahují stejné kvalifikovaný název, odkazují na stejný objekt. To poskytuje výhody výkon pro dotazy: Při porovnávání rovnosti dvou atomizované objekty názvy základní převodní jazyk má jenom k určení, zda dva odkazy odkazují na stejný objekt. Základní kód nemusí řetězec porovnání, které by byly časově náročné.

## <a name="atomization-semantics"></a>Sémantika atomizace

Atomizace znamená, že pokud dva <xref:System.Xml.Linq.XName> objekty mají stejný název místní a jsou ve stejném oboru názvů, sdílejí stejnou instanci. Stejným způsobem, pokud dva <xref:System.Xml.Linq.XNamespace> objekty mají stejný obor názvů URI, které sdílejí stejnou instanci.

V případě třídy umožňující atomizované objekty objekty musí být konstruktor pro třídu soukromé, není veřejné. Je to proto, že pokud konstruktor public, můžete vytvořit objekt neatomizovaném. <xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> Operátor implicitního převodu k převedení řetězce na implementaci třídy <xref:System.Xml.Linq.XName> nebo <xref:System.Xml.Linq.XNamespace>. To je, jak získat instanci z těchto objektů. Pomocí konstruktoru, nelze získat instanci, protože konstruktor není dostupný.

<xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> také implementovat operátory rovnosti a nerovnosti, chcete-li zjistit, zda dva objekty porovnávané jsou odkazy na stejnou instanci.

## <a name="example"></a>Příklad

Následující kód vytvoří některé <xref:System.Xml.Linq.XElement> objektů a ukazuje, že stejné názvy sdílet stejnou instanci.

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

Tento příklad vytvoří následující výstup:

```
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

Jak už bylo zmíněno dříve, výhodou atomizované objekty objekty je, že při použití jedné z metod osy, můžou <xref:System.Xml.Linq.XName> jako parametr metody osy má jenom k určení, že dva názvy odkaz na stejnou instanci k výběru požadované prvky.

Následující příklad předá <xref:System.Xml.Linq.XName> k <xref:System.Xml.Linq.XContainer.Descendants%2A> volání metody, která pak má lepší výkon z důvodu atomizace vzor.

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

Tento příklad vytvoří následující výstup:

```xml
<C1>1</C1>
<C1>1</C1>
```

## <a name="see-also"></a>Viz také:

- [Výkon (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
