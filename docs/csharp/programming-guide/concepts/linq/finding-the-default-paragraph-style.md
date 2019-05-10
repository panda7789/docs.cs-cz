---
title: Vyhledání výchozího stylu odstavce (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 89c70fcbc9d5286e2c9381250b30d525ebb1eb36
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596695"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="15b28-102">Vyhledání výchozího stylu odstavce (C#)</span><span class="sxs-lookup"><span data-stu-id="15b28-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="15b28-103">První úkol v manipulaci s informace v dokumentu WordprocessingML kurzu je vyhledání výchozího stylu odstavce v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="15b28-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15b28-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="15b28-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="15b28-105">Popis</span><span class="sxs-lookup"><span data-stu-id="15b28-105">Description</span></span>  
 <span data-ttu-id="15b28-106">Následující příklad otevře dokumentu Office Open XML WordprocessingML, najde dokument a styl součástí balíčku a pak provede dotaz, který vyhledá výchozí název stylu.</span><span class="sxs-lookup"><span data-stu-id="15b28-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="15b28-107">Informace o balíčcích dokumentu Office Open XML a skládají se z části najdete v tématu [podrobnosti o Open XML WordprocessingML dokumenty Office (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="15b28-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="15b28-108">Tento dotaz najde uzel s názvem `w:style` , který má atribut s názvem `w:type` s hodnotou "odstavec", a také atribut s názvem `w:default` s hodnotou "1".</span><span class="sxs-lookup"><span data-stu-id="15b28-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="15b28-109">Vzhledem k tomu, že bude existovat jenom jeden uzel XML s těmito atributy, pomocí dotazu <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operátor k převodu kolekce na jednotlivý prvek.</span><span class="sxs-lookup"><span data-stu-id="15b28-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="15b28-110">Potom získá hodnotu atributu s názvem `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="15b28-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="15b28-111">Tento příklad používá třídy z WindowsBase sestavení.</span><span class="sxs-lookup"><span data-stu-id="15b28-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="15b28-112">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="15b28-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="15b28-113">Kód</span><span class="sxs-lookup"><span data-stu-id="15b28-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="15b28-114">Komentáře</span><span class="sxs-lookup"><span data-stu-id="15b28-114">Comments</span></span>  
 <span data-ttu-id="15b28-115">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="15b28-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="15b28-116">Další kroky</span><span class="sxs-lookup"><span data-stu-id="15b28-116">Next Steps</span></span>  
 <span data-ttu-id="15b28-117">V následujícím příkladu vytvoříte podobně jako dotaz, který najde všechny odstavce v dokumentu a jejich stylů:</span><span class="sxs-lookup"><span data-stu-id="15b28-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="15b28-118">Načtení odstavců a jejich stylů (C#)</span><span class="sxs-lookup"><span data-stu-id="15b28-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="15b28-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15b28-119">See also</span></span>

- [<span data-ttu-id="15b28-120">Kurz: Manipulace s obsahem v dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="15b28-120">Tutorial: Manipulating Content in a WordprocessingML Document</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
