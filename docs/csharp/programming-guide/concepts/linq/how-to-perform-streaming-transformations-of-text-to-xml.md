---
title: "Postupy: provádění streamování transformací textu do formátu XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03c5ed5ef66db311ade751b5aad21de70b78f063
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
