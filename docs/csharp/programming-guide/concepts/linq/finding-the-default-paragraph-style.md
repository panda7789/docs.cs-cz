---
title: Hledání výchozí styl odstavce (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: e29ca281e1867a72a76a28765912c39675ca0f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335949"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="58f4d-102">Hledání výchozí styl odstavce (C#)</span><span class="sxs-lookup"><span data-stu-id="58f4d-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="58f4d-103">První úlohou manipulace s nimi informace v dokumentu WordprocessingML kurzu je najít výchozí styl odstavců v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="58f4d-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58f4d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="58f4d-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="58f4d-105">Popis</span><span class="sxs-lookup"><span data-stu-id="58f4d-105">Description</span></span>  
 <span data-ttu-id="58f4d-106">Následující příklad otevře dokument Office Open XML WordprocessingML, vyhledá části dokumentu a stylu balíčku a potom provede dotaz, který vyhledá výchozí název stylu.</span><span class="sxs-lookup"><span data-stu-id="58f4d-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="58f4d-107">Informace o balíčcích dokumentu Office Open XML a skládají se z části najdete v tématu [podrobnosti o Open XML WordprocessingML dokumenty Office (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="58f4d-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="58f4d-108">Tento dotaz najde uzel s názvem `w:style` , má atribut s názvem `w:type` s hodnotou "odstavec", a má také atribut pojmenovaný `w:default` s hodnotou "1".</span><span class="sxs-lookup"><span data-stu-id="58f4d-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="58f4d-109">Vzhledem k tomu, že budou existovat jenom jeden uzel XML s těmito atributy, pomocí dotazu <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operátor převést kolekci typu singleton.</span><span class="sxs-lookup"><span data-stu-id="58f4d-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="58f4d-110">Potom získá hodnotu atributu s názvem `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="58f4d-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="58f4d-111">Tento příklad používá třídy z WindowsBase sestavení.</span><span class="sxs-lookup"><span data-stu-id="58f4d-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="58f4d-112">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="58f4d-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="58f4d-113">Kód</span><span class="sxs-lookup"><span data-stu-id="58f4d-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="58f4d-114">Komentáře</span><span class="sxs-lookup"><span data-stu-id="58f4d-114">Comments</span></span>  
 <span data-ttu-id="58f4d-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="58f4d-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="58f4d-116">Další kroky</span><span class="sxs-lookup"><span data-stu-id="58f4d-116">Next Steps</span></span>  
 <span data-ttu-id="58f4d-117">V dalším příkladu vytvoříte podobné dotaz, který vyhledá všechny odstavce do dokumentu a jejich styly:</span><span class="sxs-lookup"><span data-stu-id="58f4d-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
-   [<span data-ttu-id="58f4d-118">Načítání odstavců a jejich styly (C#)</span><span class="sxs-lookup"><span data-stu-id="58f4d-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="58f4d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="58f4d-119">See Also</span></span>  
 [<span data-ttu-id="58f4d-120">Kurz: Manipulace s obsahem v dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="58f4d-120">Tutorial: Manipulating Content in a WordprocessingML Document</span></span>](http://msdn.microsoft.com/library/2696355e-4f83-4eaf-91b2-baa721f42fb4)
