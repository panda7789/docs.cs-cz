---
title: Nalezení výchozího odstavcového stylu (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 8cc1f1b9df208b0b180e5fe4a50922b5ee46b480
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169529"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="01aea-102">Nalezení výchozího odstavcového stylu (C#)</span><span class="sxs-lookup"><span data-stu-id="01aea-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="01aea-103">První úkol v manipulaci s informacemi v kurzu dokumentu WordprocessingML je najít výchozí styl odstavců v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="01aea-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01aea-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="01aea-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="01aea-105">Popis</span><span class="sxs-lookup"><span data-stu-id="01aea-105">Description</span></span>  
 <span data-ttu-id="01aea-106">Následující příklad otevře dokument Office Open XML WordprocessingML, vyhledá části balíčku a styly a potom snímá dotaz, který vyhledá výchozí název stylu.</span><span class="sxs-lookup"><span data-stu-id="01aea-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="01aea-107">Informace o balíčcích dokumentů Office Open XML a jejich částech naleznete [v tématu Podrobnosti o dokumentech Pm Open XML WordprocessingML Documents (C#).](./wordprocessingml-document-with-styles.md)</span><span class="sxs-lookup"><span data-stu-id="01aea-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="01aea-108">Dotaz vyhledá uzel s `w:style` názvem, který `w:type` má atribut s názvem s hodnotou `w:default` "paragraph" a má také atribut s názvem s hodnotou "1".</span><span class="sxs-lookup"><span data-stu-id="01aea-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="01aea-109">Vzhledem k tomu, že bude existovat pouze jeden <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> uzel XML s těmito atributy, dotaz používá operátor převést kolekci na singleton.</span><span class="sxs-lookup"><span data-stu-id="01aea-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="01aea-110">Potom získá hodnotu atributu s `w:styleId`názvem .</span><span class="sxs-lookup"><span data-stu-id="01aea-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="01aea-111">Tento příklad používá třídy z sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="01aea-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="01aea-112">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="01aea-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="01aea-113">kód</span><span class="sxs-lookup"><span data-stu-id="01aea-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="01aea-114">Komentáře</span><span class="sxs-lookup"><span data-stu-id="01aea-114">Comments</span></span>  
 <span data-ttu-id="01aea-115">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="01aea-115">This example produces the following output:</span></span>  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="01aea-116">Další kroky</span><span class="sxs-lookup"><span data-stu-id="01aea-116">Next Steps</span></span>  
 <span data-ttu-id="01aea-117">V dalším příkladu vytvoříte podobný dotaz, který vyhledá všechny odstavce v dokumentu a jejich styly:</span><span class="sxs-lookup"><span data-stu-id="01aea-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="01aea-118">Načítání odstavců a jejich stylů (C#)</span><span class="sxs-lookup"><span data-stu-id="01aea-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  
