---
title: Překlad externích prostředků během zpracování XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: d38aea1a54c93b00ec14c6aac7ed11ceba288f7b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291497"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="c6642-102">Překlad externích prostředků během zpracování XSLT</span><span class="sxs-lookup"><span data-stu-id="c6642-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="c6642-103">V případě transformace XSLT může být několikrát nutné přeložit externí prostředky.</span><span class="sxs-lookup"><span data-stu-id="c6642-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="c6642-104">Použití třídy objekt XmlResolver</span><span class="sxs-lookup"><span data-stu-id="c6642-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="c6642-105"><xref:System.Xml.XmlResolver>Třída se používá k překladu externích prostředků.</span><span class="sxs-lookup"><span data-stu-id="c6642-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="c6642-106">Následující tabulka popisuje, kdy se <xref:System.Xml.XmlResolver> během zpracování XSLT stala zahrnuta.</span><span class="sxs-lookup"><span data-stu-id="c6642-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="c6642-107">Úloha XSLT</span><span class="sxs-lookup"><span data-stu-id="c6642-107">XSLT task</span></span>|<span data-ttu-id="c6642-108">K čemu se objekt XmlResolver používá</span><span class="sxs-lookup"><span data-stu-id="c6642-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="c6642-109">Zkompilujte šablonu stylů.</span><span class="sxs-lookup"><span data-stu-id="c6642-109">Compile the style sheet.</span></span>|<span data-ttu-id="c6642-110">Vyřešte identifikátor URI pro šablonu stylů.</span><span class="sxs-lookup"><span data-stu-id="c6642-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="c6642-111">ani</span><span class="sxs-lookup"><span data-stu-id="c6642-111">-and-</span></span><br /><br /> <span data-ttu-id="c6642-112">Přeložit odkazy identifikátoru URI v libovolných `xsl:import` `xsl:include` prvcích nebo.</span><span class="sxs-lookup"><span data-stu-id="c6642-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="c6642-113">Spusťte šablonu stylů.</span><span class="sxs-lookup"><span data-stu-id="c6642-113">Execute the style sheet.</span></span>|<span data-ttu-id="c6642-114">Vyřešte identifikátor URI kontextu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c6642-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="c6642-115">ani</span><span class="sxs-lookup"><span data-stu-id="c6642-115">-and-</span></span><br /><br /> <span data-ttu-id="c6642-116">Přeložit odkazy identifikátoru URI v jakýchkoli `document()` funkcích XSLT.</span><span class="sxs-lookup"><span data-stu-id="c6642-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="c6642-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>Metody a <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> zahrnují přetížení, která přijímají <xref:System.Xml.XmlResolver> objekt jako jeden z argumentů.</span><span class="sxs-lookup"><span data-stu-id="c6642-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="c6642-118">Pokud <xref:System.Xml.XmlResolver> není zadaný, použije se výchozí nastavení <xref:System.Xml.XmlUrlResolver> bez přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="c6642-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="c6642-119">Následující seznam popisuje, kdy možná budete chtít zadat <xref:System.Xml.XmlResolver> objekt:</span><span class="sxs-lookup"><span data-stu-id="c6642-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="c6642-120">Pokud proces XSLT potřebuje přístup k síťovému prostředku, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebnými přihlašovacími údaji.</span><span class="sxs-lookup"><span data-stu-id="c6642-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="c6642-121">Pokud chcete omezit prostředky, ke kterým může proces XSLT přistupovat, můžete použít <xref:System.Xml.XmlSecureResolver> se správnou sadou oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c6642-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="c6642-122">Třídu použijte v případě, že <xref:System.Xml.XmlSecureResolver> potřebujete otevřít prostředek, který neovládáte nebo který není důvěryhodný.</span><span class="sxs-lookup"><span data-stu-id="c6642-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="c6642-123">Pokud chcete přizpůsobit chování, můžete implementovat vlastní <xref:System.Xml.XmlResolver> třídu a použít ji k řešení prostředků.</span><span class="sxs-lookup"><span data-stu-id="c6642-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="c6642-124">Pokud chcete zajistit, aby nedošlo k žádnému externímu prostředku, můžete `null` pro <xref:System.Xml.XmlResolver> argument zadat.</span><span class="sxs-lookup"><span data-stu-id="c6642-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6642-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6642-125">Example</span></span>  
 <span data-ttu-id="c6642-126">Následující příklad zkompiluje šablonu stylů uloženou v síťovém prostředku.</span><span class="sxs-lookup"><span data-stu-id="c6642-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="c6642-127"><xref:System.Xml.XmlUrlResolver>Objekt Určuje pověření nutná pro přístup k šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="c6642-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="c6642-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6642-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="c6642-129">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="c6642-129">XSLT Transformations</span></span>](xslt-transformations.md)
