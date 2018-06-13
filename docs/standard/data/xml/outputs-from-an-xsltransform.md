---
title: Výstupy z XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd22d59375a46c267c6df70727d9ca52e6843214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571277"
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="cda86-102">Výstupy z XslTransform</span><span class="sxs-lookup"><span data-stu-id="cda86-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="cda86-103">Vzhledem k tomu, že šablony stylů můžete určit formát výstupu pomocí `<xsl:output>` příkaz s `method` atribut, následující tabulka popisuje formát výstupu je, když <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda se používá k zápisu výstupu a formát výstupu se deklarovaný jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="cda86-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cda86-104"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cda86-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="cda86-105">Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="cda86-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="cda86-106">V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="cda86-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="cda86-107">Vzhledem k tomu, že šablony stylů můžete určit formát výstupu pomocí `<xsl:output>` příkaz s `method` atribut, následující tabulka popisuje formát výstupu je, když <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda se používá k zápisu výstupu a formát výstupu se deklarovaný jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="cda86-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="cda86-108">Následující tabulka popisuje, co se stane, když je deklarovaná výstupní typ <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda ve spojení s používáním `<xsl:output>` příkaz:</span><span class="sxs-lookup"><span data-stu-id="cda86-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="cda86-109">\<Metoda elementu xsl: Output = > atribut</span><span class="sxs-lookup"><span data-stu-id="cda86-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="cda86-110">Výsledný formát</span><span class="sxs-lookup"><span data-stu-id="cda86-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="cda86-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="cda86-111">method="xml"</span></span>|<span data-ttu-id="cda86-112">XML</span><span class="sxs-lookup"><span data-stu-id="cda86-112">XML</span></span>|  
|<span data-ttu-id="cda86-113">Metoda = "html"</span><span class="sxs-lookup"><span data-stu-id="cda86-113">method="html"</span></span>|<span data-ttu-id="cda86-114">HTML</span><span class="sxs-lookup"><span data-stu-id="cda86-114">HTML</span></span>|  
|<span data-ttu-id="cda86-115">Metoda = "text"</span><span class="sxs-lookup"><span data-stu-id="cda86-115">method="text"</span></span>|<span data-ttu-id="cda86-116">Text</span><span class="sxs-lookup"><span data-stu-id="cda86-116">Text</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="cda86-117">Poznámka: `<xsl:output>` příkaz se ignoruje při výstup <xref:System.Xml.Xsl.XslTransform.Transform%2A> je metoda <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="cda86-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="cda86-118">Následující atributy jsou podporovány při <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda výstup <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>:</span><span class="sxs-lookup"><span data-stu-id="cda86-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
-   <span data-ttu-id="cda86-119">kódování \*</span><span class="sxs-lookup"><span data-stu-id="cda86-119">encoding\*</span></span>  
  
-   <span data-ttu-id="cda86-120">vynechat Deklarace xml</span><span class="sxs-lookup"><span data-stu-id="cda86-120">omit-xml-declaration</span></span>  
  
-   <span data-ttu-id="cda86-121">samostatný</span><span class="sxs-lookup"><span data-stu-id="cda86-121">standalone</span></span>  
  
-   <span data-ttu-id="cda86-122">veřejná DOCTYPE</span><span class="sxs-lookup"><span data-stu-id="cda86-122">doctype-public</span></span>  
  
-   <span data-ttu-id="cda86-123">DOCTYPE systému</span><span class="sxs-lookup"><span data-stu-id="cda86-123">doctype-system</span></span>  
  
-   <span data-ttu-id="cda86-124">prvky CDATA oddílu</span><span class="sxs-lookup"><span data-stu-id="cda86-124">cdata-section-elements</span></span>  
  
-   <span data-ttu-id="cda86-125">odsazení</span><span class="sxs-lookup"><span data-stu-id="cda86-125">indent</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cda86-126">\* kódování atributu se ignoruje při <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda odesílá výstup do <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="cda86-126">\*the encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="cda86-127">Vlastnost kódování na <xref:System.IO.TextWriter> bude místo něj použita.</span><span class="sxs-lookup"><span data-stu-id="cda86-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>  
  
 <span data-ttu-id="cda86-128">Následující atribut se ignoruje při <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda výstup <xref:System.IO.Stream>:</span><span class="sxs-lookup"><span data-stu-id="cda86-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
-   <span data-ttu-id="cda86-129">verze: verze je vždy 1.0</span><span class="sxs-lookup"><span data-stu-id="cda86-129">version: the version is always 1.0</span></span>  
  
-   <span data-ttu-id="cda86-130">typ média: typ média</span><span class="sxs-lookup"><span data-stu-id="cda86-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="cda86-131">Speciální uvozovací znaky</span><span class="sxs-lookup"><span data-stu-id="cda86-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="cda86-132">`<xsl:text disable-output-escaping>` Značky slouží k označení, zda speciální znaky musí být uvozena do formuláře XML (například pomocí `<&lt>` místě `"<"` symbol) a levé ve stavu, existuje.</span><span class="sxs-lookup"><span data-stu-id="cda86-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="cda86-133">`disable-output-escaping` Atribut se ignoruje, pokud transformace na <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> objektu a nemá žádný vliv na speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="cda86-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda86-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="cda86-134">See Also</span></span>  
 [<span data-ttu-id="cda86-135">Třída XslTransform implementuje procesor XSLT</span><span class="sxs-lookup"><span data-stu-id="cda86-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
