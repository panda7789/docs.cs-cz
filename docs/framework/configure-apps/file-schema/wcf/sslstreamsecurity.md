---
title: '&lt;sslStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 65233bf416080212a5c1447cffd329eca1b921f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="a678e-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="a678e-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="a678e-103">Představuje vlastní vazby element, který podporuje kanál zabezpečení pomocí datového proudu protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="a678e-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="a678e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a678e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a678e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a678e-105">\<bindings></span></span>  
<span data-ttu-id="a678e-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a678e-106">\<customBinding></span></span>  
<span data-ttu-id="a678e-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="a678e-107">\<binding></span></span>  
<span data-ttu-id="a678e-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="a678e-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a678e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a678e-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a678e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a678e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a678e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a678e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a678e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a678e-112">Attributes</span></span>  
  
|<span data-ttu-id="a678e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a678e-113">Attribute</span></span>|<span data-ttu-id="a678e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a678e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a678e-115">RequireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="a678e-115">requireClientCertificate</span></span>|<span data-ttu-id="a678e-116">Logická hodnota, která určuje, zda klientský certifikát je požadovaná pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="a678e-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="a678e-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a678e-117">The default is `false`.</span></span>|  
|<span data-ttu-id="a678e-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="a678e-118">sslProtocols</span></span>|<span data-ttu-id="a678e-119">Hodnotu výčtu příznak SslProtocols, která určuje, které SslProtocols jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="a678e-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="a678e-120">Výchozí hodnota je Ssl3 &#124; Protokol TLS &#124; Tls11 &#124; Tls12.</span><span class="sxs-lookup"><span data-stu-id="a678e-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a678e-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a678e-121">Child Elements</span></span>  
 <span data-ttu-id="a678e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="a678e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a678e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a678e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a678e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="a678e-124">Element</span></span>|<span data-ttu-id="a678e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="a678e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a678e-126">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="a678e-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a678e-127">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="a678e-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a678e-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="a678e-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="a678e-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="a678e-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a678e-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="a678e-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a678e-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="a678e-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a678e-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a678e-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
