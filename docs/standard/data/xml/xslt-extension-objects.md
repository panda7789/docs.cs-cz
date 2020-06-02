---
title: Objekty rozšíření XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
ms.openlocfilehash: 03e24153cc11c139fc9d9e692ef93bd82c51ee3d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282594"
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="a4960-102">Objekty rozšíření XSLT</span><span class="sxs-lookup"><span data-stu-id="a4960-102">XSLT Extension Objects</span></span>
<span data-ttu-id="a4960-103">Objekty rozšíření slouží k rozšíření funkcí šablon stylů.</span><span class="sxs-lookup"><span data-stu-id="a4960-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="a4960-104">Objekty rozšíření jsou spravovány <xref:System.Xml.Xsl.XsltArgumentList> třídou.</span><span class="sxs-lookup"><span data-stu-id="a4960-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="a4960-105">Níže jsou výhody použití objektu rozšíření místo vloženého skriptu:</span><span class="sxs-lookup"><span data-stu-id="a4960-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
- <span data-ttu-id="a4960-106">Poskytuje lepší zapouzdření a opakované použití tříd.</span><span class="sxs-lookup"><span data-stu-id="a4960-106">Provides better encapsulation and reuse of classes.</span></span>  
  
- <span data-ttu-id="a4960-107">Povoluje, aby byly šablony stylů menší a udržovatelnější.</span><span class="sxs-lookup"><span data-stu-id="a4960-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="a4960-108">Objekty rozšíření XSLT jsou přidány do <xref:System.Xml.Xsl.XsltArgumentList> objektu pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a4960-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="a4960-109">Úplný název a identifikátor URI oboru názvů jsou v daném čase přidruženy k objektu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a4960-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4960-110">Pro volání metody je vyžadována sada oprávnění FullTrust <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="a4960-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="a4960-111">Další informace najdete v tématu [zabezpečení přístupu kódu](../../../framework/misc/code-access-security.md) a [pojmenované sady oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a4960-111">For more information, see [Code Access Security](../../../framework/misc/code-access-security.md) and [Named Permission Sets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="a4960-112">Datové typy vrácené z objektů rozšíření jsou jedním ze čtyř základních datových typů XPath `number` , `string` , `Boolean` a `node set` .</span><span class="sxs-lookup"><span data-stu-id="a4960-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="a4960-113">Všechny metody, které jsou definovány pomocí `params` klíčového slova, které umožňuje předat nespecifikovaný počet parametrů, není aktuálně podporována <xref:System.Xml.Xsl.XslCompiledTransform> třídou.</span><span class="sxs-lookup"><span data-stu-id="a4960-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="a4960-114">Šablony stylů XSLT, které využívají jakoukoli metodu definovanou s `params` klíčovým slovem, nebudou správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="a4960-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="a4960-115">Podrobnosti najdete v tématu [param](../../../csharp/language-reference/keywords/params.md).</span><span class="sxs-lookup"><span data-stu-id="a4960-115">For details, see [params](../../../csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="a4960-116">Použití objektu rozšíření XSLT</span><span class="sxs-lookup"><span data-stu-id="a4960-116">To use an XSLT extension object</span></span>  
  
1. <span data-ttu-id="a4960-117">Vytvořte <xref:System.Xml.Xsl.XsltArgumentList> objekt a přidejte objekt rozšíření pomocí <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a4960-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2. <span data-ttu-id="a4960-118">Zavolejte objekt rozšíření ze seznamu stylů.</span><span class="sxs-lookup"><span data-stu-id="a4960-118">Call the extension object from the style sheet.</span></span>  
  
3. <span data-ttu-id="a4960-119">Předat <xref:System.Xml.Xsl.XsltArgumentList> objekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodě.</span><span class="sxs-lookup"><span data-stu-id="a4960-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4960-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4960-120">See also</span></span>

- [<span data-ttu-id="a4960-121">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="a4960-121">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="a4960-122">Aspekty zabezpečení XSLT</span><span class="sxs-lookup"><span data-stu-id="a4960-122">XSLT Security Considerations</span></span>](xslt-security-considerations.md)
