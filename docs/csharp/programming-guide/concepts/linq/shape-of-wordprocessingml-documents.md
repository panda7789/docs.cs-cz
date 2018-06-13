---
title: Tvar WordprocessingML dokumentů (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 0d8a80a8e7d33facd452e3b7fb31793c1ed55c58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331984"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="cbbf3-102">Tvar WordprocessingML dokumentů (C#)</span><span class="sxs-lookup"><span data-stu-id="cbbf3-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="cbbf3-103">Toto téma představuje obrazec WordprocessingML dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="cbbf3-104">Formáty Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="cbbf3-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="cbbf3-105">Nativní formát pro systém Microsoft Office 2007 je Office Open XML (označovaného jako Open XML).</span><span class="sxs-lookup"><span data-stu-id="cbbf3-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="cbbf3-106">Otevřete soubor XML je XML na základě formátu, který Ecma standard a je aktuálně projít proces standardy ISO / IEC.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="cbbf3-107">Jazyk kódu pro zpracování textu soubory v rámci Open XML se nazývá WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="cbbf3-108">Tento kurz používá WordprocessingML zdrojové soubory jako vstup pro příklady.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="cbbf3-109">Pokud používáte Microsoft Office 2003, můžete uložit dokumenty ve formátu Office Open XML Pokud jste nainstalovali sadu Microsoft Office kompatibility pro Word, Excel a PowerPoint formáty souborů 2007.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="cbbf3-110">Obrazec WordprocessingML dokumenty</span><span class="sxs-lookup"><span data-stu-id="cbbf3-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="cbbf3-111">První věc pochopit je obrazec WordprocessingML dokumenty.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="cbbf3-112">Dokument WordprocessingML obsahuje body element (s názvem `w:body`), který obsahuje odstavců dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="cbbf3-113">Jednotlivých odstavců, obsahuje jeden nebo více spustí text (s názvem `w:r`).</span><span class="sxs-lookup"><span data-stu-id="cbbf3-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="cbbf3-114">Každý text spustit obsahuje jeden nebo více částí textu (s názvem `w:t`).</span><span class="sxs-lookup"><span data-stu-id="cbbf3-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="cbbf3-115">Toto je velmi jednoduchý WordprocessingML dokumentu:</span><span class="sxs-lookup"><span data-stu-id="cbbf3-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="cbbf3-116">Tento dokument obsahuje dva odstavce.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-116">This document contains two paragraphs.</span></span> <span data-ttu-id="cbbf3-117">Oba obsahují jednoho textu s spustit a každý text spustit obsahuje část jednoho textu.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="cbbf3-118">Nejjednodušší způsob, jak zobrazit obsah v dokumentu WordprocessingML ve formátu XML je vytvořit pomocí aplikace Microsoft Word, uložte ho a pak spusťte následující program, který vytiskne XML do konzoly.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="cbbf3-119">Tento příklad používá třídy v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="cbbf3-120">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cbbf3-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="cbbf3-121">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="cbbf3-121">External Resources</span></span>  
 [<span data-ttu-id="cbbf3-122">Představení formáty souborů Office (2007) Open XML</span><span class="sxs-lookup"><span data-stu-id="cbbf3-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://msdn.microsoft.com/library/ms406049.aspx)  
 <span data-ttu-id="cbbf3-123">[Přehled WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="cbbf3-123">[Overview of WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx)</span></span>  
 [<span data-ttu-id="cbbf3-124">Anatomie WordProcessingML souboru</span><span class="sxs-lookup"><span data-stu-id="cbbf3-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)  
 [<span data-ttu-id="cbbf3-125">Úvod do WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="cbbf3-125">Introduction to WordprocessingML</span></span>](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [<span data-ttu-id="cbbf3-126">Office 2003: Stáhnout schémat XML odkaz na stránku</span><span class="sxs-lookup"><span data-stu-id="cbbf3-126">Office 2003: XML Reference Schemas Download page</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=101)  
  
## <a name="see-also"></a><span data-ttu-id="cbbf3-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="cbbf3-127">See Also</span></span>  
 [<span data-ttu-id="cbbf3-128">Kurz: Manipulace se obsah v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="cbbf3-128">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
