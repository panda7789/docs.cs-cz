---
title: Hledání výchozího stylu odstavce (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 702d3906f51b996f59dcd15067702b6de07c60a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594375"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="bc760-102">Hledání výchozího stylu odstavce (C#)</span><span class="sxs-lookup"><span data-stu-id="bc760-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="bc760-103">Prvním úkolem při manipulaci s informacemi v WordprocessingML dokumentu je najít výchozí styl odstavců v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bc760-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc760-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc760-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="bc760-105">Popis</span><span class="sxs-lookup"><span data-stu-id="bc760-105">Description</span></span>  
 <span data-ttu-id="bc760-106">Následující příklad otevře dokument Office Open XML WordprocessingML, vyhledá části dokumentu a stylu a potom spustí dotaz, který najde výchozí název stylu.</span><span class="sxs-lookup"><span data-stu-id="bc760-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="bc760-107">Informace o balíčcích dokumentů Office Open XML a částech, ze kterých se skládají, najdete v tématu [Podrobnosti o Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span><span class="sxs-lookup"><span data-stu-id="bc760-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="bc760-108">Dotaz najde uzel s `w:style` názvem, který má atribut s názvem `w:type` s hodnotou "Paragraph", a má také atribut s názvem `w:default` "1".</span><span class="sxs-lookup"><span data-stu-id="bc760-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="bc760-109">Vzhledem k tomu, že bude existovat pouze jeden uzel XML s těmito atributy, dotaz <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> použije operátor pro převod kolekce na typ singleton.</span><span class="sxs-lookup"><span data-stu-id="bc760-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="bc760-110">Pak získá hodnotu atributu s názvem `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="bc760-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="bc760-111">Tento příklad používá třídy ze sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="bc760-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="bc760-112">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bc760-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="bc760-113">Kód</span><span class="sxs-lookup"><span data-stu-id="bc760-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="bc760-114">Komentáře</span><span class="sxs-lookup"><span data-stu-id="bc760-114">Comments</span></span>  
 <span data-ttu-id="bc760-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="bc760-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="bc760-116">Další kroky</span><span class="sxs-lookup"><span data-stu-id="bc760-116">Next Steps</span></span>  
 <span data-ttu-id="bc760-117">V dalším příkladu vytvoříte podobný dotaz, který najde všechny odstavce v dokumentu a jejich styly:</span><span class="sxs-lookup"><span data-stu-id="bc760-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="bc760-118">Načítání odstavců a jejich stylů (C#)</span><span class="sxs-lookup"><span data-stu-id="bc760-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  
  