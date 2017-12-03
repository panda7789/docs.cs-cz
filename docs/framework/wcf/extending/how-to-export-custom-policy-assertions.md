---
title: "Postupy: Export kontrolních výrazů vlastních zásad"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1cfce32a7e7099a601c76874c8ca951488335fc6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-export-custom-policy-assertions"></a><span data-ttu-id="12183-102">Postupy: Export kontrolních výrazů vlastních zásad</span><span class="sxs-lookup"><span data-stu-id="12183-102">How to: Export Custom Policy Assertions</span></span>
<span data-ttu-id="12183-103">Kontrolní výrazy zásad jsou popsány možnosti a požadavky koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="12183-103">Policy assertions describe the capabilities and requirements of a service endpoint.</span></span> <span data-ttu-id="12183-104">Aplikace služby můžete pomocí kontrolních výrazů vlastních zásad metadata služby komunikovat koncový bod, vazba nebo kontrakt informace o přizpůsobení do klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="12183-104">Service applications can use custom policy assertions in service metadata to communicate endpoint, binding or contract customization information to the client application.</span></span> <span data-ttu-id="12183-105">Můžete použít [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] export kontrolní výrazy ve výrazech zásad připojena v WSDL vazby na koncový bod, operace nebo zpráva tématům, v závislosti na možnosti nebo požadavky jsou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="12183-105">You can use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to export assertions in policy expressions attached in WSDL bindings at the endpoint, operation, or message subjects, depending upon the capabilities or requirements you are communicating.</span></span>  
  
 <span data-ttu-id="12183-106">Exportují se implementací kontrolních výrazů vlastních zásad <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní na <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> a buď vložení prvku vazby přímo do vazby koncového bodu služby nebo tím, že zaregistrujete prvku vazby v aplikaci konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="12183-106">Custom policy assertions are exported by implementing the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and either inserting the binding element directly into the binding of the service endpoint or by registering the binding element in your application configuration file.</span></span> <span data-ttu-id="12183-107">Export implementaci zásad měli přidat vaše vlastní zásady assertion jako <xref:System.Xml.XmlElement?displayProperty=nameWithType> instance na příslušné <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> na <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> předaný do <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="12183-107">Your policy export implementation should add your custom policy assertion as a <xref:System.Xml.XmlElement?displayProperty=nameWithType> instance to the appropriate <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> on the <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> passed into the <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> method.</span></span>  
  
 <span data-ttu-id="12183-108">Kromě toho je nutné zkontrolovat <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost <xref:System.ServiceModel.Description.WsdlExporter> třídy a export výrazy vnořené zásad a zásad framework atributy ve správný obor názvů na základě zásad verze zadané.</span><span class="sxs-lookup"><span data-stu-id="12183-108">In addition you must check the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property of the <xref:System.ServiceModel.Description.WsdlExporter> class and export nested policy expressions and policy framework attributes in the correct namespace based on the policy version specified.</span></span>  
  
 <span data-ttu-id="12183-109">Chcete-li import kontrolních výrazů vlastních zásad, přečtěte si téma <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> a [postupy: Import kontrolních výrazů vlastních zásad](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).</span><span class="sxs-lookup"><span data-stu-id="12183-109">To import custom policy assertions, see <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> and [How to: Import Custom Policy Assertions](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md).</span></span>  
  
### <a name="to-export-custom-policy-assertions"></a><span data-ttu-id="12183-110">Export kontrolních výrazů vlastních zásad</span><span class="sxs-lookup"><span data-stu-id="12183-110">To export custom policy assertions</span></span>  
  
1.  <span data-ttu-id="12183-111">Implementace <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> rozhraní na <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="12183-111">Implement the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>.</span></span> <span data-ttu-id="12183-112">Následující příklad kódu ukazuje implementaci assertion vlastní zásady na úrovni vazby.</span><span class="sxs-lookup"><span data-stu-id="12183-112">The following code example shows the implementation of a custom policy assertion at the binding level.</span></span>  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  <span data-ttu-id="12183-113">Vložení prvku vazby do koncového bodu vazba buď programově, nebo pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="12183-113">Insert the binding element into the endpoint binding either programmatically or using an application configuration file.</span></span> <span data-ttu-id="12183-114">Postupujte podle následujících pokynů.</span><span class="sxs-lookup"><span data-stu-id="12183-114">See the following procedures.</span></span>  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a><span data-ttu-id="12183-115">Chcete-li vložit element vazby pomocí konfiguračního souboru aplikace</span><span class="sxs-lookup"><span data-stu-id="12183-115">To insert a binding element using an application configuration file</span></span>  
  
1.  <span data-ttu-id="12183-116">Implementace <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> pro vaše vlastní zásady assertion vazby element.</span><span class="sxs-lookup"><span data-stu-id="12183-116">Implement <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> for your custom policy assertion binding element.</span></span>  
  
2.  <span data-ttu-id="12183-117">Přidejte rozšíření element vazby do souboru konfigurace pomocí [ \<bindingElementExtensions >](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) element.</span><span class="sxs-lookup"><span data-stu-id="12183-117">Add the binding element extension to the configuration file using the [\<bindingElementExtensions>](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) element.</span></span>  
  
3.  <span data-ttu-id="12183-118">Vytvoření vlastní vazby pomocí <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="12183-118">Build a custom binding using the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-insert-a-binding-element-programmatically"></a><span data-ttu-id="12183-119">Vložení prvku vazby prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="12183-119">To insert a binding element programmatically</span></span>  
  
1.  <span data-ttu-id="12183-120">Vytvořte novou <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> a přidejte ho do <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="12183-120">Create a new <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and add it to a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
2.  <span data-ttu-id="12183-121">Přidáte vlastní vazby z kroku 1.</span><span class="sxs-lookup"><span data-stu-id="12183-121">Add the custom binding from step 1.</span></span> <span data-ttu-id="12183-122">na nový koncový bod a přidejte tento nový koncový bod služby k <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> voláním <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="12183-122">to a new endpoint and add that new service endpoint to the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> by calling the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
3.  <span data-ttu-id="12183-123">Otevřete <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="12183-123">Open the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="12183-124">Následující příklad kódu ukazuje vytvoření vlastní vazby a programové vkládání elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="12183-124">The following code example shows the creation of a custom binding and the programmatic insertion of binding elements.</span></span>  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="12183-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="12183-125">See Also</span></span>  
 <xref:System.ServiceModel.Description.IPolicyImportExtension>  
 <xref:System.ServiceModel.Description.IPolicyExportExtension>  
 [<span data-ttu-id="12183-126">Postupy: Import kontrolních výrazů vlastních zásad</span><span class="sxs-lookup"><span data-stu-id="12183-126">How to: Import Custom Policy Assertions</span></span>](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)
