---
title: <add> z <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 939718e8dacca2698b6f71a3bdc1262a5dc3ee20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926684"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="dd007-102">\<Přidat > \<> knownCertificates</span><span class="sxs-lookup"><span data-stu-id="dd007-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="dd007-103">Přidá certifikát X. 509 do kolekce známých certifikátů.</span><span class="sxs-lookup"><span data-stu-id="dd007-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
 <span data-ttu-id="dd007-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dd007-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dd007-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="dd007-105">\<behaviors></span></span>  
<span data-ttu-id="dd007-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="dd007-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="dd007-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="dd007-107">\<behavior></span></span>  
<span data-ttu-id="dd007-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="dd007-108">\<serviceCredentials></span></span>  
<span data-ttu-id="dd007-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="dd007-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="dd007-110">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="dd007-110">\<knownCertificates></span></span>  
<span data-ttu-id="dd007-111">\<add></span><span class="sxs-lookup"><span data-stu-id="dd007-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd007-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd007-112">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd007-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dd007-113">Attributes and Elements</span></span>  
 <span data-ttu-id="dd007-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dd007-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd007-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="dd007-115">Attributes</span></span>  
  
|<span data-ttu-id="dd007-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="dd007-116">Attribute</span></span>|<span data-ttu-id="dd007-117">Popis</span><span class="sxs-lookup"><span data-stu-id="dd007-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd007-118">findValue</span><span class="sxs-lookup"><span data-stu-id="dd007-118">findValue</span></span>|<span data-ttu-id="dd007-119">Řetezce.</span><span class="sxs-lookup"><span data-stu-id="dd007-119">String.</span></span> <span data-ttu-id="dd007-120">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="dd007-120">The value to search for.</span></span>|  
|<span data-ttu-id="dd007-121">storeLocation</span><span class="sxs-lookup"><span data-stu-id="dd007-121">storeLocation</span></span>|<span data-ttu-id="dd007-122">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="dd007-122">Enumeration.</span></span> <span data-ttu-id="dd007-123">Jedno ze dvou umístění úložiště, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="dd007-123">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="dd007-124">storeName</span><span class="sxs-lookup"><span data-stu-id="dd007-124">storeName</span></span>|<span data-ttu-id="dd007-125">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="dd007-125">Enumeration.</span></span> <span data-ttu-id="dd007-126">Jedno ze systémových úložišť, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="dd007-126">One of the system stores to search.</span></span>|  
|<span data-ttu-id="dd007-127">x509FindType</span><span class="sxs-lookup"><span data-stu-id="dd007-127">x509FindType</span></span>|<span data-ttu-id="dd007-128">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="dd007-128">Enumeration.</span></span> <span data-ttu-id="dd007-129">Jedno z polí certifikátu, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="dd007-129">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="dd007-130">findValue – atribut</span><span class="sxs-lookup"><span data-stu-id="dd007-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="dd007-131">Value</span><span class="sxs-lookup"><span data-stu-id="dd007-131">Value</span></span>|<span data-ttu-id="dd007-132">Popis</span><span class="sxs-lookup"><span data-stu-id="dd007-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd007-133">String</span><span class="sxs-lookup"><span data-stu-id="dd007-133">String</span></span>|<span data-ttu-id="dd007-134">Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván.</span><span class="sxs-lookup"><span data-stu-id="dd007-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="dd007-135">Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.</span><span class="sxs-lookup"><span data-stu-id="dd007-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="dd007-136">x509FindType – atribut</span><span class="sxs-lookup"><span data-stu-id="dd007-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="dd007-137">Value</span><span class="sxs-lookup"><span data-stu-id="dd007-137">Value</span></span>|<span data-ttu-id="dd007-138">Popis</span><span class="sxs-lookup"><span data-stu-id="dd007-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd007-139">Výčet</span><span class="sxs-lookup"><span data-stu-id="dd007-139">Enumeration</span></span>|<span data-ttu-id="dd007-140">Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="dd007-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="dd007-141">storeLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="dd007-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="dd007-142">Value</span><span class="sxs-lookup"><span data-stu-id="dd007-142">Value</span></span>|<span data-ttu-id="dd007-143">Popis</span><span class="sxs-lookup"><span data-stu-id="dd007-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd007-144">Výčet</span><span class="sxs-lookup"><span data-stu-id="dd007-144">Enumeration</span></span>|<span data-ttu-id="dd007-145">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="dd007-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="dd007-146">storeName – atribut</span><span class="sxs-lookup"><span data-stu-id="dd007-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="dd007-147">Value</span><span class="sxs-lookup"><span data-stu-id="dd007-147">Value</span></span>|<span data-ttu-id="dd007-148">Popis</span><span class="sxs-lookup"><span data-stu-id="dd007-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd007-149">Výčet</span><span class="sxs-lookup"><span data-stu-id="dd007-149">Enumeration</span></span>|<span data-ttu-id="dd007-150">Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="dd007-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd007-151">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dd007-151">Child Elements</span></span>  
 <span data-ttu-id="dd007-152">Žádné</span><span class="sxs-lookup"><span data-stu-id="dd007-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd007-153">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dd007-153">Parent Elements</span></span>  
  
