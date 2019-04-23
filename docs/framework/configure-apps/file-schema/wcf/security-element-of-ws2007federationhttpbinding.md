---
title: <security> Element <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 15740144b0aad7eb2798db4712e4769d08d893a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186859"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="0fecd-102">\<zabezpečení > prvek \<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0fecd-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="0fecd-103">Definuje nastavení zabezpečení [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="0fecd-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="0fecd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0fecd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0fecd-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="0fecd-105">\<bindings></span></span>  
<span data-ttu-id="0fecd-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="0fecd-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="0fecd-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0fecd-107">\<binding></span></span>  
<span data-ttu-id="0fecd-108">\<security></span><span class="sxs-lookup"><span data-stu-id="0fecd-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fecd-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fecd-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fecd-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0fecd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0fecd-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0fecd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fecd-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0fecd-112">Attributes</span></span>  
  
|<span data-ttu-id="0fecd-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0fecd-113">Attribute</span></span>|<span data-ttu-id="0fecd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0fecd-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="0fecd-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0fecd-115">Optional.</span></span> <span data-ttu-id="0fecd-116">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="0fecd-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="0fecd-117">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="0fecd-117">The default value is `Message`.</span></span> <span data-ttu-id="0fecd-118">Tento atribut je typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0fecd-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0fecd-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="0fecd-119">mode Attribute</span></span>  
  
|<span data-ttu-id="0fecd-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0fecd-120">Value</span></span>|<span data-ttu-id="0fecd-121">Popis</span><span class="sxs-lookup"><span data-stu-id="0fecd-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0fecd-122">Žádný</span><span class="sxs-lookup"><span data-stu-id="0fecd-122">None</span></span>|<span data-ttu-id="0fecd-123">Zprávu protokolu SOAP není zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="0fecd-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="0fecd-124">Zpráva</span><span class="sxs-lookup"><span data-stu-id="0fecd-124">Message</span></span>|<span data-ttu-id="0fecd-125">Integrity, šifrování, ověřování serveru a klienta ověřování zajišťuje zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="0fecd-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="0fecd-126">Ve výchozím nastavení je tělo zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="0fecd-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="0fecd-127">Služba musí být nakonfigurován s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="0fecd-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="0fecd-128">Ověření klienta je založen na token vydaný pro klienta služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0fecd-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="0fecd-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="0fecd-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="0fecd-130">Jsou k dispozici integritu a důvěrnost serveru ověřování pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0fecd-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="0fecd-131">Služba musí být nakonfigurován s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="0fecd-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="0fecd-132">Ověření klienta se poskytuje prostřednictvím zabezpečení zprávy protokolu SOAP a je založena na token vydaný pro klienta služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0fecd-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fecd-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0fecd-133">Child Elements</span></span>  
  
|<span data-ttu-id="0fecd-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="0fecd-134">Element</span></span>|<span data-ttu-id="0fecd-135">Popis</span><span class="sxs-lookup"><span data-stu-id="0fecd-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fecd-136">\<message></span><span class="sxs-lookup"><span data-stu-id="0fecd-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="0fecd-137">Definuje nastavení založená na úrovni zpráv zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0fecd-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="0fecd-138">Tento prvek je typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="0fecd-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fecd-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0fecd-139">Parent Elements</span></span>  
  
|<span data-ttu-id="0fecd-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="0fecd-140">Element</span></span>|<span data-ttu-id="0fecd-141">Popis</span><span class="sxs-lookup"><span data-stu-id="0fecd-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fecd-142">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0fecd-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0fecd-143">Definuje všechny vazby funkce [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0fecd-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fecd-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fecd-144">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="0fecd-145">Postupy: Vytvoření instance WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0fecd-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="0fecd-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0fecd-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0fecd-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="0fecd-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="0fecd-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="0fecd-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="0fecd-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="0fecd-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0fecd-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0fecd-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0fecd-151">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0fecd-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
