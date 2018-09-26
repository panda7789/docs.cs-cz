---
title: Používání třídy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0537685a91db2c0e323b3f1bda24c6cadc264e34
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112478"
---
# <a name="using-the-xslcompiledtransform-class"></a><span data-ttu-id="ca4cb-102">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="ca4cb-102">Using the XslCompiledTransform Class</span></span>
<span data-ttu-id="ca4cb-103"><xref:System.Xml.Xsl.XslCompiledTransform> Procesoru Microsoft .NET Framework XSLT je třída.</span><span class="sxs-lookup"><span data-stu-id="ca4cb-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the Microsoft .NET Framework XSLT processor.</span></span> <span data-ttu-id="ca4cb-104">Tato třída se používá ke kompilaci šablony stylů a provedení transformace XSLT.</span><span class="sxs-lookup"><span data-stu-id="ca4cb-104">This class is used to compile style sheets and execute XSLT transformations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca4cb-105">I když celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třída je lepší, než <xref:System.Xml.Xsl.XslTransform> třídy, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslCompiledTransform> třídy můžou provádět více pomalu než <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslTransform> třída první, když je volán na transformaci.</span><span class="sxs-lookup"><span data-stu-id="ca4cb-105">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="ca4cb-106">Je to proto musí být kompilován soubor XSLT, předtím, než je načten.</span><span class="sxs-lookup"><span data-stu-id="ca4cb-106">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="ca4cb-107">Další informace najdete v následujícím blogovém příspěvku: [XslCompiledTransform pomalejší než XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)</span><span class="sxs-lookup"><span data-stu-id="ca4cb-107">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca4cb-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ca4cb-108">In This Section</span></span>  
 [<span data-ttu-id="ca4cb-109">Vstupy do třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="ca4cb-109">Inputs to the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="ca4cb-110">Popisuje dostupné možnosti vstupu XSLT.</span><span class="sxs-lookup"><span data-stu-id="ca4cb-110">Describes the available XSLT input options.</span></span>  
  
 [<span data-ttu-id="ca4cb-111">Možnosti výstupu na třídě XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="ca4cb-111">Output Options on the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="ca4cb-112">Popisuje dostupné možnosti výstup XSLT.</span><span class="sxs-lookup"><span data-stu-id="ca4cb-112">Describes the available XSLT output options.</span></span>  
  
 [<span data-ttu-id="ca4cb-113">Překlad externích prostředků během zpracování XSLT</span><span class="sxs-lookup"><span data-stu-id="ca4cb-113">Resolving External Resources During XSLT Processing</span></span>](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 <span data-ttu-id="ca4cb-114">Popisuje použití <xref:System.Xml.XmlResolver> třídy k vyřešení externích prostředků.</span><span class="sxs-lookup"><span data-stu-id="ca4cb-114">Discusses using the <xref:System.Xml.XmlResolver> class to resolve external resources.</span></span>  
  
 [<span data-ttu-id="ca4cb-115">Rozšíření šablon stylů XSLT</span><span class="sxs-lookup"><span data-stu-id="ca4cb-115">Extending XSLT Style Sheets</span></span>](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 <span data-ttu-id="ca4cb-116">Tento článek popisuje, jak jsou podporovány přípony XSLT.</span><span class="sxs-lookup"><span data-stu-id="ca4cb-116">Discusses how XSLT extensions are supported.</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="ca4cb-117">Chyby XSLT s možností zotavení</span><span class="sxs-lookup"><span data-stu-id="ca4cb-117">Recoverable XSLT Errors</span></span>](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|<span data-ttu-id="ca4cb-118">Volitelného chování dovolují XSLT World Wide Web Consortium (W3C) 1.0 doporučení uvádí a popisuje, jak jsou zpracovávány těchto projevů <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="ca4cb-118">Lists discretionary behaviors allowed by the World Wide Web Consortium (W3C) XSLT 1.0 recommendation and describes how these behaviors are handled by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>|  
|[<span data-ttu-id="ca4cb-119">Postupy: Transformace fragmentu uzlu</span><span class="sxs-lookup"><span data-stu-id="ca4cb-119">How to: Transform a Node Fragment</span></span>](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|<span data-ttu-id="ca4cb-120">Popisuje, jak transformace fragmentu uzlu.</span><span class="sxs-lookup"><span data-stu-id="ca4cb-120">Describes how to transform a node fragment.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="ca4cb-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ca4cb-121">Related Sections</span></span>  
 [<span data-ttu-id="ca4cb-122">Migrace z třídy XslTransform</span><span class="sxs-lookup"><span data-stu-id="ca4cb-122">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="ca4cb-123">Tento článek popisuje postup migrace kódu z <xref:System.Xml.Xsl.XslTransform> třídy</span><span class="sxs-lookup"><span data-stu-id="ca4cb-123">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca4cb-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca4cb-124">See also</span></span>

- <xref:System.Xml.Xsl.XsltSettings>  
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
