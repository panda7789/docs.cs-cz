---
title: '&lt;sslStreamSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
author: BrucePerlerMS
ms.openlocfilehash: 6eacf1833ecf980696d75c5dbcaaba3ba6403d92
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087447"
---
# <a name="ltsslstreamsecuritygt"></a><span data-ttu-id="3ff84-102">&lt;sslStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="3ff84-102">&lt;sslStreamSecurity&gt;</span></span>
<span data-ttu-id="3ff84-103">Představuje vlastní prvek vazby, který podporuje zabezpečení kanálu pomocí datového proudu protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="3ff84-103">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="3ff84-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3ff84-104">\<system.serviceModel></span></span>  
<span data-ttu-id="3ff84-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3ff84-105">\<bindings></span></span>  
<span data-ttu-id="3ff84-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="3ff84-106">\<customBinding></span></span>  
<span data-ttu-id="3ff84-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3ff84-107">\<binding></span></span>  
<span data-ttu-id="3ff84-108">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="3ff84-108">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ff84-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ff84-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ff84-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ff84-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ff84-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3ff84-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ff84-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ff84-112">Attributes</span></span>  
  
|<span data-ttu-id="3ff84-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3ff84-113">Attribute</span></span>|<span data-ttu-id="3ff84-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3ff84-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ff84-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="3ff84-115">requireClientCertificate</span></span>|<span data-ttu-id="3ff84-116">Logická hodnota, která určuje, jestli je certifikát klienta pro tuto vazbu vyžadován.</span><span class="sxs-lookup"><span data-stu-id="3ff84-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="3ff84-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="3ff84-117">The default is `false`.</span></span>|  
|<span data-ttu-id="3ff84-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="3ff84-118">sslProtocols</span></span>|<span data-ttu-id="3ff84-119">SslProtocols příznak hodnotu výčtu, která určuje, které SslProtocols jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="3ff84-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="3ff84-120">Výchozí hodnota je Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="3ff84-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ff84-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ff84-121">Child Elements</span></span>  
 <span data-ttu-id="3ff84-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="3ff84-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ff84-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ff84-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3ff84-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ff84-124">Element</span></span>|<span data-ttu-id="3ff84-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3ff84-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ff84-126">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3ff84-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3ff84-127">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="3ff84-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ff84-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ff84-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
 [<span data-ttu-id="3ff84-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="3ff84-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3ff84-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="3ff84-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="3ff84-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="3ff84-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="3ff84-132">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="3ff84-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
