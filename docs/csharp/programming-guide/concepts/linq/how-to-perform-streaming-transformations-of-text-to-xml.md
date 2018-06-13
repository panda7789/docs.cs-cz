---
title: 'Postupy: provádění streamování transformací textu do formátu XML (C#)'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 4313c5263b6a219ec3c8d05a7b7938c41c7cc028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328185"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Postupy: provádění streamování transformací textu do formátu XML (C#)
Jeden ze způsobů zpracování textového souboru je zápis metody rozšíření, která datové proudy textového souboru řádku na čas pomocí `yield return` vytvořit. Potom můžete napsat dotaz LINQ, který zpracovává textový soubor opožděné odložené způsobem. Pokud pak použijete <xref:System.Xml.Linq.XStreamingElement> do výstupního datového proudu, potom můžete vytvořit transformace z textového souboru na kód XML, který používá minimální množství paměti, bez ohledu na velikost zdroj textového souboru.  
  
 Existují některá upozornění týkající se datového proudu transformace. Streamování transformace je nejvhodnější použít v situacích, kde můžete zpracovat celý soubor po, a pokud může zpracovat řádků v pořadí, ve kterém nastávají ve zdrojovém dokumentu. Pokud máte více než jednou zpracovat soubor nebo pokud máte k seřazení řádků, než při jejich zpracování, ztratíte řadu výhod technikou streamování.  
  
## <a name="example"></a>Příklad  
 Následující textový soubor, People.txt, je zdrojem v tomto příkladu.  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 Následující kód obsahuje metody rozšíření, která datové proudy řádky textu souboru odložené způsobem.  
  
```csharp  
public static class StreamReaderSequence  
{  
    public static IEnumerable<string> Lines(this StreamReader source)  
    {  
        String line;  
  
        if (source == null)  
            throw new ArgumentNullException("source");  
        while ((line = source.ReadLine()) != null)  
        {  
            yield return line;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        StreamReader sr = new StreamReader("People.txt");  
        XStreamingElement xmlTree = new XStreamingElement("Root",  
            from line in sr.Lines()  
            let items = line.Split(',')  
            where !line.StartsWith("#")  
            select new XElement("Person",  
                       new XAttribute("ID", items[0]),  
                       new XElement("First", items[1]),  
                       new XElement("Last", items[2]),  
                       new XElement("Occupation", items[3])  
                   )  
        );  
        Console.WriteLine(xmlTree);  
        sr.Close();  
    }  
}  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<Root>  
  <Person ID="1">  
    <First>Tai</First>  
    <Last>Yee</Last>  
    <Occupation>Writer</Occupation>  
  </Person>  
  <Person ID="2">  
    <First>Nikolay</First>  
    <Last>Grachev</Last>  
    <Occupation>Programmer</Occupation>  
  </Person>  
  <Person ID="3">  
    <First>David</First>  
    <Last>Wright</Last>  
    <Occupation>Inventor</Occupation>  
  </Person>  
</Root>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Linq.XStreamingElement>  
 [Pokročilé techniky dotazu (technologie LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
