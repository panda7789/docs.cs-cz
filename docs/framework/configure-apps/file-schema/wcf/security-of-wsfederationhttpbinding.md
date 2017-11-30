---
title: "&lt;security&gt; – &lt;wsFederationHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: dd4f517c17efce85f7a83d7d8545cf58322d5373
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="3a211-102">&lt;security&gt; – &lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3a211-102">&lt;security&gt; of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="3a211-103">Definuje nastavení zabezpečení [ \<– wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3a211-103">Defines the security settings of the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="3a211-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3a211-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3a211-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3a211-105">\<bindings></span></span>  
<span data-ttu-id="3a211-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="3a211-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="3a211-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="3a211-107">\<binding></span></span>  
<span data-ttu-id="3a211-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="3a211-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a211-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a211-109">Syntax</span></span>  
  
```xml  
<wsFederationBinding>  
    <binding >  
       <security mode="None/Message/TransportWithMessageCredential">  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
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
                                 <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a211-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3a211-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3a211-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3a211-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a211-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3a211-112">Attributes</span></span>  
  
|<span data-ttu-id="3a211-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3a211-113">Attribute</span></span>|<span data-ttu-id="3a211-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3a211-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a211-115">Režim</span><span class="sxs-lookup"><span data-stu-id="3a211-115">Mode</span></span>|<span data-ttu-id="3a211-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3a211-116">Optional.</span></span> <span data-ttu-id="3a211-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="3a211-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="3a211-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="3a211-118">The default value is `Message`.</span></span> <span data-ttu-id="3a211-119">Tento atribut je typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3a211-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="3a211-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="3a211-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="3a211-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3a211-121">Value</span></span>|<span data-ttu-id="3a211-122">Popis</span><span class="sxs-lookup"><span data-stu-id="3a211-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3a211-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="3a211-123">None</span></span>|<span data-ttu-id="3a211-124">Zprávu SOAP není zabezpečený při přenosu.</span><span class="sxs-lookup"><span data-stu-id="3a211-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="3a211-125">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3a211-125">Message</span></span>|<span data-ttu-id="3a211-126">Integritu, důvěrnost, ověřování serveru a ověřování klientů jsou poskytovány pomocí zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="3a211-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="3a211-127">Ve výchozím nastavení je text šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="3a211-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="3a211-128">Službu je potřeba nakonfigurovat s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="3a211-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="3a211-129">Ověření klienta je založena na token do klienta vystavený služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3a211-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="3a211-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="3a211-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="3a211-131">Ověření integrity a důvěrnosti serveru jsou poskytovány HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3a211-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="3a211-132">Službu je potřeba nakonfigurovat s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="3a211-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="3a211-133">Ověření klienta je k dispozici prostřednictvím zabezpečení zpráv protokolu SOAP a je založený na token do klienta vystavený služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3a211-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a211-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3a211-134">Child Elements</span></span>  
  
|<span data-ttu-id="3a211-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="3a211-135">Element</span></span>|<span data-ttu-id="3a211-136">Popis</span><span class="sxs-lookup"><span data-stu-id="3a211-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a211-137">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="3a211-137">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="3a211-138">Definuje nastavení pro zprávy úroveň zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3a211-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="3a211-139">Tento element je typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="3a211-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a211-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3a211-140">Parent Elements</span></span>  
  
|<span data-ttu-id="3a211-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="3a211-141">Element</span></span>|<span data-ttu-id="3a211-142">Popis</span><span class="sxs-lookup"><span data-stu-id="3a211-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a211-143">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="3a211-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3a211-144">Definuje všechny možnosti vazby [ \<– wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3a211-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a211-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a211-145">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="3a211-146">Postupy: vytvoření třídy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3a211-146">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="3a211-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3a211-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3a211-148">Výběr typu pověření</span><span class="sxs-lookup"><span data-stu-id="3a211-148">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="3a211-149">Vazby</span><span class="sxs-lookup"><span data-stu-id="3a211-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3a211-150">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3a211-150">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3a211-151">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="3a211-151">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="3a211-152">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="3a211-152">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
