---
title: Hledání výchozího stylu odstavce (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 45a3e293a88fc0d7fc6aa70d21d1d3a6a8bb9b13
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204101"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="c1b02-102">Hledání výchozího stylu odstavce (C#)</span><span class="sxs-lookup"><span data-stu-id="c1b02-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="c1b02-103">Prvním úkolem při manipulaci s informacemi v WordprocessingML dokumentu je najít výchozí styl odstavců v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c1b02-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1b02-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1b02-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c1b02-105">Popis</span><span class="sxs-lookup"><span data-stu-id="c1b02-105">Description</span></span>  
 <span data-ttu-id="c1b02-106">Následující příklad otevře dokument Office Open XML WordprocessingML, vyhledá části dokumentu a stylu a potom spustí dotaz, který najde výchozí název stylu.</span><span class="sxs-lookup"><span data-stu-id="c1b02-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="c1b02-107">Informace o balíčcích dokumentů Office Open XML a částech, ze kterých se skládají, najdete v tématu [Podrobnosti o Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span><span class="sxs-lookup"><span data-stu-id="c1b02-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="c1b02-108">Dotaz najde uzel s `w:style` názvem, který má atribut s názvem `w:type` s hodnotou "Paragraph", a má také atribut s názvem `w:default` "1".</span><span class="sxs-lookup"><span data-stu-id="c1b02-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="c1b02-109">Vzhledem k tomu, že bude existovat pouze jeden uzel XML s těmito atributy, dotaz <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> použije operátor pro převod kolekce na typ singleton.</span><span class="sxs-lookup"><span data-stu-id="c1b02-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="c1b02-110">Pak získá hodnotu atributu s názvem `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="c1b02-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="c1b02-111">Tento příklad používá třídy ze sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="c1b02-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="c1b02-112">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c1b02-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c1b02-113">Kód</span><span class="sxs-lookup"><span data-stu-id="c1b02-113">Code</span></span>  
  
```csharp  
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
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
// The following query finds all the paragraphs that have the default style.  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
Console.WriteLine("The default style is: {0}", defaultStyle);  
```  
  
### <a name="comments"></a><span data-ttu-id="c1b02-114">Komentáře</span><span class="sxs-lookup"><span data-stu-id="c1b02-114">Comments</span></span>  
 <span data-ttu-id="c1b02-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c1b02-115">This example produces the following output:</span></span>  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="c1b02-116">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c1b02-116">Next Steps</span></span>  
 <span data-ttu-id="c1b02-117">V dalším příkladu vytvoříte podobný dotaz, který najde všechny odstavce v dokumentu a jejich styly:</span><span class="sxs-lookup"><span data-stu-id="c1b02-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="c1b02-118">Načítání odstavců a jejich stylů (C#)</span><span class="sxs-lookup"><span data-stu-id="c1b02-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  
