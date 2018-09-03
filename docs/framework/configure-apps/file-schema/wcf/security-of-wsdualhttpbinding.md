---
title: '&lt;security&gt; – &lt;wsDualHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 023e0dd2a89c005928625cf95f3de61af81c7b6b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464996"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="67c47-102">&lt;security&gt; – &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="67c47-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="67c47-103">Definuje možnosti zabezpečení [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="67c47-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="67c47-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="67c47-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="67c47-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="67c47-105">\<bindings></span></span>  
<span data-ttu-id="67c47-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="67c47-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="67c47-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="67c47-107">\<binding></span></span>  
<span data-ttu-id="67c47-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="67c47-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67c47-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67c47-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67c47-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="67c47-110">Attributes and Elements</span></span>  
 <span data-ttu-id="67c47-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="67c47-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67c47-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="67c47-112">Attributes</span></span>  
  
|<span data-ttu-id="67c47-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="67c47-113">Attribute</span></span>|<span data-ttu-id="67c47-114">Popis</span><span class="sxs-lookup"><span data-stu-id="67c47-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67c47-115">režim</span><span class="sxs-lookup"><span data-stu-id="67c47-115">mode</span></span>|<span data-ttu-id="67c47-116">– Volitelné.</span><span class="sxs-lookup"><span data-stu-id="67c47-116">-   Optional.</span></span> <span data-ttu-id="67c47-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="67c47-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="67c47-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="67c47-118">The default value is `Message`.</span></span> <span data-ttu-id="67c47-119">Tento atribut je typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="67c47-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="67c47-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="67c47-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="67c47-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="67c47-121">Value</span></span>|<span data-ttu-id="67c47-122">Popis</span><span class="sxs-lookup"><span data-stu-id="67c47-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="67c47-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="67c47-123">None</span></span>|<span data-ttu-id="67c47-124">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="67c47-124">Security is disabled.</span></span>|  
|<span data-ttu-id="67c47-125">Zpráva</span><span class="sxs-lookup"><span data-stu-id="67c47-125">Message</span></span>|<span data-ttu-id="67c47-126">Poskytuje zabezpečení pomocí zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="67c47-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67c47-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="67c47-127">Child Elements</span></span>  
  
|<span data-ttu-id="67c47-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="67c47-128">Element</span></span>|<span data-ttu-id="67c47-129">Popis</span><span class="sxs-lookup"><span data-stu-id="67c47-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67c47-130">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="67c47-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="67c47-131">Definuje nastavení založená na úrovni zpráv zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="67c47-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="67c47-132">Tento prvek je typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="67c47-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67c47-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="67c47-133">Parent Elements</span></span>  
  
|<span data-ttu-id="67c47-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="67c47-134">Element</span></span>|<span data-ttu-id="67c47-135">Popis</span><span class="sxs-lookup"><span data-stu-id="67c47-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67c47-136">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="67c47-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="67c47-137">Definuje všechny vazby funkce [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="67c47-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67c47-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67c47-138">Remarks</span></span>  
 <span data-ttu-id="67c47-139">Duální vazby poskytuje IP adresu klienta do služby.</span><span class="sxs-lookup"><span data-stu-id="67c47-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="67c47-140">Klient musí použít zabezpečení zajistit, že pouze připojení ke službám ho vztahy důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="67c47-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c47-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="67c47-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="67c47-142">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="67c47-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="67c47-143">Vazby</span><span class="sxs-lookup"><span data-stu-id="67c47-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="67c47-144">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="67c47-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="67c47-145">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="67c47-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="67c47-146">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="67c47-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
