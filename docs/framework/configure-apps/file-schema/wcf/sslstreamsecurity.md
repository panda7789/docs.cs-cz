---
title: <sslStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
ms.openlocfilehash: 67ec30b2bf3c322b949700789ce942e4281b77a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204442"
---
# <a name="sslstreamsecurity"></a><span data-ttu-id="2d9b7-101">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="2d9b7-101">\<sslStreamSecurity></span></span>
<span data-ttu-id="2d9b7-102">Představuje vlastní prvek vazby, který podporuje zabezpečení kanálu pomocí datového proudu protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="2d9b7-102">Represents a custom binding element that supports channel security using an SSL stream.</span></span>  
  
 <span data-ttu-id="2d9b7-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2d9b7-103">\<system.serviceModel></span></span>  
<span data-ttu-id="2d9b7-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="2d9b7-104">\<bindings></span></span>  
<span data-ttu-id="2d9b7-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2d9b7-105">\<customBinding></span></span>  
<span data-ttu-id="2d9b7-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="2d9b7-106">\<binding></span></span>  
<span data-ttu-id="2d9b7-107">\<sslStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="2d9b7-107">\<sslStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d9b7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d9b7-108">Syntax</span></span>  
  
```xml  
<sslStreamSecurity requireClientCertificate="Boolean"
                   sslProtocols="Ssl3|Tls|Tls11|Tls12" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d9b7-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2d9b7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2d9b7-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2d9b7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d9b7-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2d9b7-111">Attributes</span></span>  
  
|<span data-ttu-id="2d9b7-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="2d9b7-112">Attribute</span></span>|<span data-ttu-id="2d9b7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2d9b7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d9b7-114">requireClientCertificate</span><span class="sxs-lookup"><span data-stu-id="2d9b7-114">requireClientCertificate</span></span>|<span data-ttu-id="2d9b7-115">Logická hodnota, která určuje, jestli je certifikát klienta pro tuto vazbu vyžadován.</span><span class="sxs-lookup"><span data-stu-id="2d9b7-115">A Boolean value that specifies if a client certificate is required for this binding.</span></span> <span data-ttu-id="2d9b7-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="2d9b7-116">The default is `false`.</span></span>|  
|<span data-ttu-id="2d9b7-117">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="2d9b7-117">sslProtocols</span></span>|<span data-ttu-id="2d9b7-118">SslProtocols příznak hodnotu výčtu, která určuje, které SslProtocols jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="2d9b7-118">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="2d9b7-119">Výchozí hodnota je Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="2d9b7-119">The default is Ssl3&#124;Tls&#124;Tls11&#124;Tls12.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d9b7-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2d9b7-120">Child Elements</span></span>  
 <span data-ttu-id="2d9b7-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="2d9b7-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d9b7-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2d9b7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2d9b7-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="2d9b7-123">Element</span></span>|<span data-ttu-id="2d9b7-124">Popis</span><span class="sxs-lookup"><span data-stu-id="2d9b7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d9b7-125">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="2d9b7-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2d9b7-126">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="2d9b7-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d9b7-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d9b7-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- [<span data-ttu-id="2d9b7-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="2d9b7-128">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="2d9b7-129">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="2d9b7-129">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2d9b7-130">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="2d9b7-130">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2d9b7-131">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2d9b7-131">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
