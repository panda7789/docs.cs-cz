---
title: Používání třídy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 8212e37171ce693ee5624541f7886ef33a33b1da
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710047"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="b3688-102">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="b3688-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="b3688-103">Třída <xref:System.Xml.Xsl.XslCompiledTransform> je procesorem Microsoft .NET Framework XSLT.</span><span class="sxs-lookup"><span data-stu-id="b3688-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="b3688-104">Tato třída se používá ke kompilaci šablon stylů a provádění transformací XSLT.</span><span class="sxs-lookup"><span data-stu-id="b3688-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3688-105">I když je celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třídy lepší než <xref:System.Xml.Xsl.XslTransform> třídy, metoda <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> třídy <xref:System.Xml.Xsl.XslCompiledTransform> může při prvním volání na transformaci pracovat pomaleji než metoda <xref:System.Xml.Xsl.XslTransform.Load%2A> třídy <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="b3688-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="b3688-106">Důvodem je, že soubor XSLT musí být zkompilován před jeho načtením.</span><span class="sxs-lookup"><span data-stu-id="b3688-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="b3688-107">Další informace najdete v tomto blogovém příspěvku: [XslCompiledTransform pomalejší než XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)</span><span class="sxs-lookup"><span data-stu-id="b3688-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3688-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b3688-108">In This Section</span></span>  
 [<span data-ttu-id="b3688-109">Vstupy do třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="b3688-109">Inputs to the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="b3688-110">Popisuje dostupné možnosti vstupu XSLT.</span><span class="sxs-lookup"><span data-stu-id="b3688-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="b3688-111">Možnosti výstupu na třídě XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="b3688-111">Output Options on the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="b3688-112">Popisuje dostupné možnosti výstupu XSLT.</span><span class="sxs-lookup"><span data-stu-id="b3688-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="b3688-113">Překlad externích prostředků během zpracování XSLT</span><span class="sxs-lookup"><span data-stu-id="b3688-113">Resolving External Resources During XSLT Processing</span></span>](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="b3688-114">Popisuje použití třídy <xref:System.Xml.XmlResolver> k překladu externích prostředků.</span><span class="sxs-lookup"><span data-stu-id="b3688-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="b3688-115">Rozšíření šablon stylů XSLT</span><span class="sxs-lookup"><span data-stu-id="b3688-115">Extending XSLT Style Sheets</span></span>](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 <span data-ttu-id="b3688-116">Popisuje, jak jsou podporována rozšíření XSLT.</span><span class="sxs-lookup"><span data-stu-id="b3688-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="b3688-117">Chyby XSLT s možností zotavení</span><span class="sxs-lookup"><span data-stu-id="b3688-117">Recoverable XSLT Errors</span></span>](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|<span data-ttu-id="b3688-118">Uvádí volitelné chování, které povoluje doporučení XSLT 1,0 pro konsorcium World Wide Web (W3C) a popisuje, jak jsou tato chování zpracována <xref:System.Xml.Xsl.XslCompiledTransform> třídou.</span><span class="sxs-lookup"><span data-stu-id="b3688-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="b3688-119">Postupy: Transformace fragmentu uzlu</span><span class="sxs-lookup"><span data-stu-id="b3688-119">How to: Transform a Node Fragment</span></span>](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|<span data-ttu-id="b3688-120">Popisuje, jak transformovat fragment uzlu.</span><span class="sxs-lookup"><span data-stu-id="b3688-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="b3688-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b3688-121">Related Sections</span></span>  
 [<span data-ttu-id="b3688-122">Migrace z třídy XslTransform</span><span class="sxs-lookup"><span data-stu-id="b3688-122">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="b3688-123">Popisuje, jak migrovat kód z <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="b3688-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3688-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3688-124">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
