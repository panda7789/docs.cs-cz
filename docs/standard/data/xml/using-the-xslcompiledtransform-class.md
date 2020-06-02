---
title: Používání třídy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 8705b4c6324ce20a1f37d3ee864ab494adcdd6a5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281764"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="e1d2e-102">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="e1d2e-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="e1d2e-103"><xref:System.Xml.Xsl.XslCompiledTransform>Třída je procesorem Microsoft .NET Framework XSLT.</span><span class="sxs-lookup"><span data-stu-id="e1d2e-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="e1d2e-104">Tato třída se používá ke kompilaci šablon stylů a provádění transformací XSLT.</span><span class="sxs-lookup"><span data-stu-id="e1d2e-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1d2e-105">I když je celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třídy lepší než <xref:System.Xml.Xsl.XslTransform> třída, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslCompiledTransform> třídy může při prvním volání transformace pracovat pomaleji než <xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="e1d2e-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="e1d2e-106">Důvodem je, že soubor XSLT musí být zkompilován před jeho načtením.</span><span class="sxs-lookup"><span data-stu-id="e1d2e-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="e1d2e-107">Další informace najdete v tomto blogovém příspěvku: [XslCompiledTransform pomalejší než XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span><span class="sxs-lookup"><span data-stu-id="e1d2e-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1d2e-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e1d2e-108">In This Section</span></span>  
 [<span data-ttu-id="e1d2e-109">Vstupy do třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="e1d2e-109">Inputs to the XslCompiledTransform Class</span></span>](inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="e1d2e-110">Popisuje dostupné možnosti vstupu XSLT.</span><span class="sxs-lookup"><span data-stu-id="e1d2e-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="e1d2e-111">Možnosti výstupu na třídě XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="e1d2e-111">Output Options on the XslCompiledTransform Class</span></span>](output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="e1d2e-112">Popisuje dostupné možnosti výstupu XSLT.</span><span class="sxs-lookup"><span data-stu-id="e1d2e-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="e1d2e-113">Překlad externích prostředků během zpracování XSLT</span><span class="sxs-lookup"><span data-stu-id="e1d2e-113">Resolving External Resources During XSLT Processing</span></span>](resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="e1d2e-114">Popisuje použití <xref:System.Xml.XmlResolver> třídy k překladu externích prostředků.</span><span class="sxs-lookup"><span data-stu-id="e1d2e-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="e1d2e-115">Rozšíření šablon stylů XSLT</span><span class="sxs-lookup"><span data-stu-id="e1d2e-115">Extending XSLT Style Sheets</span></span>](extending-xslt-style-sheets.md)  
 <span data-ttu-id="e1d2e-116">Popisuje, jak jsou podporována rozšíření XSLT.</span><span class="sxs-lookup"><span data-stu-id="e1d2e-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="e1d2e-117">Chyby XSLT s možností zotavení</span><span class="sxs-lookup"><span data-stu-id="e1d2e-117">Recoverable XSLT Errors</span></span>](recoverable-xslt-errors.md)|<span data-ttu-id="e1d2e-118">Uvádí volitelné chování, které povoluje doporučení konsorcium World Wide Web (W3C) XSLT 1,0, a popisuje, jak toto chování zpracovává <xref:System.Xml.Xsl.XslCompiledTransform> Třída.</span><span class="sxs-lookup"><span data-stu-id="e1d2e-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="e1d2e-119">Postupy: Transformace fragmentu uzlu</span><span class="sxs-lookup"><span data-stu-id="e1d2e-119">How to: Transform a Node Fragment</span></span>](how-to-transform-a-node-fragment.md)|<span data-ttu-id="e1d2e-120">Popisuje, jak transformovat fragment uzlu.</span><span class="sxs-lookup"><span data-stu-id="e1d2e-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="e1d2e-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e1d2e-121">Related Sections</span></span>  
 [<span data-ttu-id="e1d2e-122">Migrace z třídy XslTransform</span><span class="sxs-lookup"><span data-stu-id="e1d2e-122">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="e1d2e-123">Popisuje, jak migrovat kód z <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="e1d2e-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d2e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1d2e-124">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
