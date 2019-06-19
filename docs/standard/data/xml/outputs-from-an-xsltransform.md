---
title: Výstupy z XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 383cfbe72d89f4360692f002a7104f7ae0bc0bdc
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170865"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="3ac1e-102">Výstupy z XslTransform</span><span class="sxs-lookup"><span data-stu-id="3ac1e-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="3ac1e-103">Protože šablony stylů můžete určit formát výstupu pomocí `<xsl:output>` příkaz s `method` atributu, jsou popsány v následující tabulce je formát výstupu, kdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda se používá k zápisu výstupu a je výstupní formát deklarovat jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="3ac1e-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ac1e-104"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralé v rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="3ac1e-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="3ac1e-105">Můžete provádět rozšiřitelný jazyk šablony stylů transformace XSLT () transformaci pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="3ac1e-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="3ac1e-106">Zobrazit [používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="3ac1e-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="3ac1e-107">Protože šablony stylů můžete určit formát výstupu pomocí `<xsl:output>` příkaz s `method` atributu, jsou popsány v následující tabulce je formát výstupu, kdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda se používá k zápisu výstupu a je výstupní formát deklarovat jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="3ac1e-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="3ac1e-108">Následující tabulka popisuje, co se stane, když není deklarována typem výstupu <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda ve spojení s použitím `<xsl:output>` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="3ac1e-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="3ac1e-109">\<Metoda elementu xsl: Output = > atribut</span><span class="sxs-lookup"><span data-stu-id="3ac1e-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="3ac1e-110">Výsledný formát</span><span class="sxs-lookup"><span data-stu-id="3ac1e-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="3ac1e-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="3ac1e-111">method="xml"</span></span>|<span data-ttu-id="3ac1e-112">XML</span><span class="sxs-lookup"><span data-stu-id="3ac1e-112">XML</span></span>|  
|<span data-ttu-id="3ac1e-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="3ac1e-113">method="html"</span></span>|<span data-ttu-id="3ac1e-114">HTML</span><span class="sxs-lookup"><span data-stu-id="3ac1e-114">HTML</span></span>|  
|<span data-ttu-id="3ac1e-115">method="text"</span><span class="sxs-lookup"><span data-stu-id="3ac1e-115">method="text"</span></span>|<span data-ttu-id="3ac1e-116">Text</span><span class="sxs-lookup"><span data-stu-id="3ac1e-116">Text</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="3ac1e-117">Poznámka: `<xsl:output>` Příkaz je ignorován při výstupu <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda je <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="3ac1e-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="3ac1e-118">Jsou podporovány následující atributy při <xref:System.Xml.Xsl.XslTransform.Transform%2A> výstupu metody je <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>:</span><span class="sxs-lookup"><span data-stu-id="3ac1e-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
- <span data-ttu-id="3ac1e-119">encoding\*</span><span class="sxs-lookup"><span data-stu-id="3ac1e-119">encoding\*</span></span>  
  
- <span data-ttu-id="3ac1e-120">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="3ac1e-120">omit-xml-declaration</span></span>  
  
- <span data-ttu-id="3ac1e-121">samostatný</span><span class="sxs-lookup"><span data-stu-id="3ac1e-121">standalone</span></span>  
  
- <span data-ttu-id="3ac1e-122">doctype-public</span><span class="sxs-lookup"><span data-stu-id="3ac1e-122">doctype-public</span></span>  
  
- <span data-ttu-id="3ac1e-123">doctype-system</span><span class="sxs-lookup"><span data-stu-id="3ac1e-123">doctype-system</span></span>  
  
- <span data-ttu-id="3ac1e-124">cdata-section-elements</span><span class="sxs-lookup"><span data-stu-id="3ac1e-124">cdata-section-elements</span></span>  
  
- <span data-ttu-id="3ac1e-125">Odsazení</span><span class="sxs-lookup"><span data-stu-id="3ac1e-125">indent</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3ac1e-126">\* kódování atribut se ignoruje při <xref:System.Xml.Xsl.XslTransform.Transform%2A> odesílá svůj výstup do metody <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="3ac1e-126">\*the encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="3ac1e-127">Vlastnost kódování na <xref:System.IO.TextWriter> místo ní se použije.</span><span class="sxs-lookup"><span data-stu-id="3ac1e-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>  
  
 <span data-ttu-id="3ac1e-128">Tento atribut se ignoruje při <xref:System.Xml.Xsl.XslTransform.Transform%2A> výstupu metody je <xref:System.IO.Stream>:</span><span class="sxs-lookup"><span data-stu-id="3ac1e-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
- <span data-ttu-id="3ac1e-129">verze: verze je vždy 1.0</span><span class="sxs-lookup"><span data-stu-id="3ac1e-129">version: the version is always 1.0</span></span>  
  
- <span data-ttu-id="3ac1e-130">typ média: typ média</span><span class="sxs-lookup"><span data-stu-id="3ac1e-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="3ac1e-131">Speciální uvozovací znaky</span><span class="sxs-lookup"><span data-stu-id="3ac1e-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="3ac1e-132">`<xsl:text disable-output-escaping>` Značka se používá k označení, zda musí být do formuláře XML uvozeny řídicími znaky speciální znaky (například pomocí `<&lt>` místo `"<"` symbol) nebo left ve přítomna podmínka.</span><span class="sxs-lookup"><span data-stu-id="3ac1e-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="3ac1e-133">`disable-output-escaping` Atribut se ignoruje při transformování do <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> objektů a nemá žádný vliv na speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="3ac1e-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac1e-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ac1e-134">See also</span></span>

- [<span data-ttu-id="3ac1e-135">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="3ac1e-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
