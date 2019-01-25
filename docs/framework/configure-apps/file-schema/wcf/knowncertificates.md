---
title: '&lt;knownCertificates&gt;'
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 49e5236abdc82fb4ca004c611e706e74fa99bf7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687346"
---
# <a name="ltknowncertificatesgt"></a><span data-ttu-id="63897-102">&lt;knownCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="63897-102">&lt;knownCertificates&gt;</span></span>
<span data-ttu-id="63897-103">Představuje kolekci certifikátů X.509, které jsou k dispozici k ověřování pověření zabezpečení vydané z tokenu služby zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="63897-103">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="63897-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="63897-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="63897-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="63897-105">\<behaviors></span></span>  
<span data-ttu-id="63897-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="63897-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="63897-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="63897-107">\<behavior></span></span>  
<span data-ttu-id="63897-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="63897-108">\<serviceCredentials></span></span>  
<span data-ttu-id="63897-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="63897-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="63897-110">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="63897-110">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63897-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63897-111">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63897-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="63897-112">Attributes and Elements</span></span>  
 <span data-ttu-id="63897-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="63897-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63897-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="63897-114">Attributes</span></span>  
 <span data-ttu-id="63897-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="63897-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="63897-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="63897-116">Child Elements</span></span>  
  
|<span data-ttu-id="63897-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="63897-117">Element</span></span>|<span data-ttu-id="63897-118">Popis</span><span class="sxs-lookup"><span data-stu-id="63897-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63897-119">\<add></span><span class="sxs-lookup"><span data-stu-id="63897-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|<span data-ttu-id="63897-120">Přidá certifikát X.509 do kolekce.</span><span class="sxs-lookup"><span data-stu-id="63897-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63897-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="63897-121">Parent Elements</span></span>  
  
|<span data-ttu-id="63897-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="63897-122">Element</span></span>|<span data-ttu-id="63897-123">Popis</span><span class="sxs-lookup"><span data-stu-id="63897-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63897-124">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="63897-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="63897-125">Určuje token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="63897-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63897-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63897-126">Remarks</span></span>  
 <span data-ttu-id="63897-127">Vydaný token scénář má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="63897-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="63897-128">V první fázi se klient pokouší o přístup ke službě označuje *služby tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="63897-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="63897-129">Služba tokenů zabezpečení pak ověří klienta a následně vydá klienta token, obvykle token zabezpečení kontrolní výrazy SAML (Markup Language).</span><span class="sxs-lookup"><span data-stu-id="63897-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="63897-130">Klient pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="63897-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="63897-131">Služba zkontroluje token pro data, která umožňuje službě ověření tokenu a proto klienta.</span><span class="sxs-lookup"><span data-stu-id="63897-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="63897-132">K ověření tokenu, certifikát používá služba tokenů zabezpečení musí být známo ke službě.</span><span class="sxs-lookup"><span data-stu-id="63897-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="63897-133">[ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element je úložiště pro tyto certifikáty služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="63897-133">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="63897-134">Chcete-li přidat certifikáty použít [ \<knownCertificates > element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="63897-134">To add certificates, use the [\<knownCertificates> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="63897-135">Vložit [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="63897-135">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="63897-136">Ve výchozím nastavení certifikáty musí pocházet od Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="63897-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="63897-137">Tyto certifikáty, ujistěte se, že, který klientům pouze bezpečných "známé" můžete přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="63897-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="63897-138">Podmínky pro klienta ověřit federované služby, jakož i další informace o použití tento prvek konfigurace najdete v tématu [jak: Konfigurace pověření ve službě Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="63897-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="63897-139">Další informace o federovaných scénářích najdete v tématu [federace a vydané tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="63897-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="63897-140">Příklad, který ukazuje, jak k naplnění kolekce v konfiguraci, najdete v části [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="63897-140">For an example that shows how to populate the collection in configuration, see [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63897-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63897-141">See also</span></span>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="63897-142">\<add></span><span class="sxs-lookup"><span data-stu-id="63897-142">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [<span data-ttu-id="63897-143">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="63897-143">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="63897-144">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="63897-144">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="63897-145">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="63897-145">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="63897-146">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="63897-146">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="63897-147">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="63897-147">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="63897-148">\<add></span><span class="sxs-lookup"><span data-stu-id="63897-148">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [<span data-ttu-id="63897-149">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="63897-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
