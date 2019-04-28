---
title: 'Postupy: Provádění transformací streamovaní textu do XML (C#)'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 906150483f7f76b4429ea390d083e9f18696ac9e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667870"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="23bca-102">Postupy: Provádění transformací streamovaní textu do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="23bca-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>
<span data-ttu-id="23bca-103">Jeden ze způsobů zpracování textového souboru, je zápis metody rozšíření, která jsou streamována textový soubor řádku v čase pomocí `yield return` vytvořit.</span><span class="sxs-lookup"><span data-stu-id="23bca-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="23bca-104">Potom můžete napsat dotaz LINQ, který zpracovává textový soubor opožděné odložené způsobem.</span><span class="sxs-lookup"><span data-stu-id="23bca-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="23bca-105">Pokud použijete <xref:System.Xml.Linq.XStreamingElement> do výstupního datového proudu, pak můžete vytvořit transformace z textového souboru XML, který používá minimální množství paměti, bez ohledu na velikost text souboru zdroje.</span><span class="sxs-lookup"><span data-stu-id="23bca-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>  
  
 <span data-ttu-id="23bca-106">Existují některé upozornění týkající se datového proudu transformace.</span><span class="sxs-lookup"><span data-stu-id="23bca-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="23bca-107">Streamování transformace platí nejlépe v situacích, kde může zpracovat celý soubor po a může zpracovat řádků v pořadí, ve kterém nastávají ve zdrojovém dokumentu.</span><span class="sxs-lookup"><span data-stu-id="23bca-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="23bca-108">Pokud máte více než jednou zpracovat soubor, nebo pokud budete muset seřadit řádky předtím, než dokáže zpracovat, dojde ke ztrátě mnohé z výhod používání technika streamování.</span><span class="sxs-lookup"><span data-stu-id="23bca-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23bca-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="23bca-109">Example</span></span>  
 <span data-ttu-id="23bca-110">Následující textový soubor, People.txt, je zdrojem pro účely tohoto příkladu.</span><span class="sxs-lookup"><span data-stu-id="23bca-110">The following text file, People.txt, is the source for this example.</span></span>  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 <span data-ttu-id="23bca-111">Následující kód obsahuje metody rozšíření, která jsou streamována řádky textového souboru odložené způsobem.</span><span class="sxs-lookup"><span data-stu-id="23bca-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>  
  
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
  
 <span data-ttu-id="23bca-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="23bca-112">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="23bca-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23bca-113">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
- [<span data-ttu-id="23bca-114">Pokročilé techniky dotazování (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="23bca-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