|<span data-ttu-id="dd007-154">Prvek</span><span class="sxs-lookup"><span data-stu-id="dd007-154">Element</span></span>|<span data-ttu-id="dd007-155">Popis</span><span class="sxs-lookup"><span data-stu-id="dd007-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd007-156">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="dd007-156">\<knownCertificates></span></span>](knowncertificates.md)|<span data-ttu-id="dd007-157">Představuje kolekci certifikátů X. 509, které poskytuje služba tokenů zabezpečení (STS) pro ověřování tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="dd007-157">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd007-158">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd007-158">Remarks</span></span>  
 <span data-ttu-id="dd007-159">Scénář vydaného tokenu má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="dd007-159">The issued token scenario has three stages.</span></span> <span data-ttu-id="dd007-160">V první fázi se klientovi, který se pokouší o přístup ke službě, říká *služba tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="dd007-160">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="dd007-161">Služba tokenů zabezpečení potom ověří klienta a následně vydá token klienta, obvykle token SAML (Security Assert Markup Language).</span><span class="sxs-lookup"><span data-stu-id="dd007-161">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="dd007-162">Klient se pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="dd007-162">The client then returns to the service with the token.</span></span> <span data-ttu-id="dd007-163">Služba prověřuje token pro data, která umožňují službě ověřit token, a tedy klienta.</span><span class="sxs-lookup"><span data-stu-id="dd007-163">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="dd007-164">Chcete-li ověřit token, je nutné, aby služba používala certifikát, který používá služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="dd007-164">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="dd007-165">Element [IssuedTokenAuthentication > je úložištěm těchto certifikátů služby tokenů zabezpečení. \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="dd007-165">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="dd007-166">K přidání certifikátů použijte [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="dd007-166">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="dd007-167">Pro každý certifikát vložte element [ \<Add > elementu knownCertificates >, jak je znázorněno v následujícím příkladu. \<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="dd007-167">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="dd007-168">Ve výchozím nastavení se certifikáty musí získat ze služby zabezpečeného tokenu.</span><span class="sxs-lookup"><span data-stu-id="dd007-168">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="dd007-169">Tyto "známé" certifikáty zajistí, že ke službě budou mít přístup jenom legitimní klienti.</span><span class="sxs-lookup"><span data-stu-id="dd007-169">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="dd007-170">Chcete-li zkontrolovat podmínky požadované pro ověření klienta federované službou a další informace o použití tohoto prvku konfigurace, přečtěte si téma [How to: Konfigurace přihlašovacích údajů na](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)služba FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="dd007-170">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="dd007-171">Další informace o federovaných scénářích najdete v tématu [federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="dd007-171">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd007-172">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd007-172">Example</span></span>  
 <span data-ttu-id="dd007-173">Následující příklad přidá certifikát do úložiště pro všechny certifikáty STS.</span><span class="sxs-lookup"><span data-stu-id="dd007-173">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="dd007-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd007-174">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="dd007-175">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="dd007-175">\<knownCertificates></span></span>](knowncertificates.md)
- [<span data-ttu-id="dd007-176">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="dd007-176">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="dd007-177">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="dd007-177">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="dd007-178">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="dd007-178">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="dd007-179">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="dd007-179">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
