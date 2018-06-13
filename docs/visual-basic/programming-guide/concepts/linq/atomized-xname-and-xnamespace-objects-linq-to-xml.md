---
title: Atomized XName a XNamespace objekty (technologie LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: e311de901a9a54bd4fc6ee56d425cc16b4978e8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643270"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Atomized XName a XNamespace objekty (technologie LINQ to XML) (Visual Basic)
<xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> objekty jsou *atomized*; to znamená, pokud obsahují stejný kvalifikovaný název, se vztahují ke stejnému objektu. Dostaneme výkonnostních výhod pro dotazy: při porovnávání rovnosti dvou atomized názvy základní převodní jazyk má jenom k určení, zda dva odkazy odkazují na stejný objekt. Kód základní nemusí řetězec porovnání, které by byly časově náročná.  
  
## <a name="atomization-semantics"></a>Sémantika atomizace  
 Atomizace znamená, že pokud dva <xref:System.Xml.Linq.XName> objekty mají stejnou místní název a jsou ve stejném oboru názvů, sdílejí stejnou instanci. Stejným způsobem, pokud dva <xref:System.Xml.Linq.XNamespace> objekty mají stejný obor názvů URI, které sdílejí stejnou instanci.  
  
 Pro třídu povolit atomized objekty musí být v konstruktoru pro třídu privátní, není veřejné. Je to proto, pokud byly veřejný konstruktor, můžete vytvořit objekt neatomizovaném. <xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> operátor implicitní převod převést řetězec do implementace třídy <xref:System.Xml.Linq.XName> nebo <xref:System.Xml.Linq.XNamespace>. Toto je, jak získat instanci tyto objekty. Pomocí konstruktoru, nelze získat instanci, protože konstruktoru je nedostupná.  
  
 <xref:System.Xml.Linq.XName> a <xref:System.Xml.Linq.XNamespace> taky implementovat operátory rovnosti a nerovnosti k určení, zda dva objekty porovnávané jsou odkazy na stejnou instanci.  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří některé <xref:System.Xml.Linq.XElement> objekty a ukazuje, že identické názvy sdílet stejnou instanci.  
  
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
  
 Jak už bylo zmíněno dříve, výhodou atomized objektů je, že když použijete jednu z metod osy, které berou <xref:System.Xml.Linq.XName> jako parametr, metoda osy má jenom k určení, že dva názvy odkaz na stejnou instanci a vyberte požadované prvky.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Výkon (technologie LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
