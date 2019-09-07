---
title: <security> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: cd3ff5d3983283f9b4783912b4b9525c5000df61
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399819"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="50de4-102">\<security> of \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="50de4-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="50de4-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="50de4-103">Defines the security settings for a binding.</span></span>  
  
<span data-ttu-id="50de4-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="50de4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="50de4-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="50de4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="50de4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="50de4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="50de4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="50de4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="50de4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="50de4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="50de4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="50de4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50de4-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50de4-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50de4-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="50de4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="50de4-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="50de4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50de4-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="50de4-113">Attributes</span></span>  
  
|<span data-ttu-id="50de4-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="50de4-114">Attribute</span></span>|<span data-ttu-id="50de4-115">Popis</span><span class="sxs-lookup"><span data-stu-id="50de4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50de4-116">režim</span><span class="sxs-lookup"><span data-stu-id="50de4-116">mode</span></span>|<span data-ttu-id="50de4-117">Určuje typ zabezpečení, který se použije pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="50de4-117">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="50de4-118">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="50de4-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="50de4-119">NTato Tím se zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="50de4-119">-   None: This disables security.</span></span><br /><span data-ttu-id="50de4-120">Přepravu Zabezpečení je zajišťováno pomocí základního zabezpečení založeného na přenosu.</span><span class="sxs-lookup"><span data-stu-id="50de4-120">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="50de4-121">Úroveň ochrany je možné řídit pomocí tohoto režimu.</span><span class="sxs-lookup"><span data-stu-id="50de4-121">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="50de4-122">– Výchozí hodnota je Transport.</span><span class="sxs-lookup"><span data-stu-id="50de4-122">-   The default value is Transport.</span></span> <span data-ttu-id="50de4-123">Tento atribut je typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="50de4-123">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50de4-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="50de4-124">Child Elements</span></span>  
  
|<span data-ttu-id="50de4-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="50de4-125">Element</span></span>|<span data-ttu-id="50de4-126">Popis</span><span class="sxs-lookup"><span data-stu-id="50de4-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50de4-127">transport</span><span class="sxs-lookup"><span data-stu-id="50de4-127">transport</span></span>|<span data-ttu-id="50de4-128">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="50de4-128">Defines the security settings for the transport.</span></span> <span data-ttu-id="50de4-129">Tento prvek je typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="50de4-129">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="50de4-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="50de4-130">Parent Elements</span></span>  
  
|<span data-ttu-id="50de4-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="50de4-131">Element</span></span>|<span data-ttu-id="50de4-132">Popis</span><span class="sxs-lookup"><span data-stu-id="50de4-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50de4-133">vazba</span><span class="sxs-lookup"><span data-stu-id="50de4-133">binding</span></span>|<span data-ttu-id="50de4-134">[ Prvek\<vazby > NetNamedPipeBinding](netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="50de4-134">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50de4-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50de4-135">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="50de4-136">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="50de4-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="50de4-137">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="50de4-137">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="50de4-138">Vazby</span><span class="sxs-lookup"><span data-stu-id="50de4-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="50de4-139">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="50de4-139">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="50de4-140">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="50de4-140">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="50de4-141">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="50de4-141">\<binding></span></span>](../../../misc/binding.md)
