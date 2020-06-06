---
title: <security> z <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 4969c041678bbf3490975bc0ec53507b6cf762bb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738605"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="3f010-102">\<security> z \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="3f010-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="3f010-103">Definuje možnosti zabezpečení [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="3f010-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="3f010-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f010-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f010-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3f010-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3f010-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3f010-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f010-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3f010-107">Attributes</span></span>  
  
|<span data-ttu-id="3f010-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="3f010-108">Attribute</span></span>|<span data-ttu-id="3f010-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3f010-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f010-110">režim</span><span class="sxs-lookup"><span data-stu-id="3f010-110">mode</span></span>|<span data-ttu-id="3f010-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3f010-111">-   Optional.</span></span> <span data-ttu-id="3f010-112">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="3f010-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="3f010-113">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="3f010-113">The default value is `Message`.</span></span> <span data-ttu-id="3f010-114">Tento atribut je typu <xref:System.ServiceModel.WSDualHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="3f010-114">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="3f010-115">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="3f010-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="3f010-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3f010-116">Value</span></span>|<span data-ttu-id="3f010-117">Description</span><span class="sxs-lookup"><span data-stu-id="3f010-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3f010-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="3f010-118">None</span></span>|<span data-ttu-id="3f010-119">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="3f010-119">Security is disabled.</span></span>|  
|<span data-ttu-id="3f010-120">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3f010-120">Message</span></span>|<span data-ttu-id="3f010-121">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="3f010-121">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f010-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3f010-122">Child Elements</span></span>  
  
|<span data-ttu-id="3f010-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="3f010-123">Element</span></span>|<span data-ttu-id="3f010-124">Description</span><span class="sxs-lookup"><span data-stu-id="3f010-124">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="3f010-125">Definuje nastavení pro zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="3f010-125">Defines the settings for the message-level security.</span></span> <span data-ttu-id="3f010-126">Tento prvek je typu <xref:System.ServiceModel.MessageSecurityOverHttp> .</span><span class="sxs-lookup"><span data-stu-id="3f010-126">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f010-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3f010-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3f010-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="3f010-128">Element</span></span>|<span data-ttu-id="3f010-129">Description</span><span class="sxs-lookup"><span data-stu-id="3f010-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="3f010-130">Definuje všechny schopnosti vazby pro [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="3f010-130">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f010-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f010-131">Remarks</span></span>  
 <span data-ttu-id="3f010-132">Duální vazba zpřístupňuje IP adresu klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="3f010-132">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="3f010-133">Klient by měl použít zabezpečení, aby zajistil, že se připojí pouze ke službám, kterým důvěřuje.</span><span class="sxs-lookup"><span data-stu-id="3f010-133">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f010-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f010-134">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="3f010-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3f010-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3f010-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="3f010-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3f010-137">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3f010-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3f010-138">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3f010-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
