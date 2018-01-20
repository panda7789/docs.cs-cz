---
title: "&lt;security&gt; – &lt;netNamedPipeBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3a018c502aead84eb6936001acb5bc24c59188f8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="3abf4-102">&lt;security&gt; – &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3abf4-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="3abf4-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="3abf4-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="3abf4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3abf4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3abf4-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3abf4-105">\<bindings></span></span>  
<span data-ttu-id="3abf4-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="3abf4-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="3abf4-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="3abf4-107">\<binding></span></span>  
<span data-ttu-id="3abf4-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="3abf4-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3abf4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3abf4-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3abf4-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3abf4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3abf4-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3abf4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3abf4-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3abf4-112">Attributes</span></span>  
  
|<span data-ttu-id="3abf4-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3abf4-113">Attribute</span></span>|<span data-ttu-id="3abf4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3abf4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3abf4-115">režim</span><span class="sxs-lookup"><span data-stu-id="3abf4-115">mode</span></span>|<span data-ttu-id="3abf4-116">Určuje typ zabezpečení, který se použije pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="3abf4-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="3abf4-117">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="3abf4-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3abf4-118">-None: To zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3abf4-118">-   None: This disables security.</span></span><br /><span data-ttu-id="3abf4-119">-Přenos: Zabezpečení je zajištěno pomocí základního zabezpečení přenosu na základě.</span><span class="sxs-lookup"><span data-stu-id="3abf4-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="3abf4-120">Je možné kontrolovat úroveň ochrany s Tento režim.</span><span class="sxs-lookup"><span data-stu-id="3abf4-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="3abf4-121">-Výchozí hodnota je přenos.</span><span class="sxs-lookup"><span data-stu-id="3abf4-121">-   The default value is Transport.</span></span> <span data-ttu-id="3abf4-122">Tento atribut je typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3abf4-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3abf4-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3abf4-123">Child Elements</span></span>  
  
|<span data-ttu-id="3abf4-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3abf4-124">Element</span></span>|<span data-ttu-id="3abf4-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3abf4-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3abf4-126">transport</span><span class="sxs-lookup"><span data-stu-id="3abf4-126">transport</span></span>|<span data-ttu-id="3abf4-127">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="3abf4-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="3abf4-128">Tento element je typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3abf4-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3abf4-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3abf4-129">Parent Elements</span></span>  
  
|<span data-ttu-id="3abf4-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="3abf4-130">Element</span></span>|<span data-ttu-id="3abf4-131">Popis</span><span class="sxs-lookup"><span data-stu-id="3abf4-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3abf4-132">vazba</span><span class="sxs-lookup"><span data-stu-id="3abf4-132">binding</span></span>|<span data-ttu-id="3abf4-133">Element vazby [ \<– netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="3abf4-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3abf4-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="3abf4-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="3abf4-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3abf4-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3abf4-136">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="3abf4-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="3abf4-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="3abf4-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3abf4-138">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3abf4-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3abf4-139">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="3abf4-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="3abf4-140">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="3abf4-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
