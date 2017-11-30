---
title: WordprocessingML dokument s Styles2
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9136e4d-c368-4661-8049-7d45c679a236
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ac833daca2e4ba12d61a1ee3c9526b7368baee74
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="7aee1-102">WordprocessingML dokument s styly</span><span class="sxs-lookup"><span data-stu-id="7aee1-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="7aee1-103">Složitější dokumenty WordprocessingML mít odstavců, které jsou naformátované se styly.</span><span class="sxs-lookup"><span data-stu-id="7aee1-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="7aee1-104">Několik poznámky o způsob vytvoření dokumentů WordprocessingML jsou užitečné.</span><span class="sxs-lookup"><span data-stu-id="7aee1-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="7aee1-105">WordprocessingML dokumenty jsou uložené v balíčcích.</span><span class="sxs-lookup"><span data-stu-id="7aee1-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="7aee1-106">Balíčky obsahují více částí (částí mít explicitní význam, když se používá v kontextu balíčky; v podstatě části jsou soubory, které jsou společně ZIP do tvoří balíčku).</span><span class="sxs-lookup"><span data-stu-id="7aee1-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="7aee1-107">Pokud dokument obsahuje odstavce, které jsou naformátované se styly, budou existovat části dokumentů, který obsahuje odstavců, které mají na ně použity styly.</span><span class="sxs-lookup"><span data-stu-id="7aee1-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="7aee1-108">Také bude styl část, která obsahuje stylů, které jsou uvedené v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7aee1-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="7aee1-109">Při přístupu k balíčků, je důležité, to prostřednictvím vztahy mezi částí, nikoli pomocí libovolné cesty.</span><span class="sxs-lookup"><span data-stu-id="7aee1-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="7aee1-110">Tento problém je nad rámec manipulace s obsahu v kurzu WordprocessingML dokumentu, ale příklad programy, které jsou zahrnuté v tomto kurzu ukazují správný přístup.</span><span class="sxs-lookup"><span data-stu-id="7aee1-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="7aee1-111">Dokument, který používá styly</span><span class="sxs-lookup"><span data-stu-id="7aee1-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="7aee1-112">Příklad WordML zobrazen [tvar WordprocessingML dokumenty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md) tématu je velmi jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="7aee1-112">The WordML example presented in the [Shape of WordprocessingML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="7aee1-113">Následující dokument je složitější: má odstavců, které jsou naformátované se styly.</span><span class="sxs-lookup"><span data-stu-id="7aee1-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="7aee1-114">Nejjednodušší způsob, jak kód XML, který tvoří dokument Office Open XML se dá spustit [příklad této výstupy Office otevřít dokument částí XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/example-that-outputs-office-open-xml-document-parts.md).</span><span class="sxs-lookup"><span data-stu-id="7aee1-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="7aee1-115">V následujícím dokumentu, je prvním odstavci styl `Heading1`.</span><span class="sxs-lookup"><span data-stu-id="7aee1-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="7aee1-116">Existuje několik odstavců, které mají výchozí styl.</span><span class="sxs-lookup"><span data-stu-id="7aee1-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="7aee1-117">Existují také počet odstavců, které mají styl `Code`.</span><span class="sxs-lookup"><span data-stu-id="7aee1-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="7aee1-118">Z důvodu této relativní složitost jde zajímavějšího dokumentu analyzovat pomocí technologie LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="7aee1-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="7aee1-119">V těchto odstavcích s jiné než výchozí styly elementy odstavce mít podřízený element s názvem `w:pPr`, která naopak má podřízený element `w:pStyle`.</span><span class="sxs-lookup"><span data-stu-id="7aee1-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="7aee1-120">Tento element má atribut, `w:val`, který obsahuje název stylu.</span><span class="sxs-lookup"><span data-stu-id="7aee1-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="7aee1-121">Pokud odstavce má výchozí styl, znamená to, že element odstavce nemá `w:p.Pr` podřízený element.</span><span class="sxs-lookup"><span data-stu-id="7aee1-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
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
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Heading1" />  
      </w:pPr>  
      <w:r>  
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>The following example prints to the console.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>using System;</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>class Program {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    public static void </w:t>  
      </w:r>  
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">  
        <w:r w:rsidRPr="00876F34">  
          <w:t>Main</w:t>  
        </w:r>  
      </w:smartTag>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>(string[] args) {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    }</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>}</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>This example produces the following output:</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>Hello World</w:t>  
      </w:r>  
    </w:p>  
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">  
      <w:pgSz w:w="12240" w:h="15840" />  
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />  
      <w:cols w:space="720" />  
      <w:docGrid w:linePitch="360" />  
    </w:sectPr>  
  </w:body>  
</w:document>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7aee1-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="7aee1-122">See Also</span></span>  
 [<span data-ttu-id="7aee1-123">Podrobnosti o Office otevřít dokumenty WordprocessingML XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7aee1-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)
