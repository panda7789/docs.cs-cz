---
title: 'Postupy: Provést transformaci textu do souboru XML (C#) pomocí streamování'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 1507c628731a11e06c73f253c1a0c0f9a85a2269
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253527"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Postupy: Provést transformaci textu do souboru XML (C#) pomocí streamování
Jedním z přístupů ke zpracování textového souboru je zápis metody rozšíření, která vytvoří datový soubor v jednom okamžiku pomocí `yield return` konstrukce. Potom můžete napsat dotaz LINQ, který zpracovává textový soubor opožděným odloženým způsobem. Pokud potom použijete <xref:System.Xml.Linq.XStreamingElement> ke streamování výstupu, můžete vytvořit transformaci z textového souboru do formátu XML, který používá minimální množství paměti bez ohledu na velikost zdrojového textového souboru.  
  
 V souvislosti s transformacemi streamování dochází k nějakým aspektům. Transformace streamování se nejlépe používá v situacích, kdy můžete celý soubor zpracovat jednou a pokud můžete řádky zpracovat v pořadí, ve kterém se nachází ve zdrojovém dokumentu. Pokud je třeba soubor zpracovat více než jednou, nebo pokud budete muset řádky seřadit předtím, než je budete moci zpracovat, ztratíte spoustu výhod používání techniky streamování.  
  
## <a name="example"></a>Příklad  
 Následující textový soubor, lidé. txt, je zdrojem tohoto příkladu.  
  
```text  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 Následující kód obsahuje metodu rozšíření, která streamuje řádky textového souboru v odvoditelné podobě.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XStreamingElement>
