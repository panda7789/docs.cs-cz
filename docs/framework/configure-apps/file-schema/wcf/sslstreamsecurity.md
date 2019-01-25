---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: fe633aa1ed2b165a83f415748b70b6a66bbb0130
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540912"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="807e8-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="807e8-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="807e8-103">Představuje vlastní prvek vazby, který podporuje zabezpečení kanálu pomocí datového proudu protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="807e8-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="807e8-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="807e8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="807e8-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="807e8-105">\<bindings></span></span>  
<span data-ttu-id="807e8-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="807e8-106">\<customBinding></span></span>  
<span data-ttu-id="807e8-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="807e8-107">\<binding></span></span>  
<span data-ttu-id="807e8-108">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="807e8-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="807e8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="807e8-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="807e8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="807e8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="807e8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="807e8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="807e8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="807e8-112">Attributes</span></span>  
  
|<span data-ttu-id="807e8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="807e8-113">Attribute</span></span>|<span data-ttu-id="807e8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="807e8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="807e8-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="807e8-115">requireClientCertificate</span></span>|<span data-ttu-id="807e8-116">Logická hodnota, která určuje, jestli je certifikát klienta pro tuto vazbu vyžadován.</span><span class="sxs-lookup"><span data-stu-id="807e8-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="807e8-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="807e8-117">The default is `false`.</span></span>|  
|<span data-ttu-id="807e8-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="807e8-118">sslProtocols</span></span>|<span data-ttu-id="807e8-119">SslProtocols příznak hodnotu výčtu, která určuje, které SslProtocols jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="807e8-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="807e8-120">Výchozí hodnota je Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="807e8-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="807e8-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="807e8-121">Child Elements</span></span>  
 <span data-ttu-id="807e8-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="807e8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="807e8-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="807e8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="807e8-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="807e8-124">Element</span></span>|<span data-ttu-id="807e8-125">Popis</span><span class="sxs-lookup"><span data-stu-id="807e8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="807e8-126">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="807e8-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="807e8-127">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="807e8-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="807e8-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="807e8-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="807e8-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="807e8-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="807e8-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="807e8-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="807e8-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="807e8-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="807e8-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="807e8-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
