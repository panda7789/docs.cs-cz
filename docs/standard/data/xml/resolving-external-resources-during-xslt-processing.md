---
title: Překlad externích prostředků během zpracování XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: 58407d5f0c6e602af15f5b19b9a19cc6379b9af7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710281"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="621da-102">Překlad externích prostředků během zpracování XSLT</span><span class="sxs-lookup"><span data-stu-id="621da-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="621da-103">V případě transformace XSLT může být několikrát nutné přeložit externí prostředky.</span><span class="sxs-lookup"><span data-stu-id="621da-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="621da-104">Použití třídy objekt XmlResolver</span><span class="sxs-lookup"><span data-stu-id="621da-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="621da-105"><xref:System.Xml.XmlResolver> Třída se používá k překladu externích prostředků.</span><span class="sxs-lookup"><span data-stu-id="621da-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="621da-106">Následující tabulka popisuje, kdy se <xref:System.Xml.XmlResolver> během zpracování XSLT stala zahrnuta.</span><span class="sxs-lookup"><span data-stu-id="621da-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="621da-107">Úloha XSLT</span><span class="sxs-lookup"><span data-stu-id="621da-107">XSLT task</span></span>|<span data-ttu-id="621da-108">K čemu se objekt XmlResolver používá</span><span class="sxs-lookup"><span data-stu-id="621da-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="621da-109">Zkompilujte šablonu stylů.</span><span class="sxs-lookup"><span data-stu-id="621da-109">Compile the style sheet.</span></span>|<span data-ttu-id="621da-110">Vyřešte identifikátor URI pro šablonu stylů.</span><span class="sxs-lookup"><span data-stu-id="621da-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="621da-111">ani</span><span class="sxs-lookup"><span data-stu-id="621da-111">-and-</span></span><br /><br /> <span data-ttu-id="621da-112">Přeložit odkazy identifikátoru URI `xsl:import` v `xsl:include` libovolných prvcích nebo.</span><span class="sxs-lookup"><span data-stu-id="621da-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="621da-113">Spusťte šablonu stylů.</span><span class="sxs-lookup"><span data-stu-id="621da-113">Execute the style sheet.</span></span>|<span data-ttu-id="621da-114">Vyřešte identifikátor URI kontextu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="621da-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="621da-115">ani</span><span class="sxs-lookup"><span data-stu-id="621da-115">-and-</span></span><br /><br /> <span data-ttu-id="621da-116">Přeložit odkazy identifikátoru URI v `document()` jakýchkoli funkcích XSLT.</span><span class="sxs-lookup"><span data-stu-id="621da-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="621da-117">Metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> a <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> zahrnují přetížení, která přijímají <xref:System.Xml.XmlResolver> objekt jako jeden z argumentů.</span><span class="sxs-lookup"><span data-stu-id="621da-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="621da-118">Pokud <xref:System.Xml.XmlResolver> není zadaný, použije se výchozí nastavení <xref:System.Xml.XmlUrlResolver> bez přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="621da-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="621da-119">Následující seznam popisuje, kdy možná budete chtít zadat <xref:System.Xml.XmlResolver> objekt:</span><span class="sxs-lookup"><span data-stu-id="621da-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="621da-120">Pokud proces XSLT potřebuje přístup k síťovému prostředku, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebnými přihlašovacími údaji.</span><span class="sxs-lookup"><span data-stu-id="621da-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="621da-121">Pokud chcete omezit prostředky, ke kterým může proces XSLT přistupovat, můžete použít <xref:System.Xml.XmlSecureResolver> se správnou sadou oprávnění.</span><span class="sxs-lookup"><span data-stu-id="621da-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="621da-122">Třídu použijte <xref:System.Xml.XmlSecureResolver> v případě, že potřebujete otevřít prostředek, který neovládáte nebo který není důvěryhodný.</span><span class="sxs-lookup"><span data-stu-id="621da-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="621da-123">Pokud chcete přizpůsobit chování, můžete implementovat vlastní <xref:System.Xml.XmlResolver> třídu a použít ji k řešení prostředků.</span><span class="sxs-lookup"><span data-stu-id="621da-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="621da-124">Pokud chcete zajistit, aby nedošlo k žádnému externímu prostředku, můžete `null` pro <xref:System.Xml.XmlResolver> argument zadat.</span><span class="sxs-lookup"><span data-stu-id="621da-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="621da-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="621da-125">Example</span></span>  
 <span data-ttu-id="621da-126">Následující příklad zkompiluje šablonu stylů uloženou v síťovém prostředku.</span><span class="sxs-lookup"><span data-stu-id="621da-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="621da-127"><xref:System.Xml.XmlUrlResolver> Objekt Určuje pověření nutná pro přístup k šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="621da-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="621da-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="621da-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="621da-129">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="621da-129">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
