---
title: <security>prvek elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 450b2403b8cd4ec43a41fd27bccb3b77202820bb
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399909"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="9a086-102">\<prvek zabezpečení > > \<WS2007FederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9a086-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="9a086-103">Definuje nastavení [ \<zabezpečení elementu WS2007FederationHttpBinding >](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="9a086-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="9a086-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9a086-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9a086-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9a086-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9a086-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="9a086-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="9a086-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="9a086-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="9a086-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="9a086-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="9a086-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="9a086-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a086-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a086-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a086-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9a086-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9a086-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9a086-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a086-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="9a086-113">Attributes</span></span>  
  
|<span data-ttu-id="9a086-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="9a086-114">Attribute</span></span>|<span data-ttu-id="9a086-115">Popis</span><span class="sxs-lookup"><span data-stu-id="9a086-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="9a086-116">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="9a086-116">Optional.</span></span> <span data-ttu-id="9a086-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="9a086-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="9a086-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="9a086-118">The default value is `Message`.</span></span> <span data-ttu-id="9a086-119">Tento atribut je typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="9a086-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="9a086-120">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="9a086-120">mode Attribute</span></span>  
  
|<span data-ttu-id="9a086-121">Value</span><span class="sxs-lookup"><span data-stu-id="9a086-121">Value</span></span>|<span data-ttu-id="9a086-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9a086-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9a086-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="9a086-123">None</span></span>|<span data-ttu-id="9a086-124">Zpráva SOAP není během přenosu zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="9a086-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="9a086-125">Message</span><span class="sxs-lookup"><span data-stu-id="9a086-125">Message</span></span>|<span data-ttu-id="9a086-126">Integrita, důvěrnost, ověřování serveru a ověřování klientů jsou k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="9a086-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="9a086-127">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="9a086-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="9a086-128">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="9a086-128">The service must be configured with a certificate.</span></span> <span data-ttu-id="9a086-129">Ověřování klientů vychází z tokenu vystaveného klientovi tokenem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9a086-129">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="9a086-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="9a086-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="9a086-131">Integrita, důvěrnost a ověřování serveru poskytuje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9a086-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="9a086-132">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="9a086-132">The service must be configured with a certificate.</span></span> <span data-ttu-id="9a086-133">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP a je založeno na tokenu vydanému klientovi pomocí služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9a086-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a086-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9a086-134">Child Elements</span></span>  
  
|<span data-ttu-id="9a086-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="9a086-135">Element</span></span>|<span data-ttu-id="9a086-136">Popis</span><span class="sxs-lookup"><span data-stu-id="9a086-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a086-137">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="9a086-137">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="9a086-138">Definuje nastavení pro zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="9a086-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="9a086-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="9a086-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a086-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9a086-140">Parent Elements</span></span>  
  
|<span data-ttu-id="9a086-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="9a086-141">Element</span></span>|<span data-ttu-id="9a086-142">Popis</span><span class="sxs-lookup"><span data-stu-id="9a086-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a086-143">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="9a086-143">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="9a086-144">Definuje všechny schopnosti [ \<vazby wsDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9a086-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a086-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a086-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="9a086-146">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9a086-146">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="9a086-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="9a086-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9a086-148">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="9a086-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="9a086-149">Vazby</span><span class="sxs-lookup"><span data-stu-id="9a086-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9a086-150">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="9a086-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9a086-151">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="9a086-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9a086-152">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="9a086-152">\<binding></span></span>](../../../misc/binding.md)
