---
title: Hledání textu v dokumentech aplikace Word (C#)
ms.date: 07/20/2015
ms.assetid: 82f86677-560b-49dc-a089-610409939b2a
ms.openlocfilehash: 173472b9dbd669476c3e5529655d111b88b0dba2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70205397"
---
# <a name="finding-text-in-word-documents-c"></a><span data-ttu-id="51413-102">Hledání textu v dokumentech aplikace Word (C#)</span><span class="sxs-lookup"><span data-stu-id="51413-102">Finding Text in Word Documents (C#)</span></span>
<span data-ttu-id="51413-103">Toto téma rozšiřuje předchozí dotazy dělat něco užitečného: najít všechny výskyty řetězce v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="51413-103">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51413-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="51413-104">Example</span></span>  
 <span data-ttu-id="51413-105">Tento příklad zpracovává wordprocessingML dokumentu, najít všechny výskyty určité části textu v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="51413-105">This example processes a WordprocessingML document, to find all the occurrences of a specific piece of text in the document.</span></span> <span data-ttu-id="51413-106">Chcete-li to provést, použijeme dotaz, který najde řetězec "Hello".</span><span class="sxs-lookup"><span data-stu-id="51413-106">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="51413-107">Tento příklad vychází z předchozích příkladů v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="51413-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="51413-108">Nový dotaz je volán v komentářích v níže uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="51413-108">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="51413-109">Pokyny k vytvoření zdrojového dokumentu pro tento příklad naleznete [v tématu Vytvoření dokumentu Open XML (C#) zdrojové sady Office](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="51413-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="51413-110">Tento příklad používá třídy nalezené v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="51413-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="51413-111">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="51413-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace =  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        XDocument xDoc = null;  
        XDocument styleDoc = null;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
                  docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                if (styleRelation != null)  
                {  
                    Uri styleUri =  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
                      (string)style.Attribute(w + "default") == "1"  
                select style  
            ).First().Attribute(w + "styleId");  
  
        // Find all paragraphs in the document.  
        var paragraphs =  
            from para in xDoc  
                         .Root  
                         .Element(w + "body")  
                         .Descendants(w + "p")  
            let styleNode = para  
                            .Elements(w + "pPr")  
                            .Elements(w + "pStyle")  
                            .FirstOrDefault()  
            select new  
            {  
                ParagraphNode = para,  
                StyleName = styleNode != null ?  
                    (string)styleNode.Attribute(w + "val") :  
                    defaultStyle  
            };  
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        // Following is the new query that retrieves all paragraphs  
        // that have specific text in them.  
        var helloParagraphs =  
            from para in paraWithText  
            where para.Text.Contains("Hello")  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para.Text  
            };  
  
        foreach (var p in helloParagraphs)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="51413-112">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="51413-112">This example produces the following output:</span></span>  
  
```output  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="51413-113">Můžete samozřejmě upravit vyhledávání tak, aby vyhledává řádky s určitým stylem.</span><span class="sxs-lookup"><span data-stu-id="51413-113">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="51413-114">Následující dotaz vyhledá všechny prázdné řádky, které mají styl Kód:</span><span class="sxs-lookup"><span data-stu-id="51413-114">The following query finds all blank lines that have the Code style:</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        XDocument xDoc = null;  
        XDocument styleDoc = null;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
        {  
            PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);  
                PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
                if (styleRelation != null)  
                {  
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
                      (string)style.Attribute(w + "default") == "1"  
                select style  
            ).First().Attribute(w + "styleId");  
  
        // Find all paragraphs in the document.  
        var paragraphs =  
            from para in xDoc  
                         .Root  
                         .Element(w + "body")  
                         .Descendants(w + "p")  
            let styleNode = para  
                            .Elements(w + "pPr")  
                            .Elements(w + "pStyle")  
                            .FirstOrDefault()  
            select new  
            {  
                ParagraphNode = para,  
                StyleName = styleNode != null ?  
                    (string)styleNode.Attribute(w + "val") :  
                    defaultStyle  
            };  
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        // Retrieve all paragraphs that have no text and are styled Code.  
        var blankCodeParagraphs =  
            from para in paraWithText  
            where para.Text == "" && para.StyleName == "Code"  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = para.Text  
            };  
  
        foreach (var p in blankCodeParagraphs)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="51413-115">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="51413-115">This example produces the following output:</span></span>  
  
```output  
StyleName:Code ><  
```  
  
 <span data-ttu-id="51413-116">Samozřejmě, tento příklad by mohl být rozšířen v mnoha ohledech.</span><span class="sxs-lookup"><span data-stu-id="51413-116">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="51413-117">Například bychom mohli použít regulární výrazy k hledání textu, mohli bychom iterovat všechny soubory aplikace Word v určitém adresáři a tak dále.</span><span class="sxs-lookup"><span data-stu-id="51413-117">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>  
  
 <span data-ttu-id="51413-118">Všimněte si, že tento příklad provádí přibližně stejně jako pokud byly zapsány jako jeden dotaz.</span><span class="sxs-lookup"><span data-stu-id="51413-118">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="51413-119">Vzhledem k tomu, že každý dotaz je implementován opožděně, odložené způsobem, každý dotaz neposkytuje jeho výsledky, dokud je dotaz iterována.</span><span class="sxs-lookup"><span data-stu-id="51413-119">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="51413-120">Další informace o spuštění a opožděné vyhodnocení naleznete v [tématu Odložené spuštění a opožděné vyhodnocení v LINQ na XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="51413-120">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="51413-121">Další kroky</span><span class="sxs-lookup"><span data-stu-id="51413-121">Next Steps</span></span>  
 <span data-ttu-id="51413-122">Další část obsahuje další informace o dokumentech WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="51413-122">The next section provides more information about WordprocessingML documents:</span></span>  
  
- [<span data-ttu-id="51413-123">Podrobnosti o dokumentech Xml WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="51413-123">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](./wordprocessingml-document-with-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="51413-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="51413-124">See also</span></span>

- [<span data-ttu-id="51413-125">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="51413-125">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="51413-126">Refaktoring pomocí čisté funkce (C#)</span><span class="sxs-lookup"><span data-stu-id="51413-126">Refactoring Using a Pure Function (C#)</span></span>](./refactoring-using-a-pure-function.md)
- [<span data-ttu-id="51413-127">Odložené spuštění a opožděné vyhodnocení v LINQ na XML (C#)</span><span class="sxs-lookup"><span data-stu-id="51413-127">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
