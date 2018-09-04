---
title: '&lt;security&gt; – &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0e5a22d6e517bc7a05f74089b7c8ece8c8a4bd39
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558669"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="5ddb1-102">&lt;security&gt; – &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5ddb1-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="5ddb1-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="5ddb1-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="5ddb1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5ddb1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ddb1-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="5ddb1-105">\<bindings></span></span>  
<span data-ttu-id="5ddb1-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="5ddb1-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="5ddb1-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="5ddb1-107">\<binding></span></span>  
<span data-ttu-id="5ddb1-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="5ddb1-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ddb1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ddb1-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ddb1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5ddb1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5ddb1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5ddb1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ddb1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5ddb1-112">Attributes</span></span>  
  
|<span data-ttu-id="5ddb1-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5ddb1-113">Attribute</span></span>|<span data-ttu-id="5ddb1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5ddb1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ddb1-115">režim</span><span class="sxs-lookup"><span data-stu-id="5ddb1-115">mode</span></span>|<span data-ttu-id="5ddb1-116">Určuje typ zabezpečení, který se použije pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="5ddb1-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="5ddb1-117">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="5ddb1-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5ddb1-118">-Žádný: Zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5ddb1-118">-   None: This disables security.</span></span><br /><span data-ttu-id="5ddb1-119">-Přenos: Zabezpečení je k dispozici pomocí základního zabezpečení přenosu na základě.</span><span class="sxs-lookup"><span data-stu-id="5ddb1-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="5ddb1-120">Je možné kontrolovat úroveň ochrany s tímto režimem.</span><span class="sxs-lookup"><span data-stu-id="5ddb1-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="5ddb1-121">– Výchozí hodnota je přenos.</span><span class="sxs-lookup"><span data-stu-id="5ddb1-121">-   The default value is Transport.</span></span> <span data-ttu-id="5ddb1-122">Tento atribut je typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5ddb1-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ddb1-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5ddb1-123">Child Elements</span></span>  
  
|<span data-ttu-id="5ddb1-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ddb1-124">Element</span></span>|<span data-ttu-id="5ddb1-125">Popis</span><span class="sxs-lookup"><span data-stu-id="5ddb1-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ddb1-126">transport</span><span class="sxs-lookup"><span data-stu-id="5ddb1-126">transport</span></span>|<span data-ttu-id="5ddb1-127">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="5ddb1-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="5ddb1-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="5ddb1-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ddb1-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5ddb1-129">Parent Elements</span></span>  
  
|<span data-ttu-id="5ddb1-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ddb1-130">Element</span></span>|<span data-ttu-id="5ddb1-131">Popis</span><span class="sxs-lookup"><span data-stu-id="5ddb1-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ddb1-132">vazba</span><span class="sxs-lookup"><span data-stu-id="5ddb1-132">binding</span></span>|<span data-ttu-id="5ddb1-133">Prvek vazby [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="5ddb1-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ddb1-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ddb1-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="5ddb1-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5ddb1-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5ddb1-136">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="5ddb1-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="5ddb1-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="5ddb1-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5ddb1-138">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5ddb1-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5ddb1-139">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="5ddb1-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5ddb1-140">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="5ddb1-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
