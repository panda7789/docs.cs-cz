---
title: <issuedTokenAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400360"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="87939-102">\<issuedTokenAuthentication> of \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="87939-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="87939-103">Určuje vlastní token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="87939-103">Specifies a custom token issued as a service credential.</span></span>  
  
<span data-ttu-id="87939-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="87939-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="87939-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="87939-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="87939-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="87939-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="87939-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="87939-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="87939-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="87939-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="87939-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="87939-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="87939-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuedTokenAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="87939-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87939-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87939-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87939-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="87939-112">Attributes and Elements</span></span>  
 <span data-ttu-id="87939-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="87939-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87939-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="87939-114">Attributes</span></span>  
  
|<span data-ttu-id="87939-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="87939-115">Attribute</span></span>|<span data-ttu-id="87939-116">Popis</span><span class="sxs-lookup"><span data-stu-id="87939-116">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="87939-117">Získá sadu cílových identifikátorů URI, pro které <xref:System.IdentityModel.Tokens.SamlSecurityToken> může být token zabezpečení cílen, aby mohl být považován za platný <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> v instanci.</span><span class="sxs-lookup"><span data-stu-id="87939-117">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="87939-118">Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span><span class="sxs-lookup"><span data-stu-id="87939-118">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="87939-119">Logická hodnota určující, zda jsou povoleny nedůvěryhodné vystavitele certifikátů RSA.</span><span class="sxs-lookup"><span data-stu-id="87939-119">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="87939-120">Certifikáty jsou podepsané certifikačními autoritami (CAs) k ověření pravosti.</span><span class="sxs-lookup"><span data-stu-id="87939-120">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="87939-121">Nedůvěryhodný Vydavatel je certifikační autorita, která nemá být důvěryhodná pro podepisování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="87939-121">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="87939-122">Načte hodnotu, která určuje, jestli <xref:System.IdentityModel.Tokens.SamlSecurityToken> se <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> má ověřit token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="87939-122">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="87939-123">Tato hodnota je typu <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="87939-123">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="87939-124">Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="87939-124">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="87939-125">Nastaví režim ověřování certifikátu.</span><span class="sxs-lookup"><span data-stu-id="87939-125">Sets the certificate validation mode.</span></span> <span data-ttu-id="87939-126">Jedna z platných hodnot <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="87939-126">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="87939-127">Je-li `Custom`nastaveno na hodnotu, musí být zadána také. `customCertificateValidator`</span><span class="sxs-lookup"><span data-stu-id="87939-127">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="87939-128">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="87939-128">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="87939-129">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="87939-129">Optional string.</span></span> <span data-ttu-id="87939-130">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="87939-130">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="87939-131">Tento atribut musí být nastaven, `certificateValidationMode` je-li `Custom`nastavena na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="87939-131">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="87939-132">Nastaví režim odvolání určující, zda dojde k provedení kontroly odvolání a zda je proveden online nebo offline.</span><span class="sxs-lookup"><span data-stu-id="87939-132">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="87939-133">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="87939-133">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="87939-134">Volitelný atribut řetězce, který určuje typ SamlSerializer, který se používá pro pověření služby.</span><span class="sxs-lookup"><span data-stu-id="87939-134">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="87939-135">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="87939-135">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="87939-136">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="87939-136">Optional enumeration.</span></span> <span data-ttu-id="87939-137">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="87939-137">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87939-138">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="87939-138">Child Elements</span></span>  
  
|<span data-ttu-id="87939-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="87939-139">Element</span></span>|<span data-ttu-id="87939-140">Popis</span><span class="sxs-lookup"><span data-stu-id="87939-140">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="87939-141">Určuje kolekci <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> prvků, které určují důvěryhodné vystavitele pro pověření služby.</span><span class="sxs-lookup"><span data-stu-id="87939-141">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87939-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="87939-142">Parent Elements</span></span>  
  
|<span data-ttu-id="87939-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="87939-143">Element</span></span>|<span data-ttu-id="87939-144">Popis</span><span class="sxs-lookup"><span data-stu-id="87939-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87939-145">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="87939-145">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="87939-146">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="87939-146">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87939-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87939-147">Remarks</span></span>  
 <span data-ttu-id="87939-148">Scénář vydaného tokenu má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="87939-148">The issued token scenario has three stages.</span></span> <span data-ttu-id="87939-149">V první fázi se klientovi, který se pokouší o přístup ke službě, říká *služba tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="87939-149">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="87939-150">Služba tokenů zabezpečení potom ověří klienta a následně vydá token klienta, obvykle token SAML (Security Assert Markup Language).</span><span class="sxs-lookup"><span data-stu-id="87939-150">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="87939-151">Klient se pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="87939-151">The client then returns to the service with the token.</span></span> <span data-ttu-id="87939-152">Služba prověřuje token pro data, která umožňují službě ověřit token, a tedy klienta.</span><span class="sxs-lookup"><span data-stu-id="87939-152">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="87939-153">Chcete-li ověřit token, je nutné, aby služba používala certifikát, který používá služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="87939-153">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="87939-154">Tento prvek je úložištěm těchto certifikátů služby tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="87939-154">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="87939-155">K přidání certifikátů použijte [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="87939-155">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="87939-156">Pro každý certifikát vložte [> Přidat,jakjeznázorněnovnásledujícímpříkladu.\<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="87939-156">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="87939-157">Ve výchozím nastavení se certifikáty musí získat ze služby zabezpečeného tokenu.</span><span class="sxs-lookup"><span data-stu-id="87939-157">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="87939-158">Tyto "známé" certifikáty zajistí, že ke službě budou mít přístup jenom legitimní klienti.</span><span class="sxs-lookup"><span data-stu-id="87939-158">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="87939-159">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [How to: Konfigurace přihlašovacích údajů na](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)služba FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="87939-159">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87939-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87939-160">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="87939-161">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="87939-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="87939-162">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="87939-162">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
