---
title: Tvar dokumentů WordprocessingML (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 4c034950006b7ce09ad03e4579cc298f0b2dd218
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711538"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="fc9b1-102">Tvar dokumentů WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="fc9b1-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="fc9b1-103">Toto téma popisuje nastavení tvaru XML dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="fc9b1-104">Formáty Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="fc9b1-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="fc9b1-105">Nativní formát souborů pro systém Microsoft Office 2007 je Office Open XML (označovaného jako Open XML).</span><span class="sxs-lookup"><span data-stu-id="fc9b1-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="fc9b1-106">Open XML je založený na formátu XML, který formát Ecma standard a je momentálně probíhá prostřednictvím procesu normy ISO / IEC.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="fc9b1-107">Značkovací jazyk pro soubory zpracování textu v rámci Open XML WordprocessingML nazývá.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="fc9b1-108">Tento kurz používá WordprocessingML zdrojové soubory jako vstup pro příklady.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="fc9b1-109">Pokud používáte Microsoft Office 2003, můžete uložit dokumenty ve formát Office Open XML Pokud jste nainstalovali sadu kompatibility aplikace Microsoft Office pro Word, Excel a PowerPoint 2007 formátů.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="fc9b1-110">Tvar dokumentů WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="fc9b1-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="fc9b1-111">První věc, kterou pochopit je tvar dokumentů WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="fc9b1-112">Dokument WordprocessingML obsahuje text prvku (s názvem `w:body`), který obsahuje odstavců z dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="fc9b1-113">K jednotlivým odstavcům obsahuje jeden nebo více spuštění text (s názvem `w:r`).</span><span class="sxs-lookup"><span data-stu-id="fc9b1-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="fc9b1-114">Každý text spuštění obsahuje jeden nebo více kusů text (s názvem `w:t`).</span><span class="sxs-lookup"><span data-stu-id="fc9b1-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="fc9b1-115">Toto je velmi jednoduchý dokumentu WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="fc9b1-115">The following is a very simple WordprocessingML document:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 <span data-ttu-id="fc9b1-116">Tento dokument obsahuje dva odstavce.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-116">This document contains two paragraphs.</span></span> <span data-ttu-id="fc9b1-117">Oba obsahují jednoho textu s spuštění a každý text spuštění obsahuje část jednoho textu.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="fc9b1-118">Nejjednodušší způsob, jak zobrazit obsah dokumentu WordprocessingML v podobě XML je ji vytvořit pomocí aplikace Microsoft Word, uložte a spusťte následující program, který vytiskne XML do konzoly.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="fc9b1-119">Tento příklad používá třídy v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="fc9b1-120">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fc9b1-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="fc9b1-121">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="fc9b1-121">External Resources</span></span>  
 [<span data-ttu-id="fc9b1-122">Úvod do formátů souborů Office (2007) Open XML</span><span class="sxs-lookup"><span data-stu-id="fc9b1-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)  
 [<span data-ttu-id="fc9b1-123">Přehled WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="fc9b1-123">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)  
 [<span data-ttu-id="fc9b1-124">Anatomie soubor WordProcessingML</span><span class="sxs-lookup"><span data-stu-id="fc9b1-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)  
 [<span data-ttu-id="fc9b1-125">Úvod do WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="fc9b1-125">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [<span data-ttu-id="fc9b1-126">Office 2003: Stránku položek ke stažení schémata referenční dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="fc9b1-126">Office 2003: XML Reference Schemas Download page</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=101)  
  
## <a name="see-also"></a><span data-ttu-id="fc9b1-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc9b1-127">See also</span></span>

- [<span data-ttu-id="fc9b1-128">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="fc9b1-128">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
