---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738589"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="1d0f8-101">\<sslStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="1d0f8-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="1d0f8-102">Představuje vlastní prvek vazby, který podporuje zabezpečení kanálu pomocí datového proudu SSL.</span><span class="sxs-lookup"><span data-stu-id="1d0f8-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
<span data-ttu-id="1d0f8-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1d0f8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1d0f8-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="1d0f8-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1d0f8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1d0f8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="1d0f8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="1d0f8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="1d0f8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="1d0f8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="1d0f8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sslStreamSecurity >**</span><span class="sxs-lookup"><span data-stu-id="1d0f8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d0f8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d0f8-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d0f8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1d0f8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1d0f8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1d0f8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d0f8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1d0f8-112">Attributes</span></span>  
  
|<span data-ttu-id="1d0f8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1d0f8-113">Attribute</span></span>|<span data-ttu-id="1d0f8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1d0f8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d0f8-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="1d0f8-115">requireClientCertificate</span></span>|<span data-ttu-id="1d0f8-116">Logická hodnota určující, zda je klientský certifikát pro tuto vazbu vyžadován.</span><span class="sxs-lookup"><span data-stu-id="1d0f8-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="1d0f8-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="1d0f8-117">The default is `false`.</span></span>|  
|<span data-ttu-id="1d0f8-118">SslProtocols určující</span><span class="sxs-lookup"><span data-stu-id="1d0f8-118">sslProtocols</span></span>|<span data-ttu-id="1d0f8-119">Hodnota příznaku výčtu SslProtocols určující, která určuje, které SslProtocols určující jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="1d0f8-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="1d0f8-120">Výchozí hodnota je SSL3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="1d0f8-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d0f8-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1d0f8-121">Child Elements</span></span>  
 <span data-ttu-id="1d0f8-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="1d0f8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d0f8-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1d0f8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1d0f8-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="1d0f8-124">Element</span></span>|<span data-ttu-id="1d0f8-125">Popis</span><span class="sxs-lookup"><span data-stu-id="1d0f8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d0f8-126">vazba \<</span><span class="sxs-lookup"><span data-stu-id="1d0f8-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="1d0f8-127">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="1d0f8-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d0f8-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d0f8-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="1d0f8-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="1d0f8-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1d0f8-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="1d0f8-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1d0f8-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="1d0f8-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1d0f8-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1d0f8-132">\<customBinding></span></span>](custombinding.md)
