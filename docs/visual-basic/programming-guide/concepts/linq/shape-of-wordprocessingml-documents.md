---
title: Tvar dokumentů WordprocessingML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 265da66329128e610c491c3ff50cec1bca434f6d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831810"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="09937-102">Tvar dokumentů WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09937-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="09937-103">Toto téma popisuje nastavení tvaru XML dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="09937-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="09937-104">Formáty Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="09937-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="09937-105">Nativní formát souborů pro systém Microsoft Office 2007 je Office Open XML (označovaného jako Open XML).</span><span class="sxs-lookup"><span data-stu-id="09937-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="09937-106">Open XML je založený na formátu XML, který formát Ecma standard a je momentálně probíhá prostřednictvím procesu normy ISO / IEC.</span><span class="sxs-lookup"><span data-stu-id="09937-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="09937-107">Značkovací jazyk pro soubory zpracování textu v rámci Open XML WordprocessingML nazývá.</span><span class="sxs-lookup"><span data-stu-id="09937-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="09937-108">Tento kurz používá WordprocessingML zdrojové soubory jako vstup pro příklady.</span><span class="sxs-lookup"><span data-stu-id="09937-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="09937-109">Pokud používáte Microsoft Office 2003, můžete uložit dokumenty ve formát Office Open XML Pokud jste nainstalovali sadu kompatibility aplikace Microsoft Office pro Word, Excel a PowerPoint 2007 formátů.</span><span class="sxs-lookup"><span data-stu-id="09937-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="09937-110">Tvar dokumentů WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="09937-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="09937-111">První věc, kterou pochopit je tvar dokumentů WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="09937-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="09937-112">Dokument WordprocessingML obsahuje text prvku (s názvem `w:body`), který obsahuje odstavců z dokumentu.</span><span class="sxs-lookup"><span data-stu-id="09937-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="09937-113">K jednotlivým odstavcům obsahuje jeden nebo více spuštění text (s názvem `w:r`).</span><span class="sxs-lookup"><span data-stu-id="09937-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="09937-114">Každý text spuštění obsahuje jeden nebo více kusů text (s názvem `w:t`).</span><span class="sxs-lookup"><span data-stu-id="09937-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="09937-115">Toto je velmi jednoduchý dokumentu WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="09937-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="09937-116">Tento dokument obsahuje dva odstavce.</span><span class="sxs-lookup"><span data-stu-id="09937-116">This document contains two paragraphs.</span></span> <span data-ttu-id="09937-117">Oba obsahují jednoho textu s spuštění a každý text spuštění obsahuje část jednoho textu.</span><span class="sxs-lookup"><span data-stu-id="09937-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="09937-118">Nejjednodušší způsob, jak zobrazit obsah dokumentu WordprocessingML v podobě XML je ji vytvořit pomocí aplikace Microsoft Word, uložte a spusťte následující program, který vytiskne XML do konzoly.</span><span class="sxs-lookup"><span data-stu-id="09937-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="09937-119">Tento příklad používá třídy v sestavení WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="09937-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="09937-120">Používá typy v <xref:System.IO.Packaging?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="09937-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="09937-121">Externí zdroje</span><span class="sxs-lookup"><span data-stu-id="09937-121">External Resources</span></span>  
 <span data-ttu-id="09937-122">[Úvod do formátů souborů Office (2007) Open XML](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span><span class="sxs-lookup"><span data-stu-id="09937-122">[Introducing the Office (2007) Open XML File Formats](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span></span>  
  
 <span data-ttu-id="09937-123">[Přehled WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span><span class="sxs-lookup"><span data-stu-id="09937-123">[Overview of WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span></span>  
  
 [<span data-ttu-id="09937-124">Office 2003: Stránku položek ke stažení schémata referenční dokumentace XML</span><span class="sxs-lookup"><span data-stu-id="09937-124">Office 2003: XML Reference Schemas Download page</span></span>](https://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a><span data-ttu-id="09937-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09937-125">See also</span></span>

- [<span data-ttu-id="09937-126">Kurz: Manipulace s obsahem v dokumentu WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09937-126">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
