---
title: <security>prvek elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 61b56ca1fae5c328cda0bbebef4026f0784095a3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936822"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="59898-102">\<prvek zabezpečení > > \<WS2007FederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="59898-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="59898-103">Definuje nastavení [ \<zabezpečení elementu WS2007FederationHttpBinding >](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="59898-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="59898-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="59898-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="59898-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="59898-105">\<bindings></span></span>  
<span data-ttu-id="59898-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="59898-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="59898-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="59898-107">\<binding></span></span>  
<span data-ttu-id="59898-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="59898-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59898-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59898-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59898-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59898-110">Attributes and Elements</span></span>  
 <span data-ttu-id="59898-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59898-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59898-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="59898-112">Attributes</span></span>  
  
|<span data-ttu-id="59898-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="59898-113">Attribute</span></span>|<span data-ttu-id="59898-114">Popis</span><span class="sxs-lookup"><span data-stu-id="59898-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="59898-115">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="59898-115">Optional.</span></span> <span data-ttu-id="59898-116">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="59898-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="59898-117">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="59898-117">The default value is `Message`.</span></span> <span data-ttu-id="59898-118">Tento atribut je typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="59898-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="59898-119">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="59898-119">mode Attribute</span></span>  
  
|<span data-ttu-id="59898-120">Value</span><span class="sxs-lookup"><span data-stu-id="59898-120">Value</span></span>|<span data-ttu-id="59898-121">Popis</span><span class="sxs-lookup"><span data-stu-id="59898-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="59898-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="59898-122">None</span></span>|<span data-ttu-id="59898-123">Zpráva SOAP není během přenosu zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="59898-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="59898-124">Message</span><span class="sxs-lookup"><span data-stu-id="59898-124">Message</span></span>|<span data-ttu-id="59898-125">Integrita, důvěrnost, ověřování serveru a ověřování klientů jsou k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="59898-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="59898-126">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="59898-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="59898-127">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="59898-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="59898-128">Ověřování klientů vychází z tokenu vystaveného klientovi tokenem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59898-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="59898-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="59898-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="59898-130">Integrita, důvěrnost a ověřování serveru poskytuje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="59898-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="59898-131">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="59898-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="59898-132">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP a je založeno na tokenu vydanému klientovi pomocí služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59898-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59898-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59898-133">Child Elements</span></span>  
  
|<span data-ttu-id="59898-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="59898-134">Element</span></span>|<span data-ttu-id="59898-135">Popis</span><span class="sxs-lookup"><span data-stu-id="59898-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59898-136">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="59898-136">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="59898-137">Definuje nastavení pro zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="59898-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="59898-138">Tento prvek je typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="59898-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59898-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59898-139">Parent Elements</span></span>  
  
|<span data-ttu-id="59898-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="59898-140">Element</span></span>|<span data-ttu-id="59898-141">Popis</span><span class="sxs-lookup"><span data-stu-id="59898-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59898-142">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="59898-142">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="59898-143">Definuje všechny schopnosti [ \<vazby wsDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="59898-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59898-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59898-144">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="59898-145">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="59898-145">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="59898-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="59898-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="59898-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="59898-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="59898-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="59898-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="59898-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="59898-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="59898-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="59898-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="59898-151">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="59898-151">\<binding></span></span>](../../../misc/binding.md)
