---
title: Tvar WordprocessingML dokumentů (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 58c028fed465f45fdcf8f63f2119eb8e8b201e32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732670"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="a50d3-102">Tvar WordprocessingML dokumentů (C#)</span><span class="sxs-lookup"><span data-stu-id="a50d3-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="a50d3-103">Toto téma představuje tvar XML dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="a50d3-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="a50d3-104">Formáty systém Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="a50d3-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="a50d3-105">Nativní formát souboru pro 2007 systém Microsoft Office je Office Open XML (obvykle se označuje jako Open XML).</span><span class="sxs-lookup"><span data-stu-id="a50d3-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="a50d3-106">Open XML je formát založený na jazyce XML, který Standard ECMA používá a právě prochází procesem standardů ISO-IEC.</span><span class="sxs-lookup"><span data-stu-id="a50d3-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="a50d3-107">Jazyk značek pro soubory pro zpracování textu v jazyce Open XML se nazývá WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="a50d3-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="a50d3-108">Tento kurz používá jako vstup pro příklady zdrojové soubory WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="a50d3-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="a50d3-109">Pokud používáte systém Microsoft Office 2003, můžete dokumenty ukládat ve formátu Office Open XML, pokud jste nainstalovali sadu systém Microsoft Office Compatibility Pack pro formáty souborů Word, Excel a PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="a50d3-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="a50d3-110">Tvar dokumentů WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="a50d3-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="a50d3-111">První věc, kterou je třeba pochopit, je tvar dokumentů WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="a50d3-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="a50d3-112">WordprocessingML dokument obsahuje element tělo (nazvaný `w:body`), který obsahuje odstavce v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a50d3-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="a50d3-113">Každý odstavec obsahuje jedno nebo více textových běhů (s názvem `w:r`).</span><span class="sxs-lookup"><span data-stu-id="a50d3-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="a50d3-114">Každý běh textu obsahuje jednu nebo více textových částí (s názvem `w:t`).</span><span class="sxs-lookup"><span data-stu-id="a50d3-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="a50d3-115">Následuje velmi jednoduchý dokument WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="a50d3-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="a50d3-116">Tento dokument obsahuje dva odstavce.</span><span class="sxs-lookup"><span data-stu-id="a50d3-116">This document contains two paragraphs.</span></span> <span data-ttu-id="a50d3-117">Oba obsahují jeden textový běh a každý spuštěný text obsahuje jeden textový kámen.</span><span class="sxs-lookup"><span data-stu-id="a50d3-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="a50d3-118">Nejjednodušší způsob, jak zobrazit obsah dokumentu WordprocessingML ve formátu XML, je vytvořit ho pomocí Microsoft Wordu, uložit ho a pak spustit následující program, který vytiskne XML do konzoly.</span><span class="sxs-lookup"><span data-stu-id="a50d3-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="a50d3-119">Tento příklad používá třídy nalezené v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="a50d3-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="a50d3-120">Používá typy v oboru názvů <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a50d3-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="a50d3-121">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="a50d3-121">External resources</span></span>

- [<span data-ttu-id="a50d3-122">Představení formátů souborů XML sady Office (2007)</span><span class="sxs-lookup"><span data-stu-id="a50d3-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [<span data-ttu-id="a50d3-123">Přehled WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="a50d3-123">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [<span data-ttu-id="a50d3-124">Anatomie souboru WordProcessingML</span><span class="sxs-lookup"><span data-stu-id="a50d3-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)
- [<span data-ttu-id="a50d3-125">Úvod do WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="a50d3-125">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a><span data-ttu-id="a50d3-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a50d3-126">See also</span></span>

- [<span data-ttu-id="a50d3-127">Kurz: manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="a50d3-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
