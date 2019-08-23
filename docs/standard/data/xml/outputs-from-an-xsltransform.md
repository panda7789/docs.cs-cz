---
title: Výstupy z XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a6c2ea2fe2f02dc1897cb1348f4c2585b730036
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924958"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="8c888-102">Výstupy z XslTransform</span><span class="sxs-lookup"><span data-stu-id="8c888-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="8c888-103">Vzhledem k tomu, že šablony stylů mohou určit výstupní `<xsl:output>` formát pomocí příkazu `method` s atributem, následující tabulka popisuje, co je <xref:System.Xml.Xsl.XslTransform.Transform%2A> výstupní formát při použití metody k zápisu výstupu a výstupní formát je deklarováno jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="8c888-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c888-104"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="8c888-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="8c888-105">Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="8c888-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="8c888-106">Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="8c888-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="8c888-107">Vzhledem k tomu, že šablony stylů mohou určit výstupní `<xsl:output>` formát pomocí příkazu `method` s atributem, následující tabulka popisuje, co je <xref:System.Xml.Xsl.XslTransform.Transform%2A> výstupní formát při použití metody k zápisu výstupu a výstupní formát je deklarováno jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="8c888-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="8c888-108">Následující tabulka popisuje, co se stane, když je typ výstupu deklarován <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodou ve spojení s použitím `<xsl:output>` příkazu:</span><span class="sxs-lookup"><span data-stu-id="8c888-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="8c888-109">\<XSL: Output – metoda = > – atribut</span><span class="sxs-lookup"><span data-stu-id="8c888-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="8c888-110">Výsledný formát</span><span class="sxs-lookup"><span data-stu-id="8c888-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="8c888-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="8c888-111">method="xml"</span></span>|<span data-ttu-id="8c888-112">XML</span><span class="sxs-lookup"><span data-stu-id="8c888-112">XML</span></span>|  
|<span data-ttu-id="8c888-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="8c888-113">method="html"</span></span>|<span data-ttu-id="8c888-114">HTML</span><span class="sxs-lookup"><span data-stu-id="8c888-114">HTML</span></span>|  
|<span data-ttu-id="8c888-115">method="text"</span><span class="sxs-lookup"><span data-stu-id="8c888-115">method="text"</span></span>|<span data-ttu-id="8c888-116">Text</span><span class="sxs-lookup"><span data-stu-id="8c888-116">Text</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="8c888-117">Poznámka: Příkaz je ignorován, pokud <xref:System.Xml.XmlReader> je výstupem <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody nebo <xref:System.Xml.XmlWriter>. `<xsl:output>`</span><span class="sxs-lookup"><span data-stu-id="8c888-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="8c888-118">Následující atributy jsou podporovány, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> <xref:System.IO.Stream> je výstupem metody nebo <xref:System.IO.TextWriter>:</span><span class="sxs-lookup"><span data-stu-id="8c888-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="8c888-119">kódování</span><span class="sxs-lookup"><span data-stu-id="8c888-119">encoding\*</span></span>  
  
- <span data-ttu-id="8c888-120">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="8c888-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="8c888-121">samostatný</span><span class="sxs-lookup"><span data-stu-id="8c888-121">standalone</span></span>  
  
- <span data-ttu-id="8c888-122">DOCTYPE – veřejné</span><span class="sxs-lookup"><span data-stu-id="8c888-122">doctype-public</span></span>  
  
- <span data-ttu-id="8c888-123">DOCTYPE – systém</span><span class="sxs-lookup"><span data-stu-id="8c888-123">doctype-system</span></span>  
  
- <span data-ttu-id="8c888-124">CDATA-Section-Elements</span><span class="sxs-lookup"><span data-stu-id="8c888-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="8c888-125">rážce</span><span class="sxs-lookup"><span data-stu-id="8c888-125">indent</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8c888-126">\*Atribut Encoding je ignorován, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda posílá svůj výstup <xref:System.IO.TextWriter>do.</span><span class="sxs-lookup"><span data-stu-id="8c888-126">\*The encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="8c888-127">Místo toho se použije vlastnost <xref:System.IO.TextWriter> Encoding v.</span><span class="sxs-lookup"><span data-stu-id="8c888-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span> 
  
 <span data-ttu-id="8c888-128">Následující atribut je ignorován, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> <xref:System.IO.Stream>je výstupem metody:</span><span class="sxs-lookup"><span data-stu-id="8c888-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="8c888-129">verze: verze je vždycky 1,0.</span><span class="sxs-lookup"><span data-stu-id="8c888-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="8c888-130">typ média: typ média</span><span class="sxs-lookup"><span data-stu-id="8c888-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="8c888-131">Speciální znaky pro uvozovací znaky</span><span class="sxs-lookup"><span data-stu-id="8c888-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="8c888-132">Tato `<xsl:text disable-output-escaping>` značka slouží k označení, zda je nutné zadat speciální znaky do formuláře XML (například pomocí `<&lt>` místo `"<"` symbolu) nebo vlevo v aktuální podmínce.</span><span class="sxs-lookup"><span data-stu-id="8c888-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="8c888-133">Atribut je ignorován při transformaci <xref:System.Xml.XmlReader> na objekt nebo <xref:System.Xml.XmlWriter> a nemá žádný vliv na speciální znaky. `disable-output-escaping`</span><span class="sxs-lookup"><span data-stu-id="8c888-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c888-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c888-134">See also</span></span>

- [<span data-ttu-id="8c888-135">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="8c888-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
