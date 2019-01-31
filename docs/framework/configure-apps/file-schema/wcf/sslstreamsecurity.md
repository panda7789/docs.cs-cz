---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: f66569f36dc61a063b79a088dcbc405126a074d8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284593"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="e37b2-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="e37b2-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="e37b2-102">Představuje vlastní prvek vazby, který podporuje zabezpečení kanálu pomocí datového proudu protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="e37b2-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="e37b2-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e37b2-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e37b2-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="e37b2-104">\<bindings></span></span>  
<span data-ttu-id="e37b2-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e37b2-105">\<customBinding></span></span>  
<span data-ttu-id="e37b2-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="e37b2-106">\<binding></span></span>  
<span data-ttu-id="e37b2-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="e37b2-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e37b2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e37b2-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e37b2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e37b2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e37b2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e37b2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e37b2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e37b2-111">Attributes</span></span>  
  
|<span data-ttu-id="e37b2-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e37b2-112">Attribute</span></span>|<span data-ttu-id="e37b2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e37b2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e37b2-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="e37b2-114">requireClientCertificate</span></span>|<span data-ttu-id="e37b2-115">Logická hodnota, která určuje, jestli je certifikát klienta pro tuto vazbu vyžadován.</span><span class="sxs-lookup"><span data-stu-id="e37b2-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="e37b2-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="e37b2-116">The default is `false`.</span></span>|  
|<span data-ttu-id="e37b2-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="e37b2-117">sslProtocols</span></span>|<span data-ttu-id="e37b2-118">SslProtocols příznak hodnotu výčtu, která určuje, které SslProtocols jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="e37b2-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="e37b2-119">Výchozí hodnota je Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="e37b2-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e37b2-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e37b2-120">Child Elements</span></span>  
 <span data-ttu-id="e37b2-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="e37b2-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e37b2-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e37b2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e37b2-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="e37b2-123">Element</span></span>|<span data-ttu-id="e37b2-124">Popis</span><span class="sxs-lookup"><span data-stu-id="e37b2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e37b2-125">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="e37b2-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e37b2-126">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="e37b2-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e37b2-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e37b2-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="e37b2-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="e37b2-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="e37b2-129">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="e37b2-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e37b2-130">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="e37b2-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e37b2-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e37b2-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
