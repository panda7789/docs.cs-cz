---
title: WordprocessingML Dokument se styly3
ms.date: 07/20/2015
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: 10697744680276a40fb7a175e4c04920c9e3c243
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167865"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="5403b-102">Dokument WordprocessingML se styly</span><span class="sxs-lookup"><span data-stu-id="5403b-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="5403b-103">Složitější wordprocessingML dokumenty mají odstavce, které jsou formátovány styly.</span><span class="sxs-lookup"><span data-stu-id="5403b-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="5403b-104">Několik poznámek o složení dokumentů WordprocessingML je užitečné.</span><span class="sxs-lookup"><span data-stu-id="5403b-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="5403b-105">WordprocessingML dokumenty jsou uloženy v balíčcích.</span><span class="sxs-lookup"><span data-stu-id="5403b-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="5403b-106">Balíčky mají více částí (části mají explicitní význam při použití v kontextu balíčků; v podstatě, části jsou soubory, které jsou zip dohromady, aby obsahovaly balíček).</span><span class="sxs-lookup"><span data-stu-id="5403b-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="5403b-107">Pokud dokument obsahuje odstavce formátované styly, bude existovat část dokumentu, která obsahuje odstavce, na které jsou použity styly.</span><span class="sxs-lookup"><span data-stu-id="5403b-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="5403b-108">K dispozici bude také část stylu, která obsahuje styly, které jsou odkazovány v dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5403b-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="5403b-109">Při přístupu k balíčkům je důležité, abyste tak učinili prostřednictvím vztahů mezi částmi, nikoli pomocí libovolné cesty.</span><span class="sxs-lookup"><span data-stu-id="5403b-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="5403b-110">Tento problém je nad rámec manipulace s obsahem v kurzu dokumentu WordprocessingML, ale příklad programy, které jsou zahrnuty v tomto kurzu ukazují správný přístup.</span><span class="sxs-lookup"><span data-stu-id="5403b-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="5403b-111">Dokument, který používá styly</span><span class="sxs-lookup"><span data-stu-id="5403b-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="5403b-112">Příklad WordML prezentovaný v [tématu Shape of WordprocessingML Documents (C#)](./shape-of-wordprocessingml-documents.md) je velmi jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="5403b-112">The WordML example presented in the [Shape of WordprocessingML Documents (C#)](./shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="5403b-113">Následující dokument je složitější: Obsahuje odstavce, které jsou formátovány styly.</span><span class="sxs-lookup"><span data-stu-id="5403b-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="5403b-114">Nejjednodušší způsob, jak zobrazit xml, který tvoří dokument Office Open XML, je spustit [příklad, který vypisuje části dokumentů Office Open XML (C#)](./example-that-outputs-office-open-xml-document-parts.md).</span><span class="sxs-lookup"><span data-stu-id="5403b-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (C#)](./example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="5403b-115">V následujícím dokumentu má první odstavec styl `Heading1`.</span><span class="sxs-lookup"><span data-stu-id="5403b-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="5403b-116">Existuje několik odstavců, které mají výchozí styl.</span><span class="sxs-lookup"><span data-stu-id="5403b-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="5403b-117">Existuje také řada odstavců, které `Code`mají styl .</span><span class="sxs-lookup"><span data-stu-id="5403b-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="5403b-118">Z důvodu této relativní složitosti se jedná o zajímavější dokument, který se má analyzovat s linq na XML.</span><span class="sxs-lookup"><span data-stu-id="5403b-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="5403b-119">V těchto odstavcích s nevýchozími styly mají `w:pPr`elementy odstavce podřízený `w:pStyle`prvek s názvem , který má zase podřízený prvek .</span><span class="sxs-lookup"><span data-stu-id="5403b-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="5403b-120">Tento prvek má `w:val`atribut , , který obsahuje název stylu.</span><span class="sxs-lookup"><span data-stu-id="5403b-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="5403b-121">Pokud má odstavec výchozí styl, znamená to, že `w:p.Pr` element odstavce nemá podřízený prvek.</span><span class="sxs-lookup"><span data-stu-id="5403b-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
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
