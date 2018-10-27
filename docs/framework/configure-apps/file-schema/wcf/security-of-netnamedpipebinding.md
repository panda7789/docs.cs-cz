---
title: '&lt;security&gt; – &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 4a80a8337a5b98ff30de60afbe4438e0d91b946b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185677"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="3ea29-102">&lt;security&gt; – &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3ea29-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="3ea29-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="3ea29-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="3ea29-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3ea29-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3ea29-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3ea29-105">\<bindings></span></span>  
<span data-ttu-id="3ea29-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="3ea29-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="3ea29-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3ea29-107">\<binding></span></span>  
<span data-ttu-id="3ea29-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="3ea29-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea29-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ea29-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ea29-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ea29-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ea29-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3ea29-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ea29-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ea29-112">Attributes</span></span>  
  
|<span data-ttu-id="3ea29-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3ea29-113">Attribute</span></span>|<span data-ttu-id="3ea29-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea29-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ea29-115">režim</span><span class="sxs-lookup"><span data-stu-id="3ea29-115">mode</span></span>|<span data-ttu-id="3ea29-116">Určuje typ zabezpečení, který se použije pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="3ea29-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="3ea29-117">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="3ea29-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3ea29-118">-Žádný: Zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3ea29-118">-   None: This disables security.</span></span><br /><span data-ttu-id="3ea29-119">-Přenos: Zabezpečení je k dispozici pomocí základního zabezpečení přenosu na základě.</span><span class="sxs-lookup"><span data-stu-id="3ea29-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="3ea29-120">Je možné kontrolovat úroveň ochrany s tímto režimem.</span><span class="sxs-lookup"><span data-stu-id="3ea29-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="3ea29-121">– Výchozí hodnota je přenos.</span><span class="sxs-lookup"><span data-stu-id="3ea29-121">-   The default value is Transport.</span></span> <span data-ttu-id="3ea29-122">Tento atribut je typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3ea29-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ea29-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ea29-123">Child Elements</span></span>  
  
|<span data-ttu-id="3ea29-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ea29-124">Element</span></span>|<span data-ttu-id="3ea29-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea29-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ea29-126">transport</span><span class="sxs-lookup"><span data-stu-id="3ea29-126">transport</span></span>|<span data-ttu-id="3ea29-127">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="3ea29-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="3ea29-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3ea29-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ea29-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ea29-129">Parent Elements</span></span>  
  
|<span data-ttu-id="3ea29-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ea29-130">Element</span></span>|<span data-ttu-id="3ea29-131">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea29-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ea29-132">vazba</span><span class="sxs-lookup"><span data-stu-id="3ea29-132">binding</span></span>|<span data-ttu-id="3ea29-133">Prvek vazby [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="3ea29-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ea29-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ea29-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="3ea29-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3ea29-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3ea29-136">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="3ea29-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="3ea29-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="3ea29-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3ea29-138">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3ea29-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3ea29-139">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3ea29-139">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="3ea29-140">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3ea29-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
