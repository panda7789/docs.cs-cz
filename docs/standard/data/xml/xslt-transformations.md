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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 63c73fc48d0beaeb3a77acc464734b11410467a0
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2018
---
# <a name="xslt-transformations"></a><span data-ttu-id="9078f-102">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="9078f-102">XSLT Transformations</span></span>
<span data-ttu-id="9078f-103">Šablony stylů transformace XSLT (Extensible Language) umožňuje transformace do jiného dokumentu, který se liší ve formátu nebo struktura obsah zdrojový dokument XML.</span><span class="sxs-lookup"><span data-stu-id="9078f-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="9078f-104">Můžete například XSLT transformace XML do kódu HTML k použití na webu a transformují je na dokument, který obsahuje pouze pole, které jsou vyžadována danou aplikací.</span><span class="sxs-lookup"><span data-stu-id="9078f-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="9078f-105">Tento proces transformace je zadána [doporučení W3C XSL transformace XSLT () verze 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="9078f-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="9078f-106"><xref:System.Xml.Xsl.XslCompiledTransform> Třída je procesor XSLT v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="9078f-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="9078f-107"><xref:System.Xml.Xsl.XslCompiledTransform> Třídy podporuje [doporučení W3C XSLT 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="9078f-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9078f-108"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="9078f-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="9078f-109"><xref:System.Xml.Xsl.XslCompiledTransform> Třída je nové implementace modulu XSLT.</span><span class="sxs-lookup"><span data-stu-id="9078f-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="9078f-110">Obsahuje vylepšení výkonu a nové funkce zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9078f-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="9078f-111">Doporučený postup je vytvoření XSLT aplikací pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="9078f-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9078f-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9078f-112">In This Section</span></span>  
 [<span data-ttu-id="9078f-113">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="9078f-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="9078f-114">Poskytuje informace o používání <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="9078f-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="9078f-115">Migrace z třídy XslTransform</span><span class="sxs-lookup"><span data-stu-id="9078f-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="9078f-116">Popisuje, jak do migrace kódu z <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="9078f-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="9078f-117">Kompilátor XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="9078f-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="9078f-118">Poskytuje informace o používání kompilátoru XSLT.</span><span class="sxs-lookup"><span data-stu-id="9078f-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="9078f-119">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="9078f-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="9078f-120">Poskytuje informace o používání <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="9078f-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9078f-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="9078f-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="9078f-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9078f-122">Related Sections</span></span>  
 [<span data-ttu-id="9078f-123">Dokumenty a data XML</span><span class="sxs-lookup"><span data-stu-id="9078f-123">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
