---
title: Objekty rozšíření XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f958af5859804cdeb382adab2f3772c42ac5b16
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483960"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="bfde2-102">Objekty rozšíření XSLT</span><span class="sxs-lookup"><span data-stu-id="bfde2-102">XSLT Extension Objects</span></span>
<span data-ttu-id="bfde2-103">Rozšíření objektů se používají k rozšíření funkcí šablon stylů.</span><span class="sxs-lookup"><span data-stu-id="bfde2-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="bfde2-104">Rozšíření objektů jsou udržovány <xref:System.Xml.Xsl.XsltArgumentList> třídy.</span><span class="sxs-lookup"><span data-stu-id="bfde2-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="bfde2-105">Následují výhody použití objekt rozšíření místo vloženého skriptu:</span><span class="sxs-lookup"><span data-stu-id="bfde2-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="bfde2-106">Poskytuje lepší zapouzdření a opakované použití tříd.</span><span class="sxs-lookup"><span data-stu-id="bfde2-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="bfde2-107">Povoluje stylů, aby bylo menší a jednodušší údržbu.</span><span class="sxs-lookup"><span data-stu-id="bfde2-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="bfde2-108">Objekty rozšíření XSLT se přidají do <xref:System.Xml.Xsl.XsltArgumentList> pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bfde2-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="bfde2-109">Úplný název a identifikátor URI oboru názvů jsou přidruženy k rozšíření objektu v daném čase.</span><span class="sxs-lookup"><span data-stu-id="bfde2-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfde2-110">Sada oprávnění FullTrust je potřeba volat <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bfde2-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="bfde2-111">Další informace najdete v tématu [zabezpečení přístupu kódu](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) a [NIB: pojmenované sady oprávnění](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="bfde2-111">For more information, see [Code Access Security](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="bfde2-112">Datové typy vrácených objektů rozšíření jsou jedním ze čtyř typů základní XPath data z `number`, `string`, `Boolean`, a `node set`.</span><span class="sxs-lookup"><span data-stu-id="bfde2-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="bfde2-113">Jakoukoli metodu, která je definována s `params` klíčové slovo, které umožňuje neurčené počtu parametrů, se aktuálně nepodporují <xref:System.Xml.Xsl.XslCompiledTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="bfde2-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="bfde2-114">XSLT šablony stylů, které využívají jakékoli metody definované `params` – klíčové slovo nebude fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="bfde2-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="bfde2-115">Podrobnosti najdete v tématu [params](~/docs/csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="bfde2-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="bfde2-116">Použití objektu rozšíření XSLT</span><span class="sxs-lookup"><span data-stu-id="bfde2-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="bfde2-117">Vytvoření <xref:System.Xml.Xsl.XsltArgumentList> objektu a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="bfde2-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="bfde2-118">Volání objektu rozšíření ze šablony stylů.</span><span class="sxs-lookup"><span data-stu-id="bfde2-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="bfde2-119">Předání <xref:System.Xml.Xsl.XsltArgumentList> objektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bfde2-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfde2-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfde2-120">See Also</span></span>  
 [<span data-ttu-id="bfde2-121">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="bfde2-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="bfde2-122">Aspekty zabezpečení XSLT</span><span class="sxs-lookup"><span data-stu-id="bfde2-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
