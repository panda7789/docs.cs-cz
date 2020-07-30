---
title: Tvar dokumentů WordprocessingML (C#)
description: Přečtěte si o formátu dokumentu WordprocessingML. Několik příkladů C# používá WordprocessingML dokument.
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 4a7716d775a634c5ad3719714be68fce67d5cbfe
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302344"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="3c0d5-104">Tvar dokumentů WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="3c0d5-104">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="3c0d5-105">Toto téma představuje tvar XML dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-105">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="3c0d5-106">Formáty systém Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="3c0d5-106">Microsoft Office Formats</span></span>  
 <span data-ttu-id="3c0d5-107">Nativní formát souboru pro 2007 systém Microsoft Office je Office Open XML (obvykle se označuje jako Open XML).</span><span class="sxs-lookup"><span data-stu-id="3c0d5-107">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="3c0d5-108">Open XML je formát založený na jazyce XML, který Standard ECMA používá a právě prochází procesem standardů ISO-IEC.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-108">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="3c0d5-109">Jazyk značek pro soubory pro zpracování textu v jazyce Open XML se nazývá WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-109">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="3c0d5-110">Tento kurz používá jako vstup pro příklady zdrojové soubory WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-110">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="3c0d5-111">Pokud používáte systém Microsoft Office 2003, můžete dokumenty ukládat ve formátu Office Open XML, pokud jste nainstalovali sadu systém Microsoft Office Compatibility Pack pro formáty souborů Word, Excel a PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-111">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="3c0d5-112">Tvar dokumentů WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="3c0d5-112">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="3c0d5-113">První věc, kterou je třeba pochopit, je tvar dokumentů WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-113">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="3c0d5-114">WordprocessingML dokument obsahuje element tělo (pojmenovaný `w:body` ), který obsahuje odstavce v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-114">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="3c0d5-115">Každý odstavec obsahuje jedno nebo více textových běhů (s názvem `w:r` ).</span><span class="sxs-lookup"><span data-stu-id="3c0d5-115">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="3c0d5-116">Každý běh textu obsahuje jednu nebo více textových částí (s názvem `w:t` ).</span><span class="sxs-lookup"><span data-stu-id="3c0d5-116">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="3c0d5-117">Následuje velmi jednoduchý dokument WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="3c0d5-117">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="3c0d5-118">Tento dokument obsahuje dva odstavce.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-118">This document contains two paragraphs.</span></span> <span data-ttu-id="3c0d5-119">Oba obsahují jeden textový běh a každý spuštěný text obsahuje jeden textový kámen.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-119">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="3c0d5-120">Nejjednodušší způsob, jak zobrazit obsah dokumentu WordprocessingML ve formátu XML, je vytvořit ho pomocí Microsoft Wordu, uložit ho a pak spustit následující program, který vytiskne XML do konzoly.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-120">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="3c0d5-121">Tento příklad používá třídy nalezené v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-121">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="3c0d5-122">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3c0d5-122">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="3c0d5-123">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="3c0d5-123">External resources</span></span>

- [<span data-ttu-id="3c0d5-124">Představení formátů souborů XML sady Office (2007)</span><span class="sxs-lookup"><span data-stu-id="3c0d5-124">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [<span data-ttu-id="3c0d5-125">Přehled WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="3c0d5-125">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [<span data-ttu-id="3c0d5-126">Anatomie souboru WordProcessingML</span><span class="sxs-lookup"><span data-stu-id="3c0d5-126">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)
- [<span data-ttu-id="3c0d5-127">Úvod do WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="3c0d5-127">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a><span data-ttu-id="3c0d5-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c0d5-128">See also</span></span>

- [<span data-ttu-id="3c0d5-129">Kurz: manipulace s obsahem v dokumentu WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="3c0d5-129">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
