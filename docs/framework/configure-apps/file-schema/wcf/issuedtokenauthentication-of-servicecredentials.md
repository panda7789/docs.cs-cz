---
title: '&lt;issuedTokenAuthentication&gt; – &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 43f03ad32345195324c9ba2a3977d294a7a2b789
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151485"
---
# <a name="ltissuedtokenauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="5dc95-102">&lt;issuedTokenAuthentication&gt; – &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="5dc95-102">&lt;issuedTokenAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="5dc95-103">Určuje vlastní token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="5dc95-103">Specifies a custom token issued as a service credential.</span></span>  
  
 <span data-ttu-id="5dc95-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5dc95-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5dc95-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5dc95-105">\<behaviors></span></span>  
<span data-ttu-id="5dc95-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5dc95-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5dc95-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5dc95-107">\<behavior></span></span>  
<span data-ttu-id="5dc95-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="5dc95-108">\<serviceCredentials></span></span>  
<span data-ttu-id="5dc95-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5dc95-109">\<issuedTokenAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dc95-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5dc95-110">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dc95-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5dc95-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5dc95-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5dc95-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dc95-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="5dc95-113">Attributes</span></span>  
  
|<span data-ttu-id="5dc95-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="5dc95-114">Attribute</span></span>|<span data-ttu-id="5dc95-115">Popis</span><span class="sxs-lookup"><span data-stu-id="5dc95-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="5dc95-116">Získá sadu cílových identifikátorů URI pro kterou <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení může služba je určená pro aby mohl být uznán platnou podle <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span><span class="sxs-lookup"><span data-stu-id="5dc95-116">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="5dc95-117">Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span><span class="sxs-lookup"><span data-stu-id="5dc95-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="5dc95-118">Logická hodnota, která určuje, jestli jsou povolená nedůvěryhodní Vystavitelé certifikátů RSA.</span><span class="sxs-lookup"><span data-stu-id="5dc95-118">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="5dc95-119">Certifikáty jsou podepsány certifikačními autoritami (CA) k ověření pravosti.</span><span class="sxs-lookup"><span data-stu-id="5dc95-119">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="5dc95-120">Nedůvěryhodné Vystavitel je certifikační Autorita, která není zadána jako důvěryhodného k podepisování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="5dc95-120">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="5dc95-121">Získá hodnotu, která určuje, zda <xref:System.IdentityModel.Tokens.SamlSecurityToken> token zabezpečení <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> by měl být ověřen.</span><span class="sxs-lookup"><span data-stu-id="5dc95-121">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="5dc95-122">Tato hodnota je typu <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="5dc95-122">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="5dc95-123">Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="5dc95-123">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="5dc95-124">Nastaví režim ověřování certifikátu.</span><span class="sxs-lookup"><span data-stu-id="5dc95-124">Sets the certificate validation mode.</span></span> <span data-ttu-id="5dc95-125">Jednu z platných hodnot z <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="5dc95-125">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="5dc95-126">Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán.</span><span class="sxs-lookup"><span data-stu-id="5dc95-126">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="5dc95-127">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="5dc95-127">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="5dc95-128">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5dc95-128">Optional string.</span></span> <span data-ttu-id="5dc95-129">Typ a sestavení používané pro ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="5dc95-129">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="5dc95-130">Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="5dc95-130">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="5dc95-131">Nastaví režim odvolání určující, zda dochází ke kontrolám odvolání a pokud se provádí online nebo offline.</span><span class="sxs-lookup"><span data-stu-id="5dc95-131">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="5dc95-132">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="5dc95-132">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="5dc95-133">Volitelný řetězec atribut, který určuje typ SamlSerializer, který se používá pro přihlašovací údaje služby.</span><span class="sxs-lookup"><span data-stu-id="5dc95-133">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="5dc95-134">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5dc95-134">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="5dc95-135">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="5dc95-135">Optional enumeration.</span></span> <span data-ttu-id="5dc95-136">Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="5dc95-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5dc95-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5dc95-137">Child Elements</span></span>  
  
|<span data-ttu-id="5dc95-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="5dc95-138">Element</span></span>|<span data-ttu-id="5dc95-139">Popis</span><span class="sxs-lookup"><span data-stu-id="5dc95-139">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="5dc95-140">Určuje kolekci <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> prvky, které určuje důvěryhodných vystavitelů pro přihlašovací údaje služby.</span><span class="sxs-lookup"><span data-stu-id="5dc95-140">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5dc95-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5dc95-141">Parent Elements</span></span>  
  
|<span data-ttu-id="5dc95-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="5dc95-142">Element</span></span>|<span data-ttu-id="5dc95-143">Popis</span><span class="sxs-lookup"><span data-stu-id="5dc95-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5dc95-144">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="5dc95-144">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="5dc95-145">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="5dc95-145">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dc95-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5dc95-146">Remarks</span></span>  
 <span data-ttu-id="5dc95-147">Vydaný token scénář má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="5dc95-147">The issued token scenario has three stages.</span></span> <span data-ttu-id="5dc95-148">V první fázi se klient pokouší o přístup ke službě označuje *služby tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="5dc95-148">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="5dc95-149">Služba tokenů zabezpečení pak ověří klienta a následně vydá klienta token, obvykle token zabezpečení kontrolní výrazy SAML (Markup Language).</span><span class="sxs-lookup"><span data-stu-id="5dc95-149">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="5dc95-150">Klient pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="5dc95-150">The client then returns to the service with the token.</span></span> <span data-ttu-id="5dc95-151">Služba zkontroluje token pro data, která umožňuje službě ověření tokenu a proto klienta.</span><span class="sxs-lookup"><span data-stu-id="5dc95-151">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="5dc95-152">K ověření tokenu, certifikát používá služba tokenů zabezpečení musí být známo ke službě.</span><span class="sxs-lookup"><span data-stu-id="5dc95-152">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="5dc95-153">Tento element má úložiště pro tyto certifikáty služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5dc95-153">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="5dc95-154">Chcete-li přidat certifikáty použít [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="5dc95-154">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="5dc95-155">Vložit [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5dc95-155">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="5dc95-156">Ve výchozím nastavení certifikáty musí pocházet od Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5dc95-156">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="5dc95-157">Tyto certifikáty, ujistěte se, že, který klientům pouze bezpečných "známé" můžete přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="5dc95-157">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="5dc95-158">Další informace o použití tento prvek konfigurace, najdete v části [jak: Konfigurace pověření ve službě Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="5dc95-158">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc95-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="5dc95-159">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
 [<span data-ttu-id="5dc95-160">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5dc95-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5dc95-161">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="5dc95-161">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
