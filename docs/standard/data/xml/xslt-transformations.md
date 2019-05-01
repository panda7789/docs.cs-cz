---
title: Transformace XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 922de11567af9409265ee18bfa6a2637951c57c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026573"
---
# <a name="xslt-transformations"></a><span data-ttu-id="57c90-102">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="57c90-102">XSLT Transformations</span></span>
<span data-ttu-id="57c90-103">Šabloně stylů transformace XSLT (Extensible Language) umožňuje transformovat obsah zdrojovém dokumentu XML do jiného dokumentu, který se liší ve formátu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="57c90-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="57c90-104">Můžete například použít XSLT pro transformaci XML do kódu HTML k použití na webové stránce nebo k transformaci do dokumentu, který obsahuje pouze pole, které jsou vyžadované aplikací.</span><span class="sxs-lookup"><span data-stu-id="57c90-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="57c90-105">Tento proces transformace je určená [doporučení W3C transformace XSL (XSLT) verze 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="57c90-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="57c90-106"><xref:System.Xml.Xsl.XslCompiledTransform> Třída je procesoru XSLT v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="57c90-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="57c90-107"><xref:System.Xml.Xsl.XslCompiledTransform> Třídy podporuje [doporučení W3C XSLT 1.0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="57c90-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57c90-108"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="57c90-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="57c90-109"><xref:System.Xml.Xsl.XslCompiledTransform> Třída je novou implementaci modul XSLT.</span><span class="sxs-lookup"><span data-stu-id="57c90-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="57c90-110">Zahrnuje vylepšení výkonu a nové funkce zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="57c90-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="57c90-111">Doporučeným postupem je vytvoření aplikace XSLT pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="57c90-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="57c90-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="57c90-112">In This Section</span></span>  
 [<span data-ttu-id="57c90-113">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="57c90-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="57c90-114">Poskytuje informace o používání <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="57c90-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="57c90-115">Migrace z třídy XslTransform</span><span class="sxs-lookup"><span data-stu-id="57c90-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="57c90-116">Tento článek popisuje postup migrace kódu z <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="57c90-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="57c90-117">Kompilátor XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="57c90-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="57c90-118">Poskytuje informace o používání kompilátor XSLT.</span><span class="sxs-lookup"><span data-stu-id="57c90-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="57c90-119">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="57c90-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="57c90-120">Poskytuje informace o používání <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="57c90-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="57c90-121">Odkaz</span><span class="sxs-lookup"><span data-stu-id="57c90-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="57c90-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="57c90-122">Related Sections</span></span>  
 [<span data-ttu-id="57c90-123">Dokumenty a data XML</span><span class="sxs-lookup"><span data-stu-id="57c90-123">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
