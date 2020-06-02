---
title: Výstupy z XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 5fa8c8228382f7f326a8d2243ed0450fca31f6fb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288690"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="4eeaf-102">Výstupy z XslTransform</span><span class="sxs-lookup"><span data-stu-id="4eeaf-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="4eeaf-103">Vzhledem k tomu, že šablony stylů mohou určit výstupní formát pomocí `<xsl:output>` příkazu s `method` atributem, následující tabulka popisuje, co je výstupní formát při použití <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody k zápisu výstupu a výstupní formát je deklarován jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter> .</span><span class="sxs-lookup"><span data-stu-id="4eeaf-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4eeaf-104"><xref:System.Xml.Xsl.XslTransform>Třída je zastaralá v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="4eeaf-105">Transformace XSLT (Extensible Stylesheet Language) můžete použít k transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="4eeaf-106">Další informace najdete v tématu [použití třídy XslCompiledTransform](using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="4eeaf-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="4eeaf-107">Vzhledem k tomu, že šablony stylů mohou určit výstupní formát pomocí `<xsl:output>` příkazu s `method` atributem, následující tabulka popisuje, co je výstupní formát při použití <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody k zápisu výstupu a výstupní formát je deklarován jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter> .</span><span class="sxs-lookup"><span data-stu-id="4eeaf-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="4eeaf-108">Následující tabulka popisuje, co se stane, když je typ výstupu deklarován <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodou ve spojení s použitím `<xsl:output>` příkazu:</span><span class="sxs-lookup"><span data-stu-id="4eeaf-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="4eeaf-109">Atribut \<xsl:output method = ></span><span class="sxs-lookup"><span data-stu-id="4eeaf-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="4eeaf-110">Výsledný formát</span><span class="sxs-lookup"><span data-stu-id="4eeaf-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="4eeaf-111">Method = "XML"</span><span class="sxs-lookup"><span data-stu-id="4eeaf-111">method="xml"</span></span>|<span data-ttu-id="4eeaf-112">XML</span><span class="sxs-lookup"><span data-stu-id="4eeaf-112">XML</span></span>|  
|<span data-ttu-id="4eeaf-113">Metoda = "HTML"</span><span class="sxs-lookup"><span data-stu-id="4eeaf-113">method="html"</span></span>|<span data-ttu-id="4eeaf-114">HTML</span><span class="sxs-lookup"><span data-stu-id="4eeaf-114">HTML</span></span>|  
|<span data-ttu-id="4eeaf-115">Method = "text"</span><span class="sxs-lookup"><span data-stu-id="4eeaf-115">method="text"</span></span>|<span data-ttu-id="4eeaf-116">Text</span><span class="sxs-lookup"><span data-stu-id="4eeaf-116">Text</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="4eeaf-117">Poznámka: `<xsl:output>` příkaz je ignorován, pokud je výstupem <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="4eeaf-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="4eeaf-118">Následující atributy jsou podporovány, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> je výstupem metody <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter> :</span><span class="sxs-lookup"><span data-stu-id="4eeaf-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="4eeaf-119">kódování</span><span class="sxs-lookup"><span data-stu-id="4eeaf-119">encoding\*</span></span>  
  
- <span data-ttu-id="4eeaf-120">vynechat – XML-deklarace</span><span class="sxs-lookup"><span data-stu-id="4eeaf-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="4eeaf-121">samostatný</span><span class="sxs-lookup"><span data-stu-id="4eeaf-121">standalone</span></span>  
  
- <span data-ttu-id="4eeaf-122">DOCTYPE – veřejné</span><span class="sxs-lookup"><span data-stu-id="4eeaf-122">doctype-public</span></span>  
  
- <span data-ttu-id="4eeaf-123">DOCTYPE – systém</span><span class="sxs-lookup"><span data-stu-id="4eeaf-123">doctype-system</span></span>  
  
- <span data-ttu-id="4eeaf-124">CDATA-Section-Elements</span><span class="sxs-lookup"><span data-stu-id="4eeaf-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="4eeaf-125">rážce</span><span class="sxs-lookup"><span data-stu-id="4eeaf-125">indent</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4eeaf-126">\*Atribut Encoding je ignorován, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> Metoda posílá svůj výstup do <xref:System.IO.TextWriter> .</span><span class="sxs-lookup"><span data-stu-id="4eeaf-126">\*The encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="4eeaf-127">Místo toho se použije vlastnost Encoding v <xref:System.IO.TextWriter> .</span><span class="sxs-lookup"><span data-stu-id="4eeaf-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>
  
 <span data-ttu-id="4eeaf-128">Následující atribut je ignorován, pokud <xref:System.Xml.Xsl.XslTransform.Transform%2A> je výstupem metody <xref:System.IO.Stream> :</span><span class="sxs-lookup"><span data-stu-id="4eeaf-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="4eeaf-129">verze: verze je vždycky 1,0.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="4eeaf-130">typ média: typ média</span><span class="sxs-lookup"><span data-stu-id="4eeaf-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="4eeaf-131">Speciální znaky pro uvozovací znaky</span><span class="sxs-lookup"><span data-stu-id="4eeaf-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="4eeaf-132">Tato `<xsl:text disable-output-escaping>` značka slouží k označení, zda je nutné zadat speciální znaky do formuláře XML (například pomocí `<&lt>` místo `"<"` symbolu) nebo vlevo v aktuální podmínce.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="4eeaf-133">`disable-output-escaping`Atribut je ignorován při transformaci na <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> objekt nebo a nemá žádný vliv na speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="4eeaf-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eeaf-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="4eeaf-134">See also</span></span>

- [<span data-ttu-id="4eeaf-135">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="4eeaf-135">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
