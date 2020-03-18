---
title: Jak provádět streamování transformace textu do XML (C#)
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 496535b7f868095a62be2b72b1eea2b082e00a44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345799"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Jak provádět streamování transformace textu do XML (C#)

Jedním z přístupů ke zpracování textového souboru je napsat metodu rozšíření, `yield return` která streamuje textový soubor řádek najednou pomocí konstrukce. Potom můžete napsat dotaz LINQ, který zpracovává textový soubor opožděně odložené způsobem. Pokud pak <xref:System.Xml.Linq.XStreamingElement> použijete k streamování výstupu, můžete vytvořit transformaci z textového souboru do xml, který používá minimální množství paměti, bez ohledu na velikost zdrojového textového souboru.

 Existují některé námitky týkající se streamování transformace. Transformace streamování je nejvhodnější v situacích, kdy můžete zpracovat celý soubor jednou a pokud můžete zpracovat řádky v pořadí, ve kterém se vyskytují ve zdrojovém dokumentu. Pokud máte zpracovat soubor více než jednou, nebo pokud budete muset třídit řádky před jejich zpracováním, ztratíte mnoho výhod použití datového proudu techniky.

## <a name="example"></a>Příklad

 Následující textový soubor, People.txt, je zdrojem pro tento příklad.

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 Následující kód obsahuje metodu rozšíření, která streamuje řádky textového souboru odloženým způsobem.

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
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
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
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

 Tento příklad vytváří následující výstup:

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
