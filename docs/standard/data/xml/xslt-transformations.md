---
title: Transformace XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: 4bbecfbf1b163a9d7bfe6957806095b5b17fbab7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709631"
---
# <a name="xslt-transformations"></a><span data-ttu-id="d6831-102">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="d6831-102">XSLT Transformations</span></span>
<span data-ttu-id="d6831-103">Extensible Stylesheet Language Transformation (XSLT) umožňuje transformovat obsah zdrojového dokumentu XML do jiného dokumentu, který je ve formátu nebo struktuře jiný.</span><span class="sxs-lookup"><span data-stu-id="d6831-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="d6831-104">Můžete například použít XSLT k transformaci XML do HTML pro použití na webu nebo k transformaci na dokument, který obsahuje pouze pole požadovaná aplikací.</span><span class="sxs-lookup"><span data-stu-id="d6831-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="d6831-105">Tento proces transformace je určen [doporučením XSLT verze 1,0 W3C Transformers (XSLT)](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="d6831-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="d6831-106"><xref:System.Xml.Xsl.XslCompiledTransform> Třída je procesor XSLT v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="d6831-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="d6831-107"><xref:System.Xml.Xsl.XslCompiledTransform> Třída podporuje [doporučení W3C XSLT 1,0](https://www.w3.org/TR/xslt-10/).</span><span class="sxs-lookup"><span data-stu-id="d6831-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6831-108"><xref:System.Xml.Xsl.XslTransform> Třída je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="d6831-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="d6831-109"><xref:System.Xml.Xsl.XslCompiledTransform> Třída je nová implementace modulu XSLT.</span><span class="sxs-lookup"><span data-stu-id="d6831-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="d6831-110">Zahrnuje vylepšení výkonu a nové funkce zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d6831-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="d6831-111">Doporučeným postupem je vytvoření aplikací XSLT pomocí <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="d6831-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6831-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d6831-112">In This Section</span></span>  
 [<span data-ttu-id="d6831-113">Používání třídy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="d6831-113">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="d6831-114">Poskytuje informace o použití <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="d6831-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="d6831-115">Migrace z třídy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d6831-115">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="d6831-116">Popisuje, jak migrovat kód z <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="d6831-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="d6831-117">Kompilátor XSLT (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="d6831-117">XSLT Compiler (xsltc.exe)</span></span>](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="d6831-118">Poskytuje informace o použití kompilátoru XSLT.</span><span class="sxs-lookup"><span data-stu-id="d6831-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="d6831-119">Transformace XSLT s třídou XslTransform</span><span class="sxs-lookup"><span data-stu-id="d6831-119">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="d6831-120">Poskytuje informace o použití <xref:System.Xml.Xsl.XslTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="d6831-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d6831-121">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="d6831-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="d6831-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d6831-122">Related Sections</span></span>  
 [<span data-ttu-id="d6831-123">Dokumenty a data XML</span><span class="sxs-lookup"><span data-stu-id="d6831-123">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
