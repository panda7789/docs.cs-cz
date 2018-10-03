---
title: '&lt;security&gt; – &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
ms.openlocfilehash: eee4cc13b5181caa4449c3ad6ebc5247cc7e0f1a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033373"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="8ba6e-102">&lt;security&gt; – &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="8ba6e-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="8ba6e-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="8ba6e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8ba6e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8ba6e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="8ba6e-105">\<bindings></span></span>  
<span data-ttu-id="8ba6e-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="8ba6e-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="8ba6e-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8ba6e-107">\<binding></span></span>  
<span data-ttu-id="8ba6e-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="8ba6e-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ba6e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ba6e-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ba6e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8ba6e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8ba6e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ba6e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="8ba6e-112">Attributes</span></span>  
  
|<span data-ttu-id="8ba6e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="8ba6e-113">Attribute</span></span>|<span data-ttu-id="8ba6e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8ba6e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ba6e-115">režim</span><span class="sxs-lookup"><span data-stu-id="8ba6e-115">mode</span></span>|<span data-ttu-id="8ba6e-116">Určuje typ zabezpečení, který se použije pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="8ba6e-117">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="8ba6e-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8ba6e-118">-Žádný: Zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-118">-   None: This disables security.</span></span><br /><span data-ttu-id="8ba6e-119">-Přenos: Zabezpečení je k dispozici pomocí základního zabezpečení přenosu na základě.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="8ba6e-120">Je možné kontrolovat úroveň ochrany s tímto režimem.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="8ba6e-121">– Výchozí hodnota je přenos.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-121">-   The default value is Transport.</span></span> <span data-ttu-id="8ba6e-122">Tento atribut je typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ba6e-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8ba6e-123">Child Elements</span></span>  
  
|<span data-ttu-id="8ba6e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="8ba6e-124">Element</span></span>|<span data-ttu-id="8ba6e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="8ba6e-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ba6e-126">transport</span><span class="sxs-lookup"><span data-stu-id="8ba6e-126">transport</span></span>|<span data-ttu-id="8ba6e-127">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="8ba6e-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="8ba6e-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ba6e-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8ba6e-129">Parent Elements</span></span>  
  
|<span data-ttu-id="8ba6e-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="8ba6e-130">Element</span></span>|<span data-ttu-id="8ba6e-131">Popis</span><span class="sxs-lookup"><span data-stu-id="8ba6e-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ba6e-132">vazba</span><span class="sxs-lookup"><span data-stu-id="8ba6e-132">binding</span></span>|<span data-ttu-id="8ba6e-133">Prvek vazby [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="8ba6e-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ba6e-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ba6e-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="8ba6e-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8ba6e-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="8ba6e-136">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="8ba6e-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="8ba6e-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="8ba6e-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8ba6e-138">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="8ba6e-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8ba6e-139">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="8ba6e-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="8ba6e-140">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8ba6e-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
