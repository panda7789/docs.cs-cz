---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 23fe19258e09e9e8a5e05a94ccef0e40ee1cb5fd
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400326"
---
# <a name="knowncertificates"></a><span data-ttu-id="5143d-101">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="5143d-101">\<knownCertificates></span></span>
<span data-ttu-id="5143d-102">Představuje kolekci certifikátů X. 509, které jsou k dispozici pro ověřování bezpečnostních přihlašovacích údajů vydaných službou tokenu zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="5143d-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
<span data-ttu-id="5143d-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5143d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5143d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5143d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5143d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5143d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5143d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5143d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="5143d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5143d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="5143d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5143d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="5143d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5143d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="5143d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<knownCertificates >**</span><span class="sxs-lookup"><span data-stu-id="5143d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5143d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5143d-111">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5143d-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5143d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5143d-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5143d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5143d-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="5143d-114">Attributes</span></span>  
 <span data-ttu-id="5143d-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="5143d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5143d-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5143d-116">Child Elements</span></span>  
  
|<span data-ttu-id="5143d-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="5143d-117">Element</span></span>|<span data-ttu-id="5143d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="5143d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5143d-119">\<add></span><span class="sxs-lookup"><span data-stu-id="5143d-119">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="5143d-120">Přidá do kolekce certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="5143d-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5143d-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5143d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5143d-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="5143d-122">Element</span></span>|<span data-ttu-id="5143d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="5143d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5143d-124">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="5143d-124">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="5143d-125">Určuje token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="5143d-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5143d-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5143d-126">Remarks</span></span>  
 <span data-ttu-id="5143d-127">Scénář vydaného tokenu má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="5143d-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="5143d-128">V první fázi se klientovi, který se pokouší o přístup ke službě, říká *služba tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="5143d-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="5143d-129">Služba tokenů zabezpečení potom ověří klienta a následně vydá token klienta, obvykle token SAML (Security Assert Markup Language).</span><span class="sxs-lookup"><span data-stu-id="5143d-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="5143d-130">Klient se pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="5143d-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="5143d-131">Služba prověřuje token pro data, která umožňují službě ověřit token, a tedy klienta.</span><span class="sxs-lookup"><span data-stu-id="5143d-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="5143d-132">Chcete-li ověřit token, je nutné, aby služba používala certifikát, který používá služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5143d-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="5143d-133">Element [IssuedTokenAuthentication > je úložištěm těchto certifikátů služby tokenů zabezpečení. \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5143d-133">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="5143d-134">Chcete-li přidat certifikáty, použijte [ \<knownCertificates > element](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="5143d-134">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="5143d-135">Pro každý certifikát vložte [> Přidat,jakjeznázorněnovnásledujícímpříkladu.\<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="5143d-135">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="5143d-136">Ve výchozím nastavení se certifikáty musí získat ze služby zabezpečeného tokenu.</span><span class="sxs-lookup"><span data-stu-id="5143d-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="5143d-137">Tyto "známé" certifikáty zajistí, že ke službě budou mít přístup jenom legitimní klienti.</span><span class="sxs-lookup"><span data-stu-id="5143d-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="5143d-138">Chcete-li zkontrolovat podmínky požadované pro ověření klienta federované službou a další informace o použití tohoto prvku konfigurace, přečtěte si téma [How to: Konfigurace přihlašovacích údajů na](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)služba FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="5143d-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="5143d-139">Další informace o federovaných scénářích najdete v tématu [federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="5143d-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="5143d-140">Příklad, který ukazuje, jak naplnit kolekci v konfiguraci, najdete v tématu [ \<Add >](add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="5143d-140">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5143d-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5143d-141">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="5143d-142">\<add></span><span class="sxs-lookup"><span data-stu-id="5143d-142">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="5143d-143">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="5143d-143">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="5143d-144">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5143d-144">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5143d-145">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="5143d-145">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="5143d-146">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="5143d-146">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="5143d-147">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="5143d-147">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5143d-148">\<add></span><span class="sxs-lookup"><span data-stu-id="5143d-148">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="5143d-149">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5143d-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
