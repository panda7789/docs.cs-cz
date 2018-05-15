---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: a86e1aae7ddd5389f098e532ae2c2cc67f4085e3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="a2b95-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="a2b95-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="a2b95-103">Představuje vlastní vazby element, který podporuje kanál zabezpečení pomocí datového proudu protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="a2b95-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="a2b95-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a2b95-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a2b95-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a2b95-105">\<bindings></span></span>  
<span data-ttu-id="a2b95-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a2b95-106">\<customBinding></span></span>  
<span data-ttu-id="a2b95-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="a2b95-107">\<binding></span></span>  
<span data-ttu-id="a2b95-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="a2b95-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b95-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2b95-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2b95-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a2b95-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a2b95-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a2b95-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2b95-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a2b95-112">Attributes</span></span>  
  
|<span data-ttu-id="a2b95-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a2b95-113">Attribute</span></span>|<span data-ttu-id="a2b95-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a2b95-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2b95-115">RequireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="a2b95-115">requireClientCertificate</span></span>|<span data-ttu-id="a2b95-116">Logická hodnota, která určuje, zda klientský certifikát je požadovaná pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="a2b95-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="a2b95-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a2b95-117">The default is `false`.</span></span>|  
|<span data-ttu-id="a2b95-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="a2b95-118">sslProtocols</span></span>|<span data-ttu-id="a2b95-119">Hodnotu výčtu příznak SslProtocols, která určuje, které SslProtocols jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="a2b95-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="a2b95-120">Výchozí hodnota je Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="a2b95-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2b95-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a2b95-121">Child Elements</span></span>  
 <span data-ttu-id="a2b95-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="a2b95-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2b95-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a2b95-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a2b95-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="a2b95-124">Element</span></span>|<span data-ttu-id="a2b95-125">Popis</span><span class="sxs-lookup"><span data-stu-id="a2b95-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2b95-126">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="a2b95-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a2b95-127">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="a2b95-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2b95-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2b95-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="a2b95-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="a2b95-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a2b95-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="a2b95-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a2b95-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="a2b95-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a2b95-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a2b95-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
