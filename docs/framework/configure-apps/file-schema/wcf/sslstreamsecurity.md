---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 9b7092878c604142c29dcd8d27e3c458d203f9fa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399521"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="2cc64-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="2cc64-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="2cc64-102">Představuje vlastní prvek vazby, který podporuje zabezpečení kanálu pomocí datového proudu SSL.</span><span class="sxs-lookup"><span data-stu-id="2cc64-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
<span data-ttu-id="2cc64-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2cc64-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2cc64-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2cc64-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2cc64-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2cc64-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2cc64-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="2cc64-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="2cc64-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="2cc64-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2cc64-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sslStreamSecurity >**</span><span class="sxs-lookup"><span data-stu-id="2cc64-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cc64-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cc64-109">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cc64-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2cc64-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2cc64-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2cc64-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cc64-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2cc64-112">Attributes</span></span>  
  
|<span data-ttu-id="2cc64-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2cc64-113">Attribute</span></span>|<span data-ttu-id="2cc64-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2cc64-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2cc64-115">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="2cc64-115">requireClientCertificate</span></span>|<span data-ttu-id="2cc64-116">Logická hodnota určující, zda je klientský certifikát pro tuto vazbu vyžadován.</span><span class="sxs-lookup"><span data-stu-id="2cc64-116">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="2cc64-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="2cc64-117">The default is `false`.</span></span>|  
|<span data-ttu-id="2cc64-118">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="2cc64-118">sslProtocols</span></span>|<span data-ttu-id="2cc64-119">Hodnota příznaku výčtu SslProtocols určující, která určuje, které SslProtocols určující jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="2cc64-119">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="2cc64-120">Výchozí hodnota je SSL3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="2cc64-120">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2cc64-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2cc64-121">Child Elements</span></span>  
 <span data-ttu-id="2cc64-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="2cc64-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2cc64-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2cc64-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2cc64-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="2cc64-124">Element</span></span>|<span data-ttu-id="2cc64-125">Popis</span><span class="sxs-lookup"><span data-stu-id="2cc64-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cc64-126">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="2cc64-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="2cc64-127">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="2cc64-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2cc64-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cc64-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="2cc64-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="2cc64-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2cc64-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="2cc64-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2cc64-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="2cc64-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2cc64-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2cc64-132">\<customBinding></span></span>](custombinding.md)
