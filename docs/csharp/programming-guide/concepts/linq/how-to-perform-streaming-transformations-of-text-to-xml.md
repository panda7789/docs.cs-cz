---
title: 'Postupy: Provést transformaci textu do souboru XML (C#) pomocí streamování'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 6dc48a7342bbeedb79e8e7f4a9270899be336f91
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851033"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="a55b7-102">Postupy: Provést transformaci textu do souboru XML (C#) pomocí streamování</span><span class="sxs-lookup"><span data-stu-id="a55b7-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>

<span data-ttu-id="a55b7-103">Jedním z přístupů ke zpracování textového souboru je zápis metody rozšíření, která vytvoří datový soubor v jednom okamžiku pomocí `yield return` konstrukce.</span><span class="sxs-lookup"><span data-stu-id="a55b7-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="a55b7-104">Potom můžete napsat dotaz LINQ, který zpracovává textový soubor opožděným odloženým způsobem.</span><span class="sxs-lookup"><span data-stu-id="a55b7-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="a55b7-105">Pokud potom použijete <xref:System.Xml.Linq.XStreamingElement> ke streamování výstupu, můžete vytvořit transformaci z textového souboru do formátu XML, který používá minimální množství paměti bez ohledu na velikost zdrojového textového souboru.</span><span class="sxs-lookup"><span data-stu-id="a55b7-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

 <span data-ttu-id="a55b7-106">V souvislosti s transformacemi streamování dochází k nějakým aspektům.</span><span class="sxs-lookup"><span data-stu-id="a55b7-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="a55b7-107">Transformace streamování se nejlépe používá v situacích, kdy můžete celý soubor zpracovat jednou a pokud můžete řádky zpracovat v pořadí, ve kterém se nachází ve zdrojovém dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a55b7-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="a55b7-108">Pokud je třeba soubor zpracovat více než jednou, nebo pokud budete muset řádky seřadit předtím, než je budete moci zpracovat, ztratíte spoustu výhod používání techniky streamování.</span><span class="sxs-lookup"><span data-stu-id="a55b7-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>

## <a name="example"></a><span data-ttu-id="a55b7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a55b7-109">Example</span></span>

 <span data-ttu-id="a55b7-110">Následující textový soubor, lidé. txt, je zdrojem tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="a55b7-110">The following text file, People.txt, is the source for this example.</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 <span data-ttu-id="a55b7-111">Následující kód obsahuje metodu rozšíření, která streamuje řádky textového souboru v odvoditelné podobě.</span><span class="sxs-lookup"><span data-stu-id="a55b7-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>

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

 <span data-ttu-id="a55b7-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a55b7-112">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a55b7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a55b7-113">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
