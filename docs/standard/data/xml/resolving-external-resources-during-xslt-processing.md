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
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="9217c-102">Překlad externích prostředků během zpracování XSLT</span><span class="sxs-lookup"><span data-stu-id="9217c-102">Resolving External Resources During XSLT Processing</span></span>
<span data-ttu-id="9217c-103">V případě transformace XSLT může být několikrát nutné přeložit externí prostředky.</span><span class="sxs-lookup"><span data-stu-id="9217c-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="9217c-104">Použití třídy objekt XmlResolver</span><span class="sxs-lookup"><span data-stu-id="9217c-104">Using the XmlResolver Class</span></span>  
 <span data-ttu-id="9217c-105">Třída <xref:System.Xml.XmlResolver> slouží k překladu externích prostředků.</span><span class="sxs-lookup"><span data-stu-id="9217c-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="9217c-106">Následující tabulka popisuje, kdy se <xref:System.Xml.XmlResolver> během zpracování XSLT zapojí.</span><span class="sxs-lookup"><span data-stu-id="9217c-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="9217c-107">Úloha XSLT</span><span class="sxs-lookup"><span data-stu-id="9217c-107">XSLT task</span></span>|<span data-ttu-id="9217c-108">K čemu se objekt XmlResolver používá</span><span class="sxs-lookup"><span data-stu-id="9217c-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="9217c-109">Zkompilujte šablonu stylů.</span><span class="sxs-lookup"><span data-stu-id="9217c-109">Compile the style sheet.</span></span>|<span data-ttu-id="9217c-110">Vyřešte identifikátor URI pro šablonu stylů.</span><span class="sxs-lookup"><span data-stu-id="9217c-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="9217c-111">\- a -</span><span class="sxs-lookup"><span data-stu-id="9217c-111">-and-</span></span><br /><br /> <span data-ttu-id="9217c-112">Přeložit odkazy identifikátoru URI v jakémkoli `xsl:import` nebo `xsl:include` prvky.</span><span class="sxs-lookup"><span data-stu-id="9217c-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="9217c-113">Spusťte šablonu stylů.</span><span class="sxs-lookup"><span data-stu-id="9217c-113">Execute the style sheet.</span></span>|<span data-ttu-id="9217c-114">Vyřešte identifikátor URI kontextu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9217c-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="9217c-115">\- a -</span><span class="sxs-lookup"><span data-stu-id="9217c-115">-and-</span></span><br /><br /> <span data-ttu-id="9217c-116">Přeloží odkazy identifikátoru URI v jakýchkoli funkcích XSLT `document()`.</span><span class="sxs-lookup"><span data-stu-id="9217c-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="9217c-117">Metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> a <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> zahrnují přetížení, která přebírají objekt <xref:System.Xml.XmlResolver> jako jeden z jeho argumentů.</span><span class="sxs-lookup"><span data-stu-id="9217c-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="9217c-118">Pokud není zadaný <xref:System.Xml.XmlResolver>, použije se výchozí <xref:System.Xml.XmlUrlResolver> bez přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="9217c-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="9217c-119">Následující seznam popisuje, kdy možná budete chtít zadat objekt <xref:System.Xml.XmlResolver>:</span><span class="sxs-lookup"><span data-stu-id="9217c-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="9217c-120">Pokud proces XSLT potřebuje přístup k síťovému prostředku, který vyžaduje ověření, můžete použít <xref:System.Xml.XmlResolver> s potřebnými přihlašovacími údaji.</span><span class="sxs-lookup"><span data-stu-id="9217c-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="9217c-121">Pokud chcete omezit prostředky, ke kterým může proces XSLT přistupovat, můžete použít <xref:System.Xml.XmlSecureResolver> se správnou sadou oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9217c-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="9217c-122">Třídu <xref:System.Xml.XmlSecureResolver> použijte v případě, že potřebujete otevřít prostředek, který neovládáte nebo který není důvěryhodný.</span><span class="sxs-lookup"><span data-stu-id="9217c-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="9217c-123">Pokud chcete přizpůsobit chování, můžete implementovat vlastní třídu <xref:System.Xml.XmlResolver> a použít ji k řešení prostředků.</span><span class="sxs-lookup"><span data-stu-id="9217c-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="9217c-124">Pokud chcete zajistit, aby nedošlo k žádnému externímu prostředku, můžete pro argument <xref:System.Xml.XmlResolver> zadat `null`.</span><span class="sxs-lookup"><span data-stu-id="9217c-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9217c-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="9217c-125">Example</span></span>  
 <span data-ttu-id="9217c-126">Následující příklad zkompiluje šablonu stylů uloženou v síťovém prostředku.</span><span class="sxs-lookup"><span data-stu-id="9217c-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="9217c-127">Objekt <xref:System.Xml.XmlUrlResolver> Určuje pověření nutná pro přístup k šabloně stylů.</span><span class="sxs-lookup"><span data-stu-id="9217c-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="9217c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9217c-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="9217c-129">Transformace XSLT</span><span class="sxs-lookup"><span data-stu-id="9217c-129">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
