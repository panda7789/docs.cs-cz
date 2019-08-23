---
title: <security> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 0996a98438dc344d96d640abced52ac99709adbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936678"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="182f0-102">\<security> of \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="182f0-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="182f0-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="182f0-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="182f0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="182f0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="182f0-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="182f0-105">\<bindings></span></span>  
<span data-ttu-id="182f0-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="182f0-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="182f0-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="182f0-107">\<binding></span></span>  
<span data-ttu-id="182f0-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="182f0-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="182f0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="182f0-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="182f0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="182f0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="182f0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="182f0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="182f0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="182f0-112">Attributes</span></span>  
  
|<span data-ttu-id="182f0-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="182f0-113">Attribute</span></span>|<span data-ttu-id="182f0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="182f0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="182f0-115">režim</span><span class="sxs-lookup"><span data-stu-id="182f0-115">mode</span></span>|<span data-ttu-id="182f0-116">Určuje typ zabezpečení, který se použije pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="182f0-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="182f0-117">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="182f0-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="182f0-118">NTato Tím se zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="182f0-118">-   None: This disables security.</span></span><br /><span data-ttu-id="182f0-119">Přepravu Zabezpečení je zajišťováno pomocí základního zabezpečení založeného na přenosu.</span><span class="sxs-lookup"><span data-stu-id="182f0-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="182f0-120">Úroveň ochrany je možné řídit pomocí tohoto režimu.</span><span class="sxs-lookup"><span data-stu-id="182f0-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="182f0-121">– Výchozí hodnota je Transport.</span><span class="sxs-lookup"><span data-stu-id="182f0-121">-   The default value is Transport.</span></span> <span data-ttu-id="182f0-122">Tento atribut je typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="182f0-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="182f0-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="182f0-123">Child Elements</span></span>  
  
|<span data-ttu-id="182f0-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="182f0-124">Element</span></span>|<span data-ttu-id="182f0-125">Popis</span><span class="sxs-lookup"><span data-stu-id="182f0-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="182f0-126">transport</span><span class="sxs-lookup"><span data-stu-id="182f0-126">transport</span></span>|<span data-ttu-id="182f0-127">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="182f0-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="182f0-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="182f0-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="182f0-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="182f0-129">Parent Elements</span></span>  
  
|<span data-ttu-id="182f0-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="182f0-130">Element</span></span>|<span data-ttu-id="182f0-131">Popis</span><span class="sxs-lookup"><span data-stu-id="182f0-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="182f0-132">vazba</span><span class="sxs-lookup"><span data-stu-id="182f0-132">binding</span></span>|<span data-ttu-id="182f0-133">[ Prvek\<vazby > NetNamedPipeBinding](netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="182f0-133">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="182f0-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="182f0-134">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="182f0-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="182f0-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="182f0-136">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="182f0-136">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="182f0-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="182f0-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="182f0-138">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="182f0-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="182f0-139">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="182f0-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="182f0-140">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="182f0-140">\<binding></span></span>](../../../misc/binding.md)
