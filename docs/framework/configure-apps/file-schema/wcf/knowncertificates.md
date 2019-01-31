---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 4c1dc15621138aa692f0a30d285f729c2bd670d3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274112"
---
# <a name="knowncertificates"></a><span data-ttu-id="492dd-101">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="492dd-101">\<knownCertificates></span></span>
<span data-ttu-id="492dd-102">Představuje kolekci certifikátů X.509, které jsou k dispozici k ověřování pověření zabezpečení vydané z tokenu služby zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="492dd-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="492dd-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="492dd-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="492dd-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="492dd-104">\<behaviors></span></span>  
<span data-ttu-id="492dd-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="492dd-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="492dd-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="492dd-106">\<behavior></span></span>  
<span data-ttu-id="492dd-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="492dd-107">\<serviceCredentials></span></span>  
<span data-ttu-id="492dd-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="492dd-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="492dd-109">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="492dd-109">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="492dd-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="492dd-110">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="492dd-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="492dd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="492dd-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="492dd-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="492dd-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="492dd-113">Attributes</span></span>  
 <span data-ttu-id="492dd-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="492dd-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="492dd-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="492dd-115">Child Elements</span></span>  
  
|<span data-ttu-id="492dd-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="492dd-116">Element</span></span>|<span data-ttu-id="492dd-117">Popis</span><span class="sxs-lookup"><span data-stu-id="492dd-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="492dd-118">\<add></span><span class="sxs-lookup"><span data-stu-id="492dd-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|<span data-ttu-id="492dd-119">Přidá certifikát X.509 do kolekce.</span><span class="sxs-lookup"><span data-stu-id="492dd-119">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="492dd-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="492dd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="492dd-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="492dd-121">Element</span></span>|<span data-ttu-id="492dd-122">Popis</span><span class="sxs-lookup"><span data-stu-id="492dd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="492dd-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="492dd-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="492dd-124">Určuje token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="492dd-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="492dd-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="492dd-125">Remarks</span></span>  
 <span data-ttu-id="492dd-126">Vydaný token scénář má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="492dd-126">The issued token scenario has three stages.</span></span> <span data-ttu-id="492dd-127">V první fázi se klient pokouší o přístup ke službě označuje *služby tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="492dd-127">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="492dd-128">Služba tokenů zabezpečení pak ověří klienta a následně vydá klienta token, obvykle token zabezpečení kontrolní výrazy SAML (Markup Language).</span><span class="sxs-lookup"><span data-stu-id="492dd-128">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="492dd-129">Klient pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="492dd-129">The client then returns to the service with the token.</span></span> <span data-ttu-id="492dd-130">Služba zkontroluje token pro data, která umožňuje službě ověření tokenu a proto klienta.</span><span class="sxs-lookup"><span data-stu-id="492dd-130">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="492dd-131">K ověření tokenu, certifikát používá služba tokenů zabezpečení musí být známo ke službě.</span><span class="sxs-lookup"><span data-stu-id="492dd-131">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="492dd-132">[ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element je úložiště pro tyto certifikáty služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="492dd-132">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="492dd-133">Chcete-li přidat certifikáty použít [ \<knownCertificates > element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="492dd-133">To add certificates, use the [\<knownCertificates> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="492dd-134">Vložit [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="492dd-134">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="492dd-135">Ve výchozím nastavení certifikáty musí pocházet od Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="492dd-135">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="492dd-136">Tyto certifikáty, ujistěte se, že, který klientům pouze bezpečných "známé" můžete přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="492dd-136">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="492dd-137">Podmínky pro klienta ověřit federované služby, jakož i další informace o použití tento prvek konfigurace najdete v tématu [jak: Konfigurace pověření ve službě Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="492dd-137">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="492dd-138">Další informace o federovaných scénářích najdete v tématu [federace a vydané tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="492dd-138">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="492dd-139">Příklad, který ukazuje, jak k naplnění kolekce v konfiguraci, najdete v části [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="492dd-139">For an example that shows how to populate the collection in configuration, see [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="492dd-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="492dd-140">See also</span></span>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="492dd-141">\<add></span><span class="sxs-lookup"><span data-stu-id="492dd-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [<span data-ttu-id="492dd-142">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="492dd-142">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="492dd-143">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="492dd-143">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="492dd-144">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="492dd-144">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="492dd-145">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="492dd-145">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="492dd-146">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="492dd-146">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="492dd-147">\<add></span><span class="sxs-lookup"><span data-stu-id="492dd-147">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [<span data-ttu-id="492dd-148">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="492dd-148">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
