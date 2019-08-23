---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 1210e6282a7dd6c40198693d4948a89efe841d59
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913529"
---
# <a name="knowncertificates"></a><span data-ttu-id="9d658-101">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="9d658-101">\<knownCertificates></span></span>
<span data-ttu-id="9d658-102">Představuje kolekci certifikátů X. 509, které jsou k dispozici pro ověřování bezpečnostních přihlašovacích údajů vydaných službou tokenu zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="9d658-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="9d658-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9d658-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9d658-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="9d658-104">\<behaviors></span></span>  
<span data-ttu-id="9d658-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9d658-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="9d658-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="9d658-106">\<behavior></span></span>  
<span data-ttu-id="9d658-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9d658-107">\<serviceCredentials></span></span>  
<span data-ttu-id="9d658-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="9d658-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="9d658-109">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="9d658-109">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d658-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d658-110">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d658-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9d658-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9d658-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9d658-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d658-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="9d658-113">Attributes</span></span>  
 <span data-ttu-id="9d658-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="9d658-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d658-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9d658-115">Child Elements</span></span>  
  
|<span data-ttu-id="9d658-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d658-116">Element</span></span>|<span data-ttu-id="9d658-117">Popis</span><span class="sxs-lookup"><span data-stu-id="9d658-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d658-118">\<add></span><span class="sxs-lookup"><span data-stu-id="9d658-118">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="9d658-119">Přidá do kolekce certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="9d658-119">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d658-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9d658-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9d658-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d658-121">Element</span></span>|<span data-ttu-id="9d658-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9d658-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d658-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="9d658-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="9d658-124">Určuje token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="9d658-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d658-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d658-125">Remarks</span></span>  
 <span data-ttu-id="9d658-126">Scénář vydaného tokenu má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="9d658-126">The issued token scenario has three stages.</span></span> <span data-ttu-id="9d658-127">V první fázi se klientovi, který se pokouší o přístup ke službě, říká *služba tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="9d658-127">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="9d658-128">Služba tokenů zabezpečení potom ověří klienta a následně vydá token klienta, obvykle token SAML (Security Assert Markup Language).</span><span class="sxs-lookup"><span data-stu-id="9d658-128">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="9d658-129">Klient se pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="9d658-129">The client then returns to the service with the token.</span></span> <span data-ttu-id="9d658-130">Služba prověřuje token pro data, která umožňují službě ověřit token, a tedy klienta.</span><span class="sxs-lookup"><span data-stu-id="9d658-130">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="9d658-131">Chcete-li ověřit token, je nutné, aby služba používala certifikát, který používá služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9d658-131">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="9d658-132">Element [IssuedTokenAuthentication > je úložištěm těchto certifikátů služby tokenů zabezpečení. \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="9d658-132">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="9d658-133">Chcete-li přidat certifikáty, použijte [ \<knownCertificates > element](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="9d658-133">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="9d658-134">Pro každý certifikát vložte [> Přidat,jakjeznázorněnovnásledujícímpříkladu.\<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="9d658-134">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9d658-135">Ve výchozím nastavení se certifikáty musí získat ze služby zabezpečeného tokenu.</span><span class="sxs-lookup"><span data-stu-id="9d658-135">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="9d658-136">Tyto "známé" certifikáty zajistí, že ke službě budou mít přístup jenom legitimní klienti.</span><span class="sxs-lookup"><span data-stu-id="9d658-136">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="9d658-137">Chcete-li zkontrolovat podmínky požadované pro ověření klienta federované službou a další informace o použití tohoto prvku konfigurace, přečtěte si téma [How to: Konfigurace přihlašovacích údajů na](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)služba FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="9d658-137">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="9d658-138">Další informace o federovaných scénářích najdete v tématu [federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="9d658-138">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="9d658-139">Příklad, který ukazuje, jak naplnit kolekci v konfiguraci, najdete v tématu [ \<Add >](add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="9d658-139">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d658-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d658-140">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="9d658-141">\<add></span><span class="sxs-lookup"><span data-stu-id="9d658-141">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="9d658-142">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="9d658-142">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="9d658-143">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9d658-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="9d658-144">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="9d658-144">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="9d658-145">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="9d658-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9d658-146">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="9d658-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9d658-147">\<add></span><span class="sxs-lookup"><span data-stu-id="9d658-147">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="9d658-148">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="9d658-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
