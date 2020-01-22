---
title: Tvar dokumentů WordprocessingML
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 9dd858e28c010d901c2c5fdfb477fe2c6975dbd4
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/22/2020
ms.locfileid: "76315847"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="8a221-102">Tvar dokumentů WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a221-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="8a221-103">Toto téma představuje tvar XML dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="8a221-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="8a221-104">Formáty systém Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="8a221-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="8a221-105">Nativní formát souboru pro 2007 systém Microsoft Office je Office Open XML (obvykle se označuje jako Open XML).</span><span class="sxs-lookup"><span data-stu-id="8a221-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="8a221-106">Open XML je formát založený na jazyce XML, který Standard ECMA používá a právě prochází procesem standardů ISO-IEC.</span><span class="sxs-lookup"><span data-stu-id="8a221-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="8a221-107">Jazyk značek pro soubory pro zpracování textu v jazyce Open XML se nazývá WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="8a221-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="8a221-108">Tento kurz používá jako vstup pro příklady zdrojové soubory WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="8a221-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="8a221-109">Pokud používáte systém Microsoft Office 2003, můžete dokumenty ukládat ve formátu Office Open XML, pokud jste nainstalovali sadu systém Microsoft Office Compatibility Pack pro formáty souborů Word, Excel a PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="8a221-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="8a221-110">Tvar dokumentů WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="8a221-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="8a221-111">První věc, kterou je třeba pochopit, je tvar dokumentů WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="8a221-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="8a221-112">WordprocessingML dokument obsahuje element tělo (nazvaný `w:body`), který obsahuje odstavce v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="8a221-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="8a221-113">Každý odstavec obsahuje jedno nebo více textových běhů (s názvem `w:r`).</span><span class="sxs-lookup"><span data-stu-id="8a221-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="8a221-114">Každý běh textu obsahuje jednu nebo více textových částí (s názvem `w:t`).</span><span class="sxs-lookup"><span data-stu-id="8a221-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="8a221-115">Následuje velmi jednoduchý dokument WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="8a221-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="8a221-116">Tento dokument obsahuje dva odstavce.</span><span class="sxs-lookup"><span data-stu-id="8a221-116">This document contains two paragraphs.</span></span> <span data-ttu-id="8a221-117">Oba obsahují jeden textový běh a každý spuštěný text obsahuje jeden textový kámen.</span><span class="sxs-lookup"><span data-stu-id="8a221-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="8a221-118">Nejjednodušší způsob, jak zobrazit obsah dokumentu WordprocessingML ve formátu XML, je vytvořit ho pomocí Microsoft Wordu, uložit ho a pak spustit následující program, který vytiskne XML do konzoly.</span><span class="sxs-lookup"><span data-stu-id="8a221-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="8a221-119">Tento příklad používá třídy nalezené v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="8a221-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="8a221-120">Používá typy v oboru názvů <xref:System.IO.Packaging?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8a221-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="8a221-121">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="8a221-121">External resources</span></span>

- <span data-ttu-id="8a221-122">[Představení formátů souborů XML sady Office (2007)](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span><span class="sxs-lookup"><span data-stu-id="8a221-122">[Introducing the Office (2007) Open XML File Formats](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span></span>
- <span data-ttu-id="8a221-123">[Přehled WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span><span class="sxs-lookup"><span data-stu-id="8a221-123">[Overview of WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span></span>

## <a name="see-also"></a><span data-ttu-id="8a221-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a221-124">See also</span></span>

- [<span data-ttu-id="8a221-125">Kurz: manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a221-125">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
