---
title: "Výstupy z XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 92bf2d7184ca2eb8b17c1d83130c66d1f33f0483
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="f1394-102">Výstupy z XslTransform</span><span class="sxs-lookup"><span data-stu-id="f1394-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="f1394-103">Vzhledem k tomu, že šablony stylů můžete určit formát výstupu pomocí `<xsl:output>` příkaz s `method` atribut, následující tabulka popisuje formát výstupu je, když <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda se používá k zápisu výstupu a formát výstupu se deklarovaný jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="f1394-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1394-104"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1394-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="f1394-105">Můžete provést jazyk XSL pro transformace transformace XSLT () pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="f1394-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="f1394-106">V tématu [pomocí třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="f1394-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="f1394-107">Vzhledem k tomu, že šablony stylů můžete určit formát výstupu pomocí `<xsl:output>` příkaz s `method` atribut, následující tabulka popisuje formát výstupu je, když <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda se používá k zápisu výstupu a formát výstupu se deklarovaný jako <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="f1394-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="f1394-108">Následující tabulka popisuje, co se stane, když je deklarovaná výstupní typ <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda ve spojení s používáním `<xsl:output>` příkaz:</span><span class="sxs-lookup"><span data-stu-id="f1394-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="f1394-109">\<Metoda elementu xsl: Output = > atribut</span><span class="sxs-lookup"><span data-stu-id="f1394-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="f1394-110">Výsledný formát</span><span class="sxs-lookup"><span data-stu-id="f1394-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="f1394-111">Metoda = "xml"</span><span class="sxs-lookup"><span data-stu-id="f1394-111">method="xml"</span></span>|<span data-ttu-id="f1394-112">XML</span><span class="sxs-lookup"><span data-stu-id="f1394-112">XML</span></span>|  
|<span data-ttu-id="f1394-113">Metoda = "html"</span><span class="sxs-lookup"><span data-stu-id="f1394-113">method="html"</span></span>|<span data-ttu-id="f1394-114">HTML</span><span class="sxs-lookup"><span data-stu-id="f1394-114">HTML</span></span>|  
|<span data-ttu-id="f1394-115">Metoda = "text"</span><span class="sxs-lookup"><span data-stu-id="f1394-115">method="text"</span></span>|<span data-ttu-id="f1394-116">Text</span><span class="sxs-lookup"><span data-stu-id="f1394-116">Text</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f1394-117">Poznámka: `<xsl:output>` příkaz se ignoruje při výstup <xref:System.Xml.Xsl.XslTransform.Transform%2A> je metoda <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="f1394-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="f1394-118">Následující atributy jsou podporovány při <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda výstup <xref:System.IO.Stream> nebo <xref:System.IO.TextWriter>:</span><span class="sxs-lookup"><span data-stu-id="f1394-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
-   <span data-ttu-id="f1394-119">kódování *</span><span class="sxs-lookup"><span data-stu-id="f1394-119">encoding*</span></span>  
  
-   <span data-ttu-id="f1394-120">vynechat Deklarace xml</span><span class="sxs-lookup"><span data-stu-id="f1394-120">omit-xml-declaration</span></span>  
  
-   <span data-ttu-id="f1394-121">samostatný</span><span class="sxs-lookup"><span data-stu-id="f1394-121">standalone</span></span>  
  
-   <span data-ttu-id="f1394-122">veřejná DOCTYPE</span><span class="sxs-lookup"><span data-stu-id="f1394-122">doctype-public</span></span>  
  
-   <span data-ttu-id="f1394-123">DOCTYPE systému</span><span class="sxs-lookup"><span data-stu-id="f1394-123">doctype-system</span></span>  
  
-   <span data-ttu-id="f1394-124">prvky CDATA oddílu</span><span class="sxs-lookup"><span data-stu-id="f1394-124">cdata-section-elements</span></span>  
  
-   <span data-ttu-id="f1394-125">odsazení</span><span class="sxs-lookup"><span data-stu-id="f1394-125">indent</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f1394-126">* kódování atributu se ignoruje při <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda odesílá výstup do <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="f1394-126">*the encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="f1394-127">Vlastnost kódování na <xref:System.IO.TextWriter> bude místo něj použita.</span><span class="sxs-lookup"><span data-stu-id="f1394-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>  
  
 <span data-ttu-id="f1394-128">Následující atribut se ignoruje při <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda výstup <xref:System.IO.Stream>:</span><span class="sxs-lookup"><span data-stu-id="f1394-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
-   <span data-ttu-id="f1394-129">verze: verze je vždy 1.0</span><span class="sxs-lookup"><span data-stu-id="f1394-129">version: the version is always 1.0</span></span>  
  
-   <span data-ttu-id="f1394-130">typ média: typ média</span><span class="sxs-lookup"><span data-stu-id="f1394-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="f1394-131">Speciální uvozovací znaky</span><span class="sxs-lookup"><span data-stu-id="f1394-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="f1394-132">`<xsl:text disable-output-escaping>` Značky slouží k označení, zda speciální znaky musí být uvozena do formuláře XML (například pomocí `<&lt>` místě `"<"` symbol) a levé ve stavu, existuje.</span><span class="sxs-lookup"><span data-stu-id="f1394-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="f1394-133">`disable-output-escaping` Atribut se ignoruje, pokud transformace na <xref:System.Xml.XmlReader> nebo <xref:System.Xml.XmlWriter> objektu a nemá žádný vliv na speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="f1394-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1394-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1394-134">See Also</span></span>  
 [<span data-ttu-id="f1394-135">Třída XslTransform implementuje procesoru XSLT</span><span class="sxs-lookup"><span data-stu-id="f1394-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
