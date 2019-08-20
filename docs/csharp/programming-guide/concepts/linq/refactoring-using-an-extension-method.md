---
title: Refaktoring pomocí metody rozšíření (C#)
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: 2be848d6454abf0dd37a6974cff915a107336503
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591297"
---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="53e9a-102">Refaktoring pomocí metody rozšíření (C#)</span><span class="sxs-lookup"><span data-stu-id="53e9a-102">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="53e9a-103">Tento příklad sestaví v předchozím příkladu a [načítá text z odstavcůC#()](./retrieving-the-text-of-the-paragraphs.md)tím, že refaktoringuje zřetězení řetězců pomocí funkce Pure, která je implementována jako metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="53e9a-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="53e9a-104">Předchozí příklad použil <xref:System.Linq.Enumerable.Aggregate%2A> standardní operátor dotazu k zřetězení více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="53e9a-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="53e9a-105">Je ale pohodlnější napsat metodu rozšíření k tomu, protože výsledný dotaz je menší a jednodušší.</span><span class="sxs-lookup"><span data-stu-id="53e9a-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53e9a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="53e9a-106">Example</span></span>  
 <span data-ttu-id="53e9a-107">Tento příklad zpracovává dokument WordprocessingML, načítá odstavce, styl každého odstavce a text každého odstavce.</span><span class="sxs-lookup"><span data-stu-id="53e9a-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="53e9a-108">Tento příklad sestaví na předchozích příkladech v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="53e9a-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="53e9a-109">Příklad obsahuje více přetížení `StringConcatenate` metody.</span><span class="sxs-lookup"><span data-stu-id="53e9a-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="53e9a-110">Pokyny pro vytvoření zdrojového dokumentu pro tento příklad najdete v [tématu vytvoření zdrojového dokumentuC#XML pro Office Open](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="53e9a-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="53e9a-111">Tento příklad používá třídy ze sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="53e9a-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="53e9a-112">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="53e9a-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
```  
  
## <a name="example"></a><span data-ttu-id="53e9a-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="53e9a-113">Example</span></span>  
 <span data-ttu-id="53e9a-114">Existují čtyři přetížení `StringConcatenate` metody.</span><span class="sxs-lookup"><span data-stu-id="53e9a-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="53e9a-115">Jedno přetížení jednoduše převezme kolekci řetězců a vrátí jeden řetězec.</span><span class="sxs-lookup"><span data-stu-id="53e9a-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="53e9a-116">Jiné přetížení může převzít kolekci libovolného typu a delegáta, který je projektem z typu Singleton, na řetězec.</span><span class="sxs-lookup"><span data-stu-id="53e9a-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="53e9a-117">Existují dvě přetížení, která umožňují zadat řetězec oddělovače.</span><span class="sxs-lookup"><span data-stu-id="53e9a-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="53e9a-118">Následující kód používá všechna čtyři přetížení.</span><span class="sxs-lookup"><span data-stu-id="53e9a-118">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="53e9a-119">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="53e9a-119">This example produces the following output:</span></span>  
  
```  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="53e9a-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="53e9a-120">Example</span></span>  
 <span data-ttu-id="53e9a-121">Nyní lze příklad upravit tak, aby využil nové metody rozšíření:</span><span class="sxs-lookup"><span data-stu-id="53e9a-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
                Text = para  
                       .ParagraphNode  
                       .Elements(w + "r")  
                       .Elements(w + "t")  
                       .StringConcatenate(e => (string)e)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="53e9a-122">Tento příklad vytvoří následující výstup při použití v dokumentu popsaném v [tématu vytvoření zdrojového dokumentu XML pro OfficeC#()](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="53e9a-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="53e9a-123">Všimněte si, že tento refaktoring je variantou refaktoringu do funkce Pure.</span><span class="sxs-lookup"><span data-stu-id="53e9a-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="53e9a-124">V dalším tématu se dozvíte, jak podrobnější informace o faktorování čistě funkcí.</span><span class="sxs-lookup"><span data-stu-id="53e9a-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="53e9a-125">Další kroky</span><span class="sxs-lookup"><span data-stu-id="53e9a-125">Next Steps</span></span>  
 <span data-ttu-id="53e9a-126">Následující příklad ukazuje, jak refaktorovat tento kód jiným způsobem pomocí funkce Pure:</span><span class="sxs-lookup"><span data-stu-id="53e9a-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="53e9a-127">Refaktoring pomocí funkce Pure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53e9a-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="53e9a-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53e9a-128">See also</span></span>

- [<span data-ttu-id="53e9a-129">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="53e9a-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="53e9a-130">Refaktoring do čistě funkcí (C#)</span><span class="sxs-lookup"><span data-stu-id="53e9a-130">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)
