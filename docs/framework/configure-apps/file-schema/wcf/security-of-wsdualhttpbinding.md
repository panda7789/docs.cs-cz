---
title: "&lt;security&gt; – &lt;wsDualHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 6680d01b068a6ac1c4f9abcda69779c9cd0786a0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="260c9-102">&lt;security&gt; – &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="260c9-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="260c9-103">Definuje možnosti zabezpečení [ \<– wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="260c9-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="260c9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="260c9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="260c9-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="260c9-105">\<bindings></span></span>  
<span data-ttu-id="260c9-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="260c9-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="260c9-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="260c9-107">\<binding></span></span>  
<span data-ttu-id="260c9-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="260c9-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="260c9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="260c9-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="260c9-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="260c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="260c9-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="260c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="260c9-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="260c9-112">Attributes</span></span>  
  
|<span data-ttu-id="260c9-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="260c9-113">Attribute</span></span>|<span data-ttu-id="260c9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="260c9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="260c9-115">režim</span><span class="sxs-lookup"><span data-stu-id="260c9-115">mode</span></span>|<span data-ttu-id="260c9-116">-Volitelné.</span><span class="sxs-lookup"><span data-stu-id="260c9-116">-   Optional.</span></span> <span data-ttu-id="260c9-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="260c9-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="260c9-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="260c9-118">The default value is `Message`.</span></span> <span data-ttu-id="260c9-119">Tento atribut je typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="260c9-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="260c9-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="260c9-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="260c9-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="260c9-121">Value</span></span>|<span data-ttu-id="260c9-122">Popis</span><span class="sxs-lookup"><span data-stu-id="260c9-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="260c9-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="260c9-123">None</span></span>|<span data-ttu-id="260c9-124">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="260c9-124">Security is disabled.</span></span>|  
|<span data-ttu-id="260c9-125">Zpráva</span><span class="sxs-lookup"><span data-stu-id="260c9-125">Message</span></span>|<span data-ttu-id="260c9-126">Zabezpečení je k dispozici pomocí zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="260c9-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="260c9-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="260c9-127">Child Elements</span></span>  
  
|<span data-ttu-id="260c9-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="260c9-128">Element</span></span>|<span data-ttu-id="260c9-129">Popis</span><span class="sxs-lookup"><span data-stu-id="260c9-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="260c9-130">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="260c9-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="260c9-131">Definuje nastavení pro zprávy úroveň zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="260c9-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="260c9-132">Tento element je typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="260c9-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="260c9-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="260c9-133">Parent Elements</span></span>  
  
|<span data-ttu-id="260c9-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="260c9-134">Element</span></span>|<span data-ttu-id="260c9-135">Popis</span><span class="sxs-lookup"><span data-stu-id="260c9-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="260c9-136">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="260c9-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="260c9-137">Definuje všechny možnosti vazby [ \<– wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="260c9-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="260c9-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="260c9-138">Remarks</span></span>  
 <span data-ttu-id="260c9-139">Duální vazbu zpřístupní IP adresu klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="260c9-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="260c9-140">Klient musí použít zabezpečení zajistit, že pouze připojení k službám ho vztahy důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="260c9-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="260c9-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="260c9-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="260c9-142">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="260c9-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="260c9-143">Vazby</span><span class="sxs-lookup"><span data-stu-id="260c9-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="260c9-144">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="260c9-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="260c9-145">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="260c9-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="260c9-146">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="260c9-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
