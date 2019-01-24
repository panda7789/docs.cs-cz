---
title: '&lt;security&gt; – &lt;wsDualHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 56755ec62c6e2c35ecdb94e4aa58903ed1216378
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555934"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="0f505-102">&lt;security&gt; – &lt;wsDualHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="0f505-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="0f505-103">Definuje možnosti zabezpečení [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0f505-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="0f505-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0f505-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0f505-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="0f505-105">\<bindings></span></span>  
<span data-ttu-id="0f505-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0f505-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="0f505-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0f505-107">\<binding></span></span>  
<span data-ttu-id="0f505-108">\<security></span><span class="sxs-lookup"><span data-stu-id="0f505-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f505-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f505-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f505-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0f505-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0f505-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0f505-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f505-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0f505-112">Attributes</span></span>  
  
|<span data-ttu-id="0f505-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0f505-113">Attribute</span></span>|<span data-ttu-id="0f505-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0f505-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f505-115">režim</span><span class="sxs-lookup"><span data-stu-id="0f505-115">mode</span></span>|<span data-ttu-id="0f505-116">– Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0f505-116">-   Optional.</span></span> <span data-ttu-id="0f505-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="0f505-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="0f505-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="0f505-118">The default value is `Message`.</span></span> <span data-ttu-id="0f505-119">Tento atribut je typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0f505-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0f505-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="0f505-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="0f505-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0f505-121">Value</span></span>|<span data-ttu-id="0f505-122">Popis</span><span class="sxs-lookup"><span data-stu-id="0f505-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0f505-123">Žádná</span><span class="sxs-lookup"><span data-stu-id="0f505-123">None</span></span>|<span data-ttu-id="0f505-124">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="0f505-124">Security is disabled.</span></span>|  
|<span data-ttu-id="0f505-125">Zpráva</span><span class="sxs-lookup"><span data-stu-id="0f505-125">Message</span></span>|<span data-ttu-id="0f505-126">Poskytuje zabezpečení pomocí zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="0f505-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f505-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0f505-127">Child Elements</span></span>  
  
|<span data-ttu-id="0f505-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="0f505-128">Element</span></span>|<span data-ttu-id="0f505-129">Popis</span><span class="sxs-lookup"><span data-stu-id="0f505-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f505-130">\<message></span><span class="sxs-lookup"><span data-stu-id="0f505-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="0f505-131">Definuje nastavení založená na úrovni zpráv zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0f505-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="0f505-132">Tento prvek je typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="0f505-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0f505-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0f505-133">Parent Elements</span></span>  
  
|<span data-ttu-id="0f505-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="0f505-134">Element</span></span>|<span data-ttu-id="0f505-135">Popis</span><span class="sxs-lookup"><span data-stu-id="0f505-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f505-136">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0f505-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0f505-137">Definuje všechny vazby funkce [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0f505-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f505-138">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f505-138">Remarks</span></span>  
 <span data-ttu-id="0f505-139">Duální vazby poskytuje IP adresu klienta do služby.</span><span class="sxs-lookup"><span data-stu-id="0f505-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="0f505-140">Klient musí použít zabezpečení zajistit, že pouze připojení ke službám ho vztahy důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="0f505-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f505-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f505-141">See also</span></span>
- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="0f505-142">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0f505-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0f505-143">Vazby</span><span class="sxs-lookup"><span data-stu-id="0f505-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="0f505-144">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="0f505-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0f505-145">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0f505-145">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0f505-146">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0f505-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
