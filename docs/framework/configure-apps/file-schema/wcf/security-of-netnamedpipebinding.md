---
title: '&lt;security&gt; – &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 74bf0d14b0acfd8a5382575d2ee1e51174b6b6b8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752790"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="2199c-102">&lt;security&gt; – &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="2199c-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="2199c-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="2199c-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="2199c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2199c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2199c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="2199c-105">\<bindings></span></span>  
<span data-ttu-id="2199c-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="2199c-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="2199c-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="2199c-107">\<binding></span></span>  
<span data-ttu-id="2199c-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="2199c-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2199c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2199c-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2199c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2199c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2199c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2199c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2199c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2199c-112">Attributes</span></span>  
  
|<span data-ttu-id="2199c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2199c-113">Attribute</span></span>|<span data-ttu-id="2199c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2199c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2199c-115">režim</span><span class="sxs-lookup"><span data-stu-id="2199c-115">mode</span></span>|<span data-ttu-id="2199c-116">Určuje typ zabezpečení, který se použije pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="2199c-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="2199c-117">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="2199c-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2199c-118">-None: To zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2199c-118">-   None: This disables security.</span></span><br /><span data-ttu-id="2199c-119">-Přenos: Zabezpečení je zajištěno pomocí základního zabezpečení přenosu na základě.</span><span class="sxs-lookup"><span data-stu-id="2199c-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="2199c-120">Je možné kontrolovat úroveň ochrany s Tento režim.</span><span class="sxs-lookup"><span data-stu-id="2199c-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="2199c-121">-Výchozí hodnota je přenos.</span><span class="sxs-lookup"><span data-stu-id="2199c-121">-   The default value is Transport.</span></span> <span data-ttu-id="2199c-122">Tento atribut je typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="2199c-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2199c-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2199c-123">Child Elements</span></span>  
  
|<span data-ttu-id="2199c-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="2199c-124">Element</span></span>|<span data-ttu-id="2199c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="2199c-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2199c-126">transport</span><span class="sxs-lookup"><span data-stu-id="2199c-126">transport</span></span>|<span data-ttu-id="2199c-127">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="2199c-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="2199c-128">Tento element je typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2199c-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2199c-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2199c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2199c-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="2199c-130">Element</span></span>|<span data-ttu-id="2199c-131">Popis</span><span class="sxs-lookup"><span data-stu-id="2199c-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2199c-132">vazba</span><span class="sxs-lookup"><span data-stu-id="2199c-132">binding</span></span>|<span data-ttu-id="2199c-133">Element vazby [ \<– netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="2199c-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2199c-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="2199c-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="2199c-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2199c-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="2199c-136">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="2199c-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="2199c-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="2199c-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2199c-138">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="2199c-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2199c-139">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="2199c-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="2199c-140">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="2199c-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
