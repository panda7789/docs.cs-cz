---
title: Hledání výchozího stylu odstavce (C#)
description: Naučte se zpracovat dokument WordprocessingML pomocí LINQ v jazyce C#. Tento příklad najde výchozí styl odstavců v dokumentu.
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: e18bbbdbd5b2627c9ff4c3c3eedd84d7cb166a62
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103821"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="10c66-104">Hledání výchozího stylu odstavce (C#)</span><span class="sxs-lookup"><span data-stu-id="10c66-104">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="10c66-105">Prvním úkolem při manipulaci s informacemi v WordprocessingML dokumentu je najít výchozí styl odstavců v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="10c66-105">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10c66-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="10c66-106">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="10c66-107">Popis</span><span class="sxs-lookup"><span data-stu-id="10c66-107">Description</span></span>  
 <span data-ttu-id="10c66-108">Následující příklad otevře dokument Office Open XML WordprocessingML, vyhledá části dokumentu a stylu a potom spustí dotaz, který najde výchozí název stylu.</span><span class="sxs-lookup"><span data-stu-id="10c66-108">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="10c66-109">Informace o balíčcích dokumentů Office Open XML a částech, ze kterých se skládají, najdete v tématu [Podrobnosti o Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span><span class="sxs-lookup"><span data-stu-id="10c66-109">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="10c66-110">Dotaz najde uzel s názvem `w:style` , který má atribut s názvem `w:type` s hodnotou "Paragraph", a má také atribut s názvem `w:default` "1".</span><span class="sxs-lookup"><span data-stu-id="10c66-110">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="10c66-111">Vzhledem k tomu, že bude existovat pouze jeden uzel XML s těmito atributy, dotaz použije <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operátor pro převod kolekce na typ singleton.</span><span class="sxs-lookup"><span data-stu-id="10c66-111">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="10c66-112">Pak získá hodnotu atributu s názvem `w:styleId` .</span><span class="sxs-lookup"><span data-stu-id="10c66-112">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="10c66-113">Tento příklad používá třídy ze sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="10c66-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="10c66-114">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="10c66-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="10c66-115">Kód</span><span class="sxs-lookup"><span data-stu-id="10c66-115">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="10c66-116">Komentáře</span><span class="sxs-lookup"><span data-stu-id="10c66-116">Comments</span></span>  
 <span data-ttu-id="10c66-117">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="10c66-117">This example produces the following output:</span></span>  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="10c66-118">Další kroky</span><span class="sxs-lookup"><span data-stu-id="10c66-118">Next Steps</span></span>  
 <span data-ttu-id="10c66-119">V dalším příkladu vytvoříte podobný dotaz, který najde všechny odstavce v dokumentu a jejich styly:</span><span class="sxs-lookup"><span data-stu-id="10c66-119">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="10c66-120">Načítání odstavců a jejich stylů (C#)</span><span class="sxs-lookup"><span data-stu-id="10c66-120">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  
