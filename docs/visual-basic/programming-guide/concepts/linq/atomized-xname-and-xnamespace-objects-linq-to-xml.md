---
title: Atomizované objekty XName a XNamespace (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: 6a94bc0f2fd8013997e233b300fa19c12671bf29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383686"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Atomované XName a objekty XNamespace (LINQ to XML) (Visual Basic)

<xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> objekty jsou *atomické*; to znamená, že pokud obsahují stejný kvalifikovaný název, odkazují na stejný objekt. To má vliv na výkon pro dotazy: Když porovnáte dva atomické názvy pro rovnost, má základní zprostředkující jazyk pouze určit, zda dva odkazy odkazují na stejný objekt. Podkladový kód nemusí provádět porovnávání řetězců, což by mohlo být časově náročné.

## <a name="atomization-semantics"></a>Sémantika atoming

Atoming znamená, že pokud <xref:System.Xml.Linq.XName> mají dva objekty stejný místní název a jsou ve stejném oboru názvů, sdílejí stejnou instanci. Stejným způsobem, pokud <xref:System.Xml.Linq.XNamespace> mají dva objekty stejný identifikátor URI oboru názvů, sdílejí stejnou instanci.

Pro třídu, která povoluje atomované objekty, konstruktor třídy musí být privátní, nikoli Public. Důvodem je, že pokud byl konstruktor veřejný, mohli byste vytvořit neatomické objekty. <xref:System.Xml.Linq.XName>Třídy a <xref:System.Xml.Linq.XNamespace> implementují implicitní operátor převodu pro převod řetězce na <xref:System.Xml.Linq.XName> nebo <xref:System.Xml.Linq.XNamespace> . Tímto způsobem získáte instanci těchto objektů. Nelze získat instanci pomocí konstruktoru, protože konstruktor je nepřístupný.

<xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> také implementujte operátory rovnosti a nerovnosti, abyste zjistili, zda jsou dva porovnávané objekty odkazy na stejnou instanci.

## <a name="example"></a>Příklad

Následující kód vytvoří některé <xref:System.Xml.Linq.XElement> objekty a demonstruje, že stejné názvy sdílejí stejnou instanci.

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

```console
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

Jak bylo zmíněno dříve, výhodou objektů Atom je, že pokud použijete jednu z metod osy, která přijímá <xref:System.Xml.Linq.XName> jako parametr, metoda Axis má pouze určit, že dva názvy odkazují na stejnou instanci, aby vybraly požadované prvky.

Následující příklad předává <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> volání metody, které pak má lepší výkon, protože se jedná o model atoming.

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

## <a name="see-also"></a>Viz také

- [Výkon (LINQ to XML) (Visual Basic)](performance-linq-to-xml.md)
