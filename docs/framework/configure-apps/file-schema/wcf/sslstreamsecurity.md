---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: c5c7ec2b18143ff4d71540a60e24b8225ca4db16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738589"
---
# \<sslStreamSecurity>
<span data-ttu-id="06a33-101">Představuje vlastní prvek vazby, který podporuje zabezpečení kanálu pomocí datového proudu SSL.</span><span class="sxs-lookup"><span data-stu-id="06a33-101">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sslStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="06a33-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06a33-102">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06a33-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="06a33-103">Attributes and Elements</span></span>  
 <span data-ttu-id="06a33-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="06a33-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06a33-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="06a33-105">Attributes</span></span>  
  
|<span data-ttu-id="06a33-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="06a33-106">Attribute</span></span>|<span data-ttu-id="06a33-107">Popis</span><span class="sxs-lookup"><span data-stu-id="06a33-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06a33-108">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="06a33-108">requireClientCertificate</span></span>|<span data-ttu-id="06a33-109">Logická hodnota určující, zda je klientský certifikát pro tuto vazbu vyžadován.</span><span class="sxs-lookup"><span data-stu-id="06a33-109">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="06a33-110">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="06a33-110">The default is `false`.</span></span>|  
|<span data-ttu-id="06a33-111">SslProtocols určující</span><span class="sxs-lookup"><span data-stu-id="06a33-111">sslProtocols</span></span>|<span data-ttu-id="06a33-112">Hodnota příznaku výčtu SslProtocols určující, která určuje, které SslProtocols určující jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="06a33-112">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="06a33-113">Výchozí hodnota je SSL3&#124;TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="06a33-113">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06a33-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="06a33-114">Child Elements</span></span>  
 <span data-ttu-id="06a33-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="06a33-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06a33-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="06a33-116">Parent Elements</span></span>  
  
|<span data-ttu-id="06a33-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="06a33-117">Element</span></span>|<span data-ttu-id="06a33-118">Description</span><span class="sxs-lookup"><span data-stu-id="06a33-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="06a33-119">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="06a33-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06a33-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="06a33-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="06a33-121">Vazby</span><span class="sxs-lookup"><span data-stu-id="06a33-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="06a33-122">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="06a33-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="06a33-123">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="06a33-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
