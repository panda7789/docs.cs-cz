---
title: <security> z <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 75e3910473a353c2ef110106c34b4e92c018b51c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196122"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="8dfb1-102">\<security> of \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8dfb1-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="8dfb1-103">Definuje nastavení zabezpečení [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8dfb1-103">Defines the security settings of the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="8dfb1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8dfb1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8dfb1-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="8dfb1-105">\<bindings></span></span>  
<span data-ttu-id="8dfb1-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="8dfb1-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="8dfb1-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8dfb1-107">\<binding></span></span>  
<span data-ttu-id="8dfb1-108">\<security></span><span class="sxs-lookup"><span data-stu-id="8dfb1-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dfb1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dfb1-109">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dfb1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8dfb1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8dfb1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dfb1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="8dfb1-112">Attributes</span></span>  
  
|<span data-ttu-id="8dfb1-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="8dfb1-113">Attribute</span></span>|<span data-ttu-id="8dfb1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8dfb1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8dfb1-115">Režim</span><span class="sxs-lookup"><span data-stu-id="8dfb1-115">Mode</span></span>|<span data-ttu-id="8dfb1-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-116">Optional.</span></span> <span data-ttu-id="8dfb1-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="8dfb1-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-118">The default value is `Message`.</span></span> <span data-ttu-id="8dfb1-119">Tento atribut je typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="8dfb1-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="8dfb1-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="8dfb1-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8dfb1-121">Value</span></span>|<span data-ttu-id="8dfb1-122">Popis</span><span class="sxs-lookup"><span data-stu-id="8dfb1-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8dfb1-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="8dfb1-123">None</span></span>|<span data-ttu-id="8dfb1-124">Zprávu protokolu SOAP není zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="8dfb1-125">Zpráva</span><span class="sxs-lookup"><span data-stu-id="8dfb1-125">Message</span></span>|<span data-ttu-id="8dfb1-126">Integrity, šifrování, ověřování serveru a klienta ověřování zajišťuje zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="8dfb1-127">Ve výchozím nastavení je tělo zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="8dfb1-128">Služba je potřeba nakonfigurovat s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="8dfb1-129">Ověření klienta je založena na token vydaný pro klienta služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8dfb1-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="8dfb1-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="8dfb1-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="8dfb1-131">Jsou k dispozici integritu a důvěrnost serveru ověřování pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="8dfb1-132">Služba je potřeba nakonfigurovat s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="8dfb1-133">Ověření klienta se poskytuje prostřednictvím zabezpečení zprávy protokolu SOAP a je založena na token vydaný pro klienta služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8dfb1-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8dfb1-134">Child Elements</span></span>  
  
|<span data-ttu-id="8dfb1-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="8dfb1-135">Element</span></span>|<span data-ttu-id="8dfb1-136">Popis</span><span class="sxs-lookup"><span data-stu-id="8dfb1-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8dfb1-137">\<message></span><span class="sxs-lookup"><span data-stu-id="8dfb1-137">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="8dfb1-138">Definuje nastavení založená na úrovni zpráv zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="8dfb1-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="8dfb1-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8dfb1-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8dfb1-140">Parent Elements</span></span>  
  
|<span data-ttu-id="8dfb1-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="8dfb1-141">Element</span></span>|<span data-ttu-id="8dfb1-142">Popis</span><span class="sxs-lookup"><span data-stu-id="8dfb1-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8dfb1-143">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8dfb1-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8dfb1-144">Definuje všechny vazby funkce [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="8dfb1-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8dfb1-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8dfb1-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="8dfb1-146">Postupy: Vytvoření instance WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="8dfb1-146">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="8dfb1-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8dfb1-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8dfb1-148">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="8dfb1-148">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="8dfb1-149">Vazby</span><span class="sxs-lookup"><span data-stu-id="8dfb1-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8dfb1-150">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="8dfb1-150">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8dfb1-151">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8dfb1-151">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8dfb1-152">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8dfb1-152">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
