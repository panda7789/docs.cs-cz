---
title: <issuedTokenAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 280aa49019f68a0906307e24842a585a92c6600a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925371"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="8977a-102">\<issuedTokenAuthentication> of \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="8977a-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="8977a-103">Určuje vlastní token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="8977a-103">Specifies a custom token issued as a service credential.</span></span>  
  
 <span data-ttu-id="8977a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8977a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8977a-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="8977a-105">\<behaviors></span></span>  
<span data-ttu-id="8977a-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8977a-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8977a-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="8977a-107">\<behavior></span></span>  
<span data-ttu-id="8977a-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="8977a-108">\<serviceCredentials></span></span>  
<span data-ttu-id="8977a-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="8977a-109">\<issuedTokenAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8977a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8977a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8977a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8977a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8977a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8977a-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8977a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="8977a-113">Attributes</span></span>  
  
|<span data-ttu-id="8977a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="8977a-114">Attribute</span></span>|<span data-ttu-id="8977a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="8977a-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="8977a-116">Získá sadu cílových identifikátorů URI, pro které <xref:System.IdentityModel.Tokens.SamlSecurityToken> může být token zabezpečení cílen, aby mohl být považován za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="8977a-116">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="8977a-117">Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span><span class="sxs-lookup"><span data-stu-id="8977a-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="8977a-118">Logická hodnota určující, zda jsou povoleny nedůvěryhodné vystavitele certifikátů RSA.</span><span class="sxs-lookup"><span data-stu-id="8977a-118">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="8977a-119">Certifikáty jsou podepsané certifikačními autoritami (CAs) k ověření pravosti.</span><span class="sxs-lookup"><span data-stu-id="8977a-119">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="8977a-120">Nedůvěryhodný Vydavatel je certifikační autorita, která nemá být důvěryhodná pro podepisování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8977a-120">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="8977a-121">Načte hodnotu, která určuje, jestli <xref:System.IdentityModel.Tokens.SamlSecurityToken> se <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> má ověřit token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8977a-121">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="8977a-122">Tato hodnota je typu <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="8977a-122">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="8977a-123">Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="8977a-123">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="8977a-124">Nastaví režim ověřování certifikátu.</span><span class="sxs-lookup"><span data-stu-id="8977a-124">Sets the certificate validation mode.</span></span> <span data-ttu-id="8977a-125">Jedna z platných hodnot <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="8977a-125">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="8977a-126">Je-li `Custom`nastaveno na hodnotu, musí být zadána také. `customCertificateValidator`</span><span class="sxs-lookup"><span data-stu-id="8977a-126">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="8977a-127">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="8977a-127">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="8977a-128">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8977a-128">Optional string.</span></span> <span data-ttu-id="8977a-129">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="8977a-129">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="8977a-130">Tento atribut musí být nastaven, `certificateValidationMode` je-li `Custom`nastavena na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8977a-130">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="8977a-131">Nastaví režim odvolání určující, zda dojde k provedení kontroly odvolání a zda je proveden online nebo offline.</span><span class="sxs-lookup"><span data-stu-id="8977a-131">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="8977a-132">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="8977a-132">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="8977a-133">Volitelný atribut řetězce, který určuje typ SamlSerializer, který se používá pro pověření služby.</span><span class="sxs-lookup"><span data-stu-id="8977a-133">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="8977a-134">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8977a-134">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="8977a-135">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="8977a-135">Optional enumeration.</span></span> <span data-ttu-id="8977a-136">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="8977a-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8977a-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8977a-137">Child Elements</span></span>  
  
|<span data-ttu-id="8977a-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="8977a-138">Element</span></span>|<span data-ttu-id="8977a-139">Popis</span><span class="sxs-lookup"><span data-stu-id="8977a-139">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="8977a-140">Určuje kolekci <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> prvků, které určují důvěryhodné vystavitele pro pověření služby.</span><span class="sxs-lookup"><span data-stu-id="8977a-140">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8977a-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8977a-141">Parent Elements</span></span>  
  
|<span data-ttu-id="8977a-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="8977a-142">Element</span></span>|<span data-ttu-id="8977a-143">Popis</span><span class="sxs-lookup"><span data-stu-id="8977a-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8977a-144">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="8977a-144">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="8977a-145">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="8977a-145">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8977a-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8977a-146">Remarks</span></span>  
 <span data-ttu-id="8977a-147">Scénář vydaného tokenu má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="8977a-147">The issued token scenario has three stages.</span></span> <span data-ttu-id="8977a-148">V první fázi se klientovi, který se pokouší o přístup ke službě, říká *služba tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="8977a-148">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="8977a-149">Služba tokenů zabezpečení potom ověří klienta a následně vydá token klienta, obvykle token SAML (Security Assert Markup Language).</span><span class="sxs-lookup"><span data-stu-id="8977a-149">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="8977a-150">Klient se pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="8977a-150">The client then returns to the service with the token.</span></span> <span data-ttu-id="8977a-151">Služba prověřuje token pro data, která umožňují službě ověřit token, a tedy klienta.</span><span class="sxs-lookup"><span data-stu-id="8977a-151">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="8977a-152">Chcete-li ověřit token, je nutné, aby služba používala certifikát, který používá služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8977a-152">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="8977a-153">Tento prvek je úložištěm těchto certifikátů služby tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8977a-153">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="8977a-154">K přidání certifikátů použijte [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="8977a-154">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="8977a-155">Pro každý certifikát vložte [> Přidat,jakjeznázorněnovnásledujícímpříkladu.\<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="8977a-155">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="8977a-156">Ve výchozím nastavení se certifikáty musí získat ze služby zabezpečeného tokenu.</span><span class="sxs-lookup"><span data-stu-id="8977a-156">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="8977a-157">Tyto "známé" certifikáty zajistí, že ke službě budou mít přístup jenom legitimní klienti.</span><span class="sxs-lookup"><span data-stu-id="8977a-157">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="8977a-158">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [How to: Konfigurace přihlašovacích údajů na](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)služba FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="8977a-158">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8977a-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8977a-159">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="8977a-160">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8977a-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8977a-161">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="8977a-161">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
