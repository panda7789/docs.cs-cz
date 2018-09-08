---
title: Dokument WordprocessingML se Styles3
ms.date: 07/20/2015
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: 8b21c9e8be957ea2b43405a96e343cea78197f68
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138582"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="172ec-102">Dokument WordprocessingML se styly</span><span class="sxs-lookup"><span data-stu-id="172ec-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="172ec-103">Složitější dokumentů WordprocessingML mít odstavců, které jsou naformátované se styly.</span><span class="sxs-lookup"><span data-stu-id="172ec-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="172ec-104">Několik poznámky o strukturu dokumentů WordprocessingML jsou užitečné.</span><span class="sxs-lookup"><span data-stu-id="172ec-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="172ec-105">Dokumenty WordprocessingML se ukládají do balíčků.</span><span class="sxs-lookup"><span data-stu-id="172ec-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="172ec-106">Balíčky obsahují více částí (části mají explicitní význam, při použití v souvislosti s balíčky, v podstatě části jsou soubory, které jsou společně ZIP obsahuje balíček).</span><span class="sxs-lookup"><span data-stu-id="172ec-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="172ec-107">Pokud dokument obsahuje odstavců, které jsou naformátované se styly, bude část dokumentu, který obsahuje odstavců, které mají styly použité k nim.</span><span class="sxs-lookup"><span data-stu-id="172ec-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="172ec-108">Také bude součástí styl, který obsahuje styly, které jsou uvedené dokumentu.</span><span class="sxs-lookup"><span data-stu-id="172ec-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="172ec-109">Při přístupu k balíčků, je důležité, můžete to udělat prostřednictvím vztahy mezi částmi, nikoli pomocí libovolného cesty.</span><span class="sxs-lookup"><span data-stu-id="172ec-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="172ec-110">Tento problém je nad rámec manipulace s obsahu v dokumentu WordprocessingML kurzu, ale příklad programy, které jsou zahrnuty v tomto kurzu ukazují správný přístup.</span><span class="sxs-lookup"><span data-stu-id="172ec-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="172ec-111">Dokument, který používá styly</span><span class="sxs-lookup"><span data-stu-id="172ec-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="172ec-112">Příklad WordML zobrazen [tvar WordprocessingML dokumenty (C#)](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md) téma je velmi jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="172ec-112">The WordML example presented in the [Shape of WordprocessingML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="172ec-113">Následující dokument je složitější: má odstavců, které jsou naformátované se styly.</span><span class="sxs-lookup"><span data-stu-id="172ec-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="172ec-114">Nejjednodušší způsob, jak zobrazit, XML, které tvoří dokumentu Office Open XML je spustit [příklad této výstupy Office Open XML části dokumentu (C#)](../../../../csharp/programming-guide/concepts/linq/example-that-outputs-office-open-xml-document-parts.md).</span><span class="sxs-lookup"><span data-stu-id="172ec-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (C#)](../../../../csharp/programming-guide/concepts/linq/example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="172ec-115">V následujícím dokumentu, je prvním odstavci styl `Heading1`.</span><span class="sxs-lookup"><span data-stu-id="172ec-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="172ec-116">Existuje několik bodů, které mají výchozí styl.</span><span class="sxs-lookup"><span data-stu-id="172ec-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="172ec-117">Je také několik bodů, které mají styl `Code`.</span><span class="sxs-lookup"><span data-stu-id="172ec-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="172ec-118">Z důvodu této relativní složitost jde zajímavější dokumentu má být analyzován pomocí LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="172ec-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="172ec-119">V těchto odstavcích s jiné než výchozí styly odstavec elementy mají podřízený element s názvem `w:pPr`, která naopak má podřízený element `w:pStyle`.</span><span class="sxs-lookup"><span data-stu-id="172ec-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="172ec-120">Tento element má atribut, `w:val`, který obsahuje název stylu.</span><span class="sxs-lookup"><span data-stu-id="172ec-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="172ec-121">Pokud výchozí styl odstavce, znamená to, že nemá element odstavce `w:p.Pr` podřízený element.</span><span class="sxs-lookup"><span data-stu-id="172ec-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="172ec-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="172ec-122">See Also</span></span>

- [<span data-ttu-id="172ec-123">Podrobnosti o systému Office otevřít dokumenty XML WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="172ec-123">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)
