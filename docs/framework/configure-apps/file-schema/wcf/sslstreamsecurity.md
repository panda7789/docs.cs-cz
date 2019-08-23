---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 5ed87adfb3963513602844fc69afce8f7994fa8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932426"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="1c9c4-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="1c9c4-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="1c9c4-102">Představuje vlastní prvek vazby, který podporuje zabezpečení kanálu pomocí datového proudu SSL.</span><span class="sxs-lookup"><span data-stu-id="1c9c4-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="1c9c4-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1c9c4-103">\<system.serviceModel></span></span>  
<span data-ttu-id="1c9c4-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="1c9c4-104">\<bindings></span></span>  
<span data-ttu-id="1c9c4-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1c9c4-105">\<customBinding></span></span>  
<span data-ttu-id="1c9c4-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="1c9c4-106">\<binding></span></span>  
<span data-ttu-id="1c9c4-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="1c9c4-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c9c4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c9c4-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c9c4-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1c9c4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1c9c4-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1c9c4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c9c4-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1c9c4-111">Attributes</span></span>  
  
|<span data-ttu-id="1c9c4-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="1c9c4-112">Attribute</span></span>|<span data-ttu-id="1c9c4-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1c9c4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c9c4-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="1c9c4-114">requireClientCertificate</span></span>|<span data-ttu-id="1c9c4-115">Logická hodnota určující, zda je klientský certifikát pro tuto vazbu vyžadován.</span><span class="sxs-lookup"><span data-stu-id="1c9c4-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="1c9c4-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="1c9c4-116">The default is `false`.</span></span>|  
|<span data-ttu-id="1c9c4-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="1c9c4-117">sslProtocols</span></span>|<span data-ttu-id="1c9c4-118">Hodnota příznaku výčtu SslProtocols určující, která určuje, které SslProtocols určující jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="1c9c4-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="1c9c4-119">Výchozí hodnota je SSL3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="1c9c4-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c9c4-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1c9c4-120">Child Elements</span></span>  
 <span data-ttu-id="1c9c4-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="1c9c4-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c9c4-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1c9c4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1c9c4-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="1c9c4-123">Element</span></span>|<span data-ttu-id="1c9c4-124">Popis</span><span class="sxs-lookup"><span data-stu-id="1c9c4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c9c4-125">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="1c9c4-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="1c9c4-126">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="1c9c4-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c9c4-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c9c4-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="1c9c4-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="1c9c4-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1c9c4-129">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="1c9c4-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1c9c4-130">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="1c9c4-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1c9c4-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1c9c4-131">\<customBinding></span></span>](custombinding.md)
