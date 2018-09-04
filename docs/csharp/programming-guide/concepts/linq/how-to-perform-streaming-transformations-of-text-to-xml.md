---
title: 'Postupy: provádění transformací streamovaní textu do XML (C#)'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 98fa8bd9ae393e9c87b67ae3f2874a2c279415af
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526944"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Postupy: provádění transformací streamovaní textu do XML (C#)
Jeden ze způsobů zpracování textového souboru, je zápis metody rozšíření, která jsou streamována textový soubor řádku v čase pomocí `yield return` vytvořit. Potom můžete napsat dotaz LINQ, který zpracovává textový soubor opožděné odložené způsobem. Pokud použijete <xref:System.Xml.Linq.XStreamingElement> do výstupního datového proudu, pak můžete vytvořit transformace z textového souboru XML, který používá minimální množství paměti, bez ohledu na velikost text souboru zdroje.  
  
 Existují některé upozornění týkající se datového proudu transformace. Streamování transformace platí nejlépe v situacích, kde může zpracovat celý soubor po a může zpracovat řádků v pořadí, ve kterém nastávají ve zdrojovém dokumentu. Pokud máte více než jednou zpracovat soubor, nebo pokud budete muset seřadit řádky předtím, než dokáže zpracovat, dojde ke ztrátě mnohé z výhod používání technika streamování.  
  
## <a name="example"></a>Příklad  
 Následující textový soubor, People.txt, je zdrojem pro účely tohoto příkladu.  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 Následující kód obsahuje metody rozšíření, která jsou streamována řádky textového souboru odložené způsobem.  
  
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

- <xref:System.Xml.Linq.XStreamingElement>  
- [Pokročilé techniky dotazování (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
