---
title: <security> Element <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 15740144b0aad7eb2798db4712e4769d08d893a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670544"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="eb9c5-102">\<zabezpečení > prvek \<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="eb9c5-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="eb9c5-103">Definuje nastavení zabezpečení [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="eb9c5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eb9c5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="eb9c5-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="eb9c5-105">\<bindings></span></span>  
<span data-ttu-id="eb9c5-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="eb9c5-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="eb9c5-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="eb9c5-107">\<binding></span></span>  
<span data-ttu-id="eb9c5-108">\<security></span><span class="sxs-lookup"><span data-stu-id="eb9c5-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb9c5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb9c5-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb9c5-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eb9c5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="eb9c5-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb9c5-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="eb9c5-112">Attributes</span></span>  
  
|<span data-ttu-id="eb9c5-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="eb9c5-113">Attribute</span></span>|<span data-ttu-id="eb9c5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="eb9c5-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="eb9c5-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-115">Optional.</span></span> <span data-ttu-id="eb9c5-116">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="eb9c5-117">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-117">The default value is `Message`.</span></span> <span data-ttu-id="eb9c5-118">Tento atribut je typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="eb9c5-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="eb9c5-119">mode Attribute</span></span>  
  
|<span data-ttu-id="eb9c5-120">Value</span><span class="sxs-lookup"><span data-stu-id="eb9c5-120">Value</span></span>|<span data-ttu-id="eb9c5-121">Popis</span><span class="sxs-lookup"><span data-stu-id="eb9c5-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eb9c5-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="eb9c5-122">None</span></span>|<span data-ttu-id="eb9c5-123">Zprávu protokolu SOAP není zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="eb9c5-124">Zpráva</span><span class="sxs-lookup"><span data-stu-id="eb9c5-124">Message</span></span>|<span data-ttu-id="eb9c5-125">Integrity, šifrování, ověřování serveru a klienta ověřování zajišťuje zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="eb9c5-126">Ve výchozím nastavení je tělo zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="eb9c5-127">Služba musí být nakonfigurován s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="eb9c5-128">Ověření klienta je založen na token vydaný pro klienta služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="eb9c5-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="eb9c5-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="eb9c5-130">Jsou k dispozici integritu a důvěrnost serveru ověřování pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="eb9c5-131">Služba musí být nakonfigurován s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="eb9c5-132">Ověření klienta se poskytuje prostřednictvím zabezpečení zprávy protokolu SOAP a je založena na token vydaný pro klienta služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb9c5-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eb9c5-133">Child Elements</span></span>  
  
|<span data-ttu-id="eb9c5-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="eb9c5-134">Element</span></span>|<span data-ttu-id="eb9c5-135">Popis</span><span class="sxs-lookup"><span data-stu-id="eb9c5-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb9c5-136">\<message></span><span class="sxs-lookup"><span data-stu-id="eb9c5-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="eb9c5-137">Definuje nastavení založená na úrovni zpráv zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="eb9c5-138">Tento prvek je typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="eb9c5-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb9c5-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eb9c5-139">Parent Elements</span></span>  
  
|<span data-ttu-id="eb9c5-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="eb9c5-140">Element</span></span>|<span data-ttu-id="eb9c5-141">Popis</span><span class="sxs-lookup"><span data-stu-id="eb9c5-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb9c5-142">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="eb9c5-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="eb9c5-143">Definuje všechny vazby funkce [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="eb9c5-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb9c5-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb9c5-144">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="eb9c5-145">Postupy: Vytvoření instance WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="eb9c5-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="eb9c5-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="eb9c5-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="eb9c5-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="eb9c5-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="eb9c5-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="eb9c5-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="eb9c5-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="eb9c5-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="eb9c5-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="eb9c5-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="eb9c5-151">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="eb9c5-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
