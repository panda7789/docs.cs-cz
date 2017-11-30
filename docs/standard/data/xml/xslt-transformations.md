---
title: Transformace XSLT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0d7fa8492487daff68fd8ebaf4159dd537d13e51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-transformations"></a><span data-ttu-id="6901d-102">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="6901d-102">XSLT Transformations</span></span>
<span data-ttu-id="6901d-103">Šablony stylů transformace XSLT (Extensible Language) umožňuje transformace do jiného dokumentu, který se liší ve formátu nebo struktura obsah zdrojový dokument XML.</span><span class="sxs-lookup"><span data-stu-id="6901d-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="6901d-104">Můžete například XSLT transformace XML do kódu HTML k použití na webu a transformují je na dokument, který obsahuje pouze pole, které jsou vyžadována danou aplikací.</span><span class="sxs-lookup"><span data-stu-id="6901d-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="6901d-105">Tento proces transformace je zadána [doporučení W3C XSL transformace XSLT () verze 1.0](http://go.microsoft.com/fwlink/?LinkID=49919).</span><span class="sxs-lookup"><span data-stu-id="6901d-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](http://go.microsoft.com/fwlink/?LinkID=49919).</span></span>  
  
 <span data-ttu-id="6901d-106"><xref:System.Xml.Xsl.XslCompiledTransform> Třída je procesor XSLT v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6901d-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in the .NET Framework.</span></span> <span data-ttu-id="6901d-107"><xref:System.Xml.Xsl.XslCompiledTransform> Třída podporuje doporučení W3C XSLT 1.0.</span><span class="sxs-lookup"><span data-stu-id="6901d-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the W3C XSLT 1.0 recommendation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6901d-108"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="6901d-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="6901d-109"><xref:System.Xml.Xsl.XslCompiledTransform> Třída je nové implementace modulu XSLT.</span><span class="sxs-lookup"><span data-stu-id="6901d-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="6901d-110">Obsahuje vylepšení výkonu a nové funkce zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6901d-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="6901d-111">Doporučený postup je vytvoření XSLT aplikací pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="6901d-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6901d-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6901d-112">In This Section</span></span>  
 [<span data-ttu-id="6901d-113">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="6901d-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="6901d-114">Poskytuje informace o používání <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="6901d-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="6901d-115">Migrace z XslTransform – třída</span><span class="sxs-lookup"><span data-stu-id="6901d-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="6901d-116">Popisuje, jak do migrace kódu z <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="6901d-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="6901d-117">Kompilátoru XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="6901d-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="6901d-118">Poskytuje informace o používání kompilátoru XSLT.</span><span class="sxs-lookup"><span data-stu-id="6901d-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="6901d-119">Transformace XSLT pomocí XslTransform – třída</span><span class="sxs-lookup"><span data-stu-id="6901d-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="6901d-120">Poskytuje informace o používání <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="6901d-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 <span data-ttu-id="6901d-121">**Poznámka:** <xref:System.Xml.Xsl.XslTransform> třída je zastaralá ve verzi rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="6901d-121">**Note** The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0 release.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6901d-122">Odkaz</span><span class="sxs-lookup"><span data-stu-id="6901d-122">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="6901d-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="6901d-123">Related Sections</span></span>  
 [<span data-ttu-id="6901d-124">XML – dokumenty a Data</span><span class="sxs-lookup"><span data-stu-id="6901d-124">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
