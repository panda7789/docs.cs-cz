---
title: <security>prvek elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: b85c54c6507313522286e0c66504cfd0c8afb2b0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738720"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="990df-102">\<security>prvek elementu\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="990df-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="990df-103">Definuje nastavení zabezpečení [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="990df-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="990df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="990df-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="990df-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="990df-105">Attributes and Elements</span></span>  
 <span data-ttu-id="990df-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="990df-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="990df-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="990df-107">Attributes</span></span>  
  
|<span data-ttu-id="990df-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="990df-108">Attribute</span></span>|<span data-ttu-id="990df-109">Popis</span><span class="sxs-lookup"><span data-stu-id="990df-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="990df-110">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="990df-110">Optional.</span></span> <span data-ttu-id="990df-111">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="990df-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="990df-112">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="990df-112">The default value is `Message`.</span></span> <span data-ttu-id="990df-113">Tento atribut je typu <xref:System.ServiceModel.WSFederationHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="990df-113">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="990df-114">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="990df-114">mode Attribute</span></span>  
  
|<span data-ttu-id="990df-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="990df-115">Value</span></span>|<span data-ttu-id="990df-116">Description</span><span class="sxs-lookup"><span data-stu-id="990df-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="990df-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="990df-117">None</span></span>|<span data-ttu-id="990df-118">Zpráva SOAP není během přenosu zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="990df-118">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="990df-119">Zpráva</span><span class="sxs-lookup"><span data-stu-id="990df-119">Message</span></span>|<span data-ttu-id="990df-120">Integrita, důvěrnost, ověřování serveru a ověřování klientů jsou k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="990df-120">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="990df-121">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="990df-121">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="990df-122">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="990df-122">The service must be configured with a certificate.</span></span> <span data-ttu-id="990df-123">Ověřování klientů vychází z tokenu vystaveného klientovi tokenem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="990df-123">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="990df-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="990df-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="990df-125">Integrita, důvěrnost a ověřování serveru poskytuje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="990df-125">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="990df-126">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="990df-126">The service must be configured with a certificate.</span></span> <span data-ttu-id="990df-127">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP a je založeno na tokenu vydanému klientovi pomocí služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="990df-127">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="990df-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="990df-128">Child Elements</span></span>  
  
|<span data-ttu-id="990df-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="990df-129">Element</span></span>|<span data-ttu-id="990df-130">Description</span><span class="sxs-lookup"><span data-stu-id="990df-130">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="990df-131">Definuje nastavení pro zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="990df-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="990df-132">Tento prvek je typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="990df-132">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="990df-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="990df-133">Parent Elements</span></span>  
  
|<span data-ttu-id="990df-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="990df-134">Element</span></span>|<span data-ttu-id="990df-135">Description</span><span class="sxs-lookup"><span data-stu-id="990df-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="990df-136">Definuje všechny schopnosti vazby pro [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="990df-136">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="990df-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="990df-137">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="990df-138">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="990df-138">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="990df-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="990df-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="990df-140">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="990df-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="990df-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="990df-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="990df-142">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="990df-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="990df-143">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="990df-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
