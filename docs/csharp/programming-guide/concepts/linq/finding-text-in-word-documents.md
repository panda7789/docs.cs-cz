---
title: Hledání textu v dokumentech aplikace WordC#()
ms.date: 07/20/2015
ms.assetid: 82f86677-560b-49dc-a089-610409939b2a
ms.openlocfilehash: 173472b9dbd669476c3e5529655d111b88b0dba2
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205397"
---
# <a name="finding-text-in-word-documents-c"></a><span data-ttu-id="0e5c4-102">Hledání textu v dokumentech aplikace WordC#()</span><span class="sxs-lookup"><span data-stu-id="0e5c4-102">Finding Text in Word Documents (C#)</span></span>
<span data-ttu-id="0e5c4-103">Toto téma rozšiřuje předchozí dotazy, aby bylo možné něco využít: vyhledá všechny výskyty řetězce v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0e5c4-103">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e5c4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e5c4-104">Example</span></span>  
 <span data-ttu-id="0e5c4-105">Tento příklad zpracovává dokument WordprocessingML, aby bylo možné najít všechny výskyty určitého textu v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0e5c4-105">This example processes a WordprocessingML document, to find all the occurrences of a specific piece of text in the document.</span></span> <span data-ttu-id="0e5c4-106">K tomu použijeme dotaz, který najde řetězec "Hello".</span><span class="sxs-lookup"><span data-stu-id="0e5c4-106">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="0e5c4-107">Tento příklad sestaví na předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="0e5c4-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="0e5c4-108">Nový dotaz se zavolá v komentářích v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="0e5c4-108">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="0e5c4-109">Pokyny k vytvoření zdrojového dokumentu pro tento příklad najdete v tématu [vytvoření zdrojového dokumentu XML (C#) pro zdrojový Office](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="0e5c4-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="0e5c4-110">Tento příklad používá třídy nalezené v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="0e5c4-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="0e5c4-111">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0e5c4-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="0e5c4-112">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0e5c4-112">This example produces the following output:</span></span>  
  
```output  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="0e5c4-113">Můžete samozřejmě upravit hledání tak, aby vyhledalo řádky s konkrétním stylem.</span><span class="sxs-lookup"><span data-stu-id="0e5c4-113">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="0e5c4-114">Následující dotaz vyhledá všechny prázdné řádky, které mají styl kódu:</span><span class="sxs-lookup"><span data-stu-id="0e5c4-114">The following query finds all blank lines that have the Code style:</span></span>  
  
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
  
 <span data-ttu-id="0e5c4-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0e5c4-115">This example produces the following output:</span></span>  
  
```output  
StyleName:Code ><  
```  
  
 <span data-ttu-id="0e5c4-116">Tento příklad je samozřejmě možné rozšířit různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="0e5c4-116">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="0e5c4-117">Například můžeme použít regulární výrazy pro hledání textu, můžeme iterovat všemi soubory aplikace Word v konkrétním adresáři a tak dále.</span><span class="sxs-lookup"><span data-stu-id="0e5c4-117">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>  
  
 <span data-ttu-id="0e5c4-118">Všimněte si, že v tomto příkladu se provádí přibližně i když byl zapsaný jako jeden dotaz.</span><span class="sxs-lookup"><span data-stu-id="0e5c4-118">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="0e5c4-119">Vzhledem k tomu, že každý dotaz je implementován v opožděném, odvoditelné podobě, každý dotaz nepřinese výsledky, dokud se dotaz neopakuje.</span><span class="sxs-lookup"><span data-stu-id="0e5c4-119">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="0e5c4-120">Další informace o provádění a opožděném vyhodnocení naleznete [v tématu Odložené provádění a opožděné hodnocení v LINQ to XMLC#()](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0e5c4-120">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="0e5c4-121">Další kroky</span><span class="sxs-lookup"><span data-stu-id="0e5c4-121">Next Steps</span></span>  
 <span data-ttu-id="0e5c4-122">V další části najdete další informace o WordprocessingML dokumentech:</span><span class="sxs-lookup"><span data-stu-id="0e5c4-122">The next section provides more information about WordprocessingML documents:</span></span>  
  
- [<span data-ttu-id="0e5c4-123">Podrobnosti Office Open XML WordprocessingML Documents (C#)</span><span class="sxs-lookup"><span data-stu-id="0e5c4-123">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](./wordprocessingml-document-with-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="0e5c4-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e5c4-124">See also</span></span>

- [<span data-ttu-id="0e5c4-125">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="0e5c4-125">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="0e5c4-126">Refaktoring pomocí funkce Pure (C#)</span><span class="sxs-lookup"><span data-stu-id="0e5c4-126">Refactoring Using a Pure Function (C#)</span></span>](./refactoring-using-a-pure-function.md)
- [<span data-ttu-id="0e5c4-127">Odložené provádění a opožděné vyhodnocení v LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0e5c4-127">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
