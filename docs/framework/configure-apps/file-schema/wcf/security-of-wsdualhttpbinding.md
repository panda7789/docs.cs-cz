---
title: <security> z <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: bed7f4ce325e0d5e387e310ca15a3b72ac93f18e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936547"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="a7f32-102">\<> zabezpečení > \<WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a7f32-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="a7f32-103">Definuje možnosti [ \<zabezpečení WSDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a7f32-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="a7f32-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a7f32-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7f32-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="a7f32-105">\<bindings></span></span>  
<span data-ttu-id="a7f32-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a7f32-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="a7f32-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="a7f32-107">\<binding></span></span>  
<span data-ttu-id="a7f32-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a7f32-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f32-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7f32-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7f32-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a7f32-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a7f32-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a7f32-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7f32-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a7f32-112">Attributes</span></span>  
  
|<span data-ttu-id="a7f32-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a7f32-113">Attribute</span></span>|<span data-ttu-id="a7f32-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a7f32-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7f32-115">režim</span><span class="sxs-lookup"><span data-stu-id="a7f32-115">mode</span></span>|<span data-ttu-id="a7f32-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a7f32-116">-   Optional.</span></span> <span data-ttu-id="a7f32-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="a7f32-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a7f32-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="a7f32-118">The default value is `Message`.</span></span> <span data-ttu-id="a7f32-119">Tento atribut je typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a7f32-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a7f32-120">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="a7f32-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="a7f32-121">Value</span><span class="sxs-lookup"><span data-stu-id="a7f32-121">Value</span></span>|<span data-ttu-id="a7f32-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a7f32-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a7f32-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="a7f32-123">None</span></span>|<span data-ttu-id="a7f32-124">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="a7f32-124">Security is disabled.</span></span>|  
|<span data-ttu-id="a7f32-125">Message</span><span class="sxs-lookup"><span data-stu-id="a7f32-125">Message</span></span>|<span data-ttu-id="a7f32-126">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="a7f32-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7f32-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a7f32-127">Child Elements</span></span>  
  
|<span data-ttu-id="a7f32-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="a7f32-128">Element</span></span>|<span data-ttu-id="a7f32-129">Popis</span><span class="sxs-lookup"><span data-stu-id="a7f32-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7f32-130">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="a7f32-130">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="a7f32-131">Definuje nastavení pro zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="a7f32-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="a7f32-132">Tento prvek je typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="a7f32-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7f32-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a7f32-133">Parent Elements</span></span>  
  
|<span data-ttu-id="a7f32-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="a7f32-134">Element</span></span>|<span data-ttu-id="a7f32-135">Popis</span><span class="sxs-lookup"><span data-stu-id="a7f32-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7f32-136">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="a7f32-136">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="a7f32-137">Definuje všechny schopnosti [ \<vazby wsDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a7f32-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7f32-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7f32-138">Remarks</span></span>  
 <span data-ttu-id="a7f32-139">Duální vazba zpřístupňuje IP adresu klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="a7f32-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="a7f32-140">Klient by měl použít zabezpečení, aby zajistil, že se připojí pouze ke službám, kterým důvěřuje.</span><span class="sxs-lookup"><span data-stu-id="a7f32-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f32-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7f32-141">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="a7f32-142">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a7f32-142">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a7f32-143">Vazby</span><span class="sxs-lookup"><span data-stu-id="a7f32-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a7f32-144">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="a7f32-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a7f32-145">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a7f32-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a7f32-146">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="a7f32-146">\<binding></span></span>](../../../misc/binding.md)
