---
title: "Rozšíření objektů XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2916f7da6b990cddef9b86559a71b5206351d558
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="59b9a-102">Rozšíření objektů XSLT</span><span class="sxs-lookup"><span data-stu-id="59b9a-102">XSLT Extension Objects</span></span>
<span data-ttu-id="59b9a-103">Rozšíření objektů se používají k rozšíření funkcí stylů.</span><span class="sxs-lookup"><span data-stu-id="59b9a-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="59b9a-104">Rozšíření objektů jsou udržované <xref:System.Xml.Xsl.XsltArgumentList> třídy.</span><span class="sxs-lookup"><span data-stu-id="59b9a-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="59b9a-105">Následují výhody použití rozšíření namísto objektu vložený skript:</span><span class="sxs-lookup"><span data-stu-id="59b9a-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="59b9a-106">Poskytuje lepší zapouzdření a opakovaného použití třídy.</span><span class="sxs-lookup"><span data-stu-id="59b9a-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="59b9a-107">Umožňuje stylů menší a více udržovatelný.</span><span class="sxs-lookup"><span data-stu-id="59b9a-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="59b9a-108">XSLT rozšíření objekty jsou přidány na <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="59b9a-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="59b9a-109">Úplný název a identifikátor URI oboru názvů jsou přidruženy k rozšíření objektu v daném čase.</span><span class="sxs-lookup"><span data-stu-id="59b9a-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59b9a-110">Sada oprávnění FullTrust je třeba volat <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="59b9a-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="59b9a-111">Další informace najdete v tématu [zabezpečení přístupu kódu](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03) a [NIB: pojmenované sady oprávnění](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="59b9a-111">For more information, see [Code Access Security](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="59b9a-112">Datové typy vrácených objektů rozšíření jsou jedním ze čtyř typů základní XPath data z `number`, `string`, `Boolean`, a `node set`.</span><span class="sxs-lookup"><span data-stu-id="59b9a-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="59b9a-113">Libovolné metody, která je definovaná pomocí `params` – klíčové slovo, která umožňuje neurčené počet parametrů, není aktuálně podporována <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="59b9a-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="59b9a-114">Šablony stylů XSLT, které využívají jakékoli metody definované s `params` – klíčové slovo nebude pracovat správně.</span><span class="sxs-lookup"><span data-stu-id="59b9a-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="59b9a-115">Podrobnosti najdete v tématu [parametry](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="59b9a-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="59b9a-116">Chcete-li použít objekt XSLT rozšíření</span><span class="sxs-lookup"><span data-stu-id="59b9a-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="59b9a-117">Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> objektu a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="59b9a-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="59b9a-118">Volání objektu rozšíření z této šablony.</span><span class="sxs-lookup"><span data-stu-id="59b9a-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="59b9a-119">Předat <xref:System.Xml.Xsl.XsltArgumentList> do objektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="59b9a-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b9a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="59b9a-120">See Also</span></span>  
 [<span data-ttu-id="59b9a-121">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="59b9a-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="59b9a-122">Aspekty zabezpečení XSLT</span><span class="sxs-lookup"><span data-stu-id="59b9a-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
