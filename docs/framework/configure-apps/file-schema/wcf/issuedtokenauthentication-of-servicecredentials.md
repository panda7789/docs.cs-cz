---
title: <issuedTokenAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400360"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="cb13b-102">\<issuedTokenAuthentication> z \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="cb13b-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="cb13b-103">Určuje vlastní token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="cb13b-103">Specifies a custom token issued as a service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="cb13b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb13b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb13b-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cb13b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cb13b-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cb13b-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb13b-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="cb13b-107">Attributes</span></span>  
  
|<span data-ttu-id="cb13b-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="cb13b-108">Attribute</span></span>|<span data-ttu-id="cb13b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cb13b-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="cb13b-110">Získá sadu cílových identifikátorů URI, pro které <xref:System.IdentityModel.Tokens.SamlSecurityToken> může být token zabezpečení cílen, aby mohl být považován za platný v <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instanci.</span><span class="sxs-lookup"><span data-stu-id="cb13b-110">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="cb13b-111">Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A> .</span><span class="sxs-lookup"><span data-stu-id="cb13b-111">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="cb13b-112">Logická hodnota určující, zda jsou povoleny nedůvěryhodné vystavitele certifikátů RSA.</span><span class="sxs-lookup"><span data-stu-id="cb13b-112">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="cb13b-113">Certifikáty jsou podepsané certifikačními autoritami (CAs) k ověření pravosti.</span><span class="sxs-lookup"><span data-stu-id="cb13b-113">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="cb13b-114">Nedůvěryhodný Vydavatel je certifikační autorita, která nemá být důvěryhodná pro podepisování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="cb13b-114">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="cb13b-115">Načte hodnotu, která určuje, jestli se <xref:System.IdentityModel.Tokens.SamlSecurityToken> <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> má ověřit token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cb13b-115">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="cb13b-116">Tato hodnota je typu <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="cb13b-116">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="cb13b-117">Další informace o použití tohoto atributu naleznete v tématu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A> .</span><span class="sxs-lookup"><span data-stu-id="cb13b-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="cb13b-118">Nastaví režim ověřování certifikátu.</span><span class="sxs-lookup"><span data-stu-id="cb13b-118">Sets the certificate validation mode.</span></span> <span data-ttu-id="cb13b-119">Jedna z platných hodnot <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="cb13b-119">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="cb13b-120">Je-li nastaveno na hodnotu `Custom` , `customCertificateValidator` musí být zadána také.</span><span class="sxs-lookup"><span data-stu-id="cb13b-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="cb13b-121">Výchozí formát je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="cb13b-121">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="cb13b-122">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="cb13b-122">Optional string.</span></span> <span data-ttu-id="cb13b-123">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="cb13b-123">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="cb13b-124">Tento atribut musí být nastaven `certificateValidationMode` , je-li nastavena na hodnotu `Custom` .</span><span class="sxs-lookup"><span data-stu-id="cb13b-124">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="cb13b-125">Nastaví režim odvolání určující, zda dojde k provedení kontroly odvolání a zda je proveden online nebo offline.</span><span class="sxs-lookup"><span data-stu-id="cb13b-125">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="cb13b-126">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="cb13b-126">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="cb13b-127">Volitelný atribut řetězce, který určuje typ SamlSerializer, který se používá pro pověření služby.</span><span class="sxs-lookup"><span data-stu-id="cb13b-127">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="cb13b-128">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="cb13b-128">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="cb13b-129">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="cb13b-129">Optional enumeration.</span></span> <span data-ttu-id="cb13b-130">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="cb13b-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb13b-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cb13b-131">Child Elements</span></span>  
  
|<span data-ttu-id="cb13b-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="cb13b-132">Element</span></span>|<span data-ttu-id="cb13b-133">Description</span><span class="sxs-lookup"><span data-stu-id="cb13b-133">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="cb13b-134">Určuje kolekci <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> prvků, které určují důvěryhodné vystavitele pro pověření služby.</span><span class="sxs-lookup"><span data-stu-id="cb13b-134">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb13b-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cb13b-135">Parent Elements</span></span>  
  
|<span data-ttu-id="cb13b-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="cb13b-136">Element</span></span>|<span data-ttu-id="cb13b-137">Description</span><span class="sxs-lookup"><span data-stu-id="cb13b-137">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="cb13b-138">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="cb13b-138">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb13b-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb13b-139">Remarks</span></span>  
 <span data-ttu-id="cb13b-140">Scénář vydaného tokenu má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="cb13b-140">The issued token scenario has three stages.</span></span> <span data-ttu-id="cb13b-141">V první fázi se klientovi, který se pokouší o přístup ke službě, říká *služba tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="cb13b-141">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="cb13b-142">Služba tokenů zabezpečení potom ověří klienta a následně vydá token klienta, obvykle token SAML (Security Assert Markup Language).</span><span class="sxs-lookup"><span data-stu-id="cb13b-142">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="cb13b-143">Klient se pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="cb13b-143">The client then returns to the service with the token.</span></span> <span data-ttu-id="cb13b-144">Služba prověřuje token pro data, která umožňují službě ověřit token, a tedy klienta.</span><span class="sxs-lookup"><span data-stu-id="cb13b-144">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="cb13b-145">Chcete-li ověřit token, je nutné, aby služba používala certifikát, který používá služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cb13b-145">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="cb13b-146">Tento prvek je úložištěm těchto certifikátů služby tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cb13b-146">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="cb13b-147">Chcete-li přidat certifikáty, použijte [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="cb13b-147">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="cb13b-148">Vložte [\<add>](add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cb13b-148">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="cb13b-149">Ve výchozím nastavení se certifikáty musí získat ze služby zabezpečeného tokenu.</span><span class="sxs-lookup"><span data-stu-id="cb13b-149">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="cb13b-150">Tyto "známé" certifikáty zajistí, že ke službě budou mít přístup jenom legitimní klienti.</span><span class="sxs-lookup"><span data-stu-id="cb13b-150">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="cb13b-151">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [How to: Configure a Credentials on a služba FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="cb13b-151">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb13b-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb13b-152">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="cb13b-153">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="cb13b-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cb13b-154">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="cb13b-154">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
