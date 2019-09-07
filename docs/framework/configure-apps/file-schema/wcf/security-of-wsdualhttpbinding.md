---
title: <security> z <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: b6a1c952b1ae65c8fb6f17237b5c15f3a8d4844a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399751"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="1353d-102">\<> zabezpečení > \<WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="1353d-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="1353d-103">Definuje možnosti [ \<zabezpečení WSDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1353d-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
<span data-ttu-id="1353d-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1353d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1353d-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1353d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1353d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1353d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="1353d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsDualHttpBinding >** ](wsdualhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1353d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)</span></span>\
<span data-ttu-id="1353d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="1353d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="1353d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="1353d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1353d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1353d-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1353d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1353d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1353d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1353d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1353d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1353d-113">Attributes</span></span>  
  
|<span data-ttu-id="1353d-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="1353d-114">Attribute</span></span>|<span data-ttu-id="1353d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1353d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1353d-116">režim</span><span class="sxs-lookup"><span data-stu-id="1353d-116">mode</span></span>|<span data-ttu-id="1353d-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1353d-117">-   Optional.</span></span> <span data-ttu-id="1353d-118">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="1353d-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="1353d-119">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="1353d-119">The default value is `Message`.</span></span> <span data-ttu-id="1353d-120">Tento atribut je typu <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="1353d-120">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="1353d-121">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="1353d-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="1353d-122">Value</span><span class="sxs-lookup"><span data-stu-id="1353d-122">Value</span></span>|<span data-ttu-id="1353d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="1353d-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1353d-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="1353d-124">None</span></span>|<span data-ttu-id="1353d-125">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="1353d-125">Security is disabled.</span></span>|  
|<span data-ttu-id="1353d-126">Message</span><span class="sxs-lookup"><span data-stu-id="1353d-126">Message</span></span>|<span data-ttu-id="1353d-127">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="1353d-127">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1353d-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1353d-128">Child Elements</span></span>  
  
|<span data-ttu-id="1353d-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="1353d-129">Element</span></span>|<span data-ttu-id="1353d-130">Popis</span><span class="sxs-lookup"><span data-stu-id="1353d-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1353d-131">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="1353d-131">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="1353d-132">Definuje nastavení pro zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="1353d-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="1353d-133">Tento prvek je typu <xref:System.ServiceModel.MessageSecurityOverHttp>.</span><span class="sxs-lookup"><span data-stu-id="1353d-133">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1353d-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1353d-134">Parent Elements</span></span>  
  
|<span data-ttu-id="1353d-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="1353d-135">Element</span></span>|<span data-ttu-id="1353d-136">Popis</span><span class="sxs-lookup"><span data-stu-id="1353d-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1353d-137">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="1353d-137">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="1353d-138">Definuje všechny schopnosti [ \<vazby wsDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1353d-138">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1353d-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1353d-139">Remarks</span></span>  
 <span data-ttu-id="1353d-140">Duální vazba zpřístupňuje IP adresu klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="1353d-140">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="1353d-141">Klient by měl použít zabezpečení, aby zajistil, že se připojí pouze ke službám, kterým důvěřuje.</span><span class="sxs-lookup"><span data-stu-id="1353d-141">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1353d-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1353d-142">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="1353d-143">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="1353d-143">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1353d-144">Vazby</span><span class="sxs-lookup"><span data-stu-id="1353d-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1353d-145">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="1353d-145">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1353d-146">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="1353d-146">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1353d-147">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="1353d-147">\<binding></span></span>](../../../misc/binding.md)
