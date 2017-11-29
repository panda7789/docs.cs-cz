---
title: Element &lt;messageSenderAuthentication&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f73a72398d183e5b758f69edb7bc034f30ed80a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagesenderauthenticationgt-element"></a><span data-ttu-id="ec949-102">Element &lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="ec949-102">&lt;messageSenderAuthentication&gt; element</span></span>
<span data-ttu-id="ec949-103">Určuje možnosti ověřování pro odesílatelé zpráv peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="ec949-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="ec949-104">Další informace o programování peer-to-peer, najdete v části [Peer-to-Peer sítě](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="ec949-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="ec949-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ec949-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ec949-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ec949-106">\<behaviors></span></span>  
<span data-ttu-id="ec949-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ec949-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="ec949-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ec949-108">\<behavior></span></span>  
<span data-ttu-id="ec949-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="ec949-109">\<clientCredentials></span></span>  
<span data-ttu-id="ec949-110">\<sdílené ></span><span class="sxs-lookup"><span data-stu-id="ec949-110">\<peer></span></span>  
<span data-ttu-id="ec949-111">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ec949-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec949-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec949-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec949-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ec949-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ec949-114">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ec949-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec949-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="ec949-115">Attributes</span></span>  
  
|<span data-ttu-id="ec949-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="ec949-116">Attribute</span></span>|<span data-ttu-id="ec949-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ec949-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec949-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="ec949-118">customCertificateValidatorType</span></span>|<span data-ttu-id="ec949-119">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="ec949-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="ec949-120">Tento atribut musí být nastaven při `certificateValidationMode` je nastaven na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="ec949-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="ec949-121">certifcateValidationMode</span><span class="sxs-lookup"><span data-stu-id="ec949-121">certifcateValidationMode</span></span>|<span data-ttu-id="ec949-122">Určuje jeden ze tří režimů slouží k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="ec949-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="ec949-123">Pokud nastavena na `Custom`, pak `customCertificateValidator` musí být uveden také.</span><span class="sxs-lookup"><span data-stu-id="ec949-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|<span data-ttu-id="ec949-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="ec949-124">revocationMode</span></span>|<span data-ttu-id="ec949-125">Jeden z režimů používá k ověření pro seznamy odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="ec949-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|<span data-ttu-id="ec949-126">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="ec949-126">trustedStoreLocation</span></span>|<span data-ttu-id="ec949-127">Jedno z umístění úložiště dvě systému: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ec949-127">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="ec949-128">Tato hodnota se používá, když je klientovi vyjednal certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="ec949-128">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="ec949-129">Ověření se provádí před **důvěryhodné osoby** uložit do umístění zadaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="ec949-129">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="ec949-130">customCertificateValidatorType atribut</span><span class="sxs-lookup"><span data-stu-id="ec949-130">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="ec949-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ec949-131">Value</span></span>|<span data-ttu-id="ec949-132">Popis</span><span class="sxs-lookup"><span data-stu-id="ec949-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec949-133">String</span><span class="sxs-lookup"><span data-stu-id="ec949-133">String</span></span>|<span data-ttu-id="ec949-134">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ec949-134">Optional.</span></span> <span data-ttu-id="ec949-135">Určuje název typu a sestavení a další data použít k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="ec949-135">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="ec949-136">Název oboru názvů a typ se minimálně, vyžadují.</span><span class="sxs-lookup"><span data-stu-id="ec949-136">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="ec949-137">Volitelné informace zahrnují: název sestavení, číslo verze, jazykové verze a tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="ec949-137">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="ec949-138">certificateValidationMode atribut</span><span class="sxs-lookup"><span data-stu-id="ec949-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="ec949-139">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ec949-139">Value</span></span>|<span data-ttu-id="ec949-140">Popis</span><span class="sxs-lookup"><span data-stu-id="ec949-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec949-141">Výčet</span><span class="sxs-lookup"><span data-stu-id="ec949-141">Enumeration</span></span>|<span data-ttu-id="ec949-142">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ec949-142">Optional.</span></span> <span data-ttu-id="ec949-143">Jeden z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="ec949-143">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="ec949-144">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="ec949-144">The default is `ChainTrust`.</span></span> <span data-ttu-id="ec949-145">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="ec949-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="ec949-146">Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ec949-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="ec949-147">revocationMode atribut</span><span class="sxs-lookup"><span data-stu-id="ec949-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="ec949-148">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ec949-148">Value</span></span>|<span data-ttu-id="ec949-149">Popis</span><span class="sxs-lookup"><span data-stu-id="ec949-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec949-150">Výčet</span><span class="sxs-lookup"><span data-stu-id="ec949-150">Enumeration</span></span>|<span data-ttu-id="ec949-151">Jeden z následujících hodnot: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="ec949-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="ec949-152">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="ec949-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="ec949-153">Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ec949-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="ec949-154">trustedStoreLocation atribut</span><span class="sxs-lookup"><span data-stu-id="ec949-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="ec949-155">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ec949-155">Value</span></span>|<span data-ttu-id="ec949-156">Popis</span><span class="sxs-lookup"><span data-stu-id="ec949-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec949-157">Výčet</span><span class="sxs-lookup"><span data-stu-id="ec949-157">Enumeration</span></span>|<span data-ttu-id="ec949-158">Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ec949-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="ec949-159">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ec949-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="ec949-160">Pokud klientská aplikace běží pod účtem systému pak certifikát je obvykle v části `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="ec949-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="ec949-161">Pokud klientská aplikace běží pod účtem uživatele, pak tento certifikát je obvykle v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ec949-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="ec949-162">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ec949-162">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec949-163">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ec949-163">Child Elements</span></span>  
 <span data-ttu-id="ec949-164">Žádné</span><span class="sxs-lookup"><span data-stu-id="ec949-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec949-165">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ec949-165">Parent Elements</span></span>  
  
|<span data-ttu-id="ec949-166">Prvek</span><span class="sxs-lookup"><span data-stu-id="ec949-166">Element</span></span>|<span data-ttu-id="ec949-167">Popis</span><span class="sxs-lookup"><span data-stu-id="ec949-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec949-168">\<sdílené ></span><span class="sxs-lookup"><span data-stu-id="ec949-168">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="ec949-169">Určí pověření používaná pro ověřování klienta do sdílené služby.</span><span class="sxs-lookup"><span data-stu-id="ec949-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec949-170">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec949-170">Remarks</span></span>  
 <span data-ttu-id="ec949-171">Tento element musí být nakonfigurován, pokud je zvoleno ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="ec949-171">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="ec949-172">Pro výstup kanály, je každá zpráva podepsaná pomocí certifikátu poskytované [ \<certifikátu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="ec949-172">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="ec949-173">Všechny zprávy před doručí aplikaci, je zkontrolován pověřením zpráv pomocí validátor určeného `customCertificateValidatorType` atribut tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="ec949-173">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="ec949-174">Validátor můžete buď přijmout nebo odmítnout přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="ec949-174">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec949-175">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec949-175">Example</span></span>  
 <span data-ttu-id="ec949-176">Následující kód nastaví režim ověření odesílatele zprávy `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="ec949-176">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec949-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec949-177">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="ec949-178">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="ec949-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="ec949-179">Sítě peer-to-Peer</span><span class="sxs-lookup"><span data-stu-id="ec949-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="ec949-180">Ověřování zpráv rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="ec949-180">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="ec949-181">Vlastní ověřování rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="ec949-181">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="ec949-182">Zabezpečení aplikací rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="ec949-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
