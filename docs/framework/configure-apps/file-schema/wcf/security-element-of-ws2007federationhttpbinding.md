---
title: Element &lt;security&gt; – &lt;ws2007FederationHttpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 87f8f3cf296aeb30cd19c7579887ef94e0992ba7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44194978"
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="bd82a-102">Element &lt;security&gt; – &lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="bd82a-102">&lt;security&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="bd82a-103">Definuje nastavení zabezpečení [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="bd82a-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="bd82a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bd82a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bd82a-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="bd82a-105">\<bindings></span></span>  
<span data-ttu-id="bd82a-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="bd82a-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="bd82a-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="bd82a-107">\<binding></span></span>  
<span data-ttu-id="bd82a-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="bd82a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd82a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd82a-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd82a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bd82a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bd82a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bd82a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd82a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="bd82a-112">Attributes</span></span>  
  
|<span data-ttu-id="bd82a-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="bd82a-113">Attribute</span></span>|<span data-ttu-id="bd82a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bd82a-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="bd82a-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="bd82a-115">Optional.</span></span> <span data-ttu-id="bd82a-116">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="bd82a-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="bd82a-117">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="bd82a-117">The default value is `Message`.</span></span> <span data-ttu-id="bd82a-118">Tento atribut je typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="bd82a-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="bd82a-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="bd82a-119">mode Attribute</span></span>  
  
|<span data-ttu-id="bd82a-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bd82a-120">Value</span></span>|<span data-ttu-id="bd82a-121">Popis</span><span class="sxs-lookup"><span data-stu-id="bd82a-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bd82a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="bd82a-122">None</span></span>|<span data-ttu-id="bd82a-123">Zprávu protokolu SOAP není zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="bd82a-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="bd82a-124">Zpráva</span><span class="sxs-lookup"><span data-stu-id="bd82a-124">Message</span></span>|<span data-ttu-id="bd82a-125">Integrity, šifrování, ověřování serveru a klienta ověřování zajišťuje zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="bd82a-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="bd82a-126">Ve výchozím nastavení je tělo zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="bd82a-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="bd82a-127">Služba musí být nakonfigurován s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="bd82a-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="bd82a-128">Ověření klienta je založen na token vydaný pro klienta služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bd82a-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="bd82a-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="bd82a-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="bd82a-130">Jsou k dispozici integritu a důvěrnost serveru ověřování pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bd82a-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="bd82a-131">Služba musí být nakonfigurován s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="bd82a-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="bd82a-132">Ověření klienta se poskytuje prostřednictvím zabezpečení zprávy protokolu SOAP a je založena na token vydaný pro klienta služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bd82a-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd82a-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bd82a-133">Child Elements</span></span>  
  
|<span data-ttu-id="bd82a-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="bd82a-134">Element</span></span>|<span data-ttu-id="bd82a-135">Popis</span><span class="sxs-lookup"><span data-stu-id="bd82a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd82a-136">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="bd82a-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="bd82a-137">Definuje nastavení založená na úrovni zpráv zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bd82a-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="bd82a-138">Tento prvek je typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="bd82a-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd82a-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bd82a-139">Parent Elements</span></span>  
  
|<span data-ttu-id="bd82a-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="bd82a-140">Element</span></span>|<span data-ttu-id="bd82a-141">Popis</span><span class="sxs-lookup"><span data-stu-id="bd82a-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd82a-142">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="bd82a-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bd82a-143">Definuje všechny vazby funkce [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bd82a-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd82a-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd82a-144">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="bd82a-145">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="bd82a-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="bd82a-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="bd82a-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="bd82a-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="bd82a-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="bd82a-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="bd82a-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bd82a-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="bd82a-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="bd82a-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="bd82a-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="bd82a-151">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="bd82a-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
