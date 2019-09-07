---
title: <add> z <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400613"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="d9b33-102">\<Přidat > \<> knownCertificates</span><span class="sxs-lookup"><span data-stu-id="d9b33-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="d9b33-103">Přidá certifikát X. 509 do kolekce známých certifikátů.</span><span class="sxs-lookup"><span data-stu-id="d9b33-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
<span data-ttu-id="d9b33-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d9b33-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d9b33-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d9b33-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d9b33-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d9b33-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="d9b33-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d9b33-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="d9b33-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d9b33-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="d9b33-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="d9b33-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="d9b33-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuedTokenAuthentication >** ](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="d9b33-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="d9b33-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<knownCertificates >** ](knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="d9b33-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)</span></span>\
<span data-ttu-id="d9b33-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="d9b33-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b33-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9b33-113">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9b33-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d9b33-114">Attributes and Elements</span></span>  
 <span data-ttu-id="d9b33-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d9b33-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9b33-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="d9b33-116">Attributes</span></span>  
  
|<span data-ttu-id="d9b33-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="d9b33-117">Attribute</span></span>|<span data-ttu-id="d9b33-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d9b33-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9b33-119">findValue</span><span class="sxs-lookup"><span data-stu-id="d9b33-119">findValue</span></span>|<span data-ttu-id="d9b33-120">Řetezce.</span><span class="sxs-lookup"><span data-stu-id="d9b33-120">String.</span></span> <span data-ttu-id="d9b33-121">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d9b33-121">The value to search for.</span></span>|  
|<span data-ttu-id="d9b33-122">storeLocation</span><span class="sxs-lookup"><span data-stu-id="d9b33-122">storeLocation</span></span>|<span data-ttu-id="d9b33-123">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="d9b33-123">Enumeration.</span></span> <span data-ttu-id="d9b33-124">Jedno ze dvou umístění úložiště, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d9b33-124">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="d9b33-125">storeName</span><span class="sxs-lookup"><span data-stu-id="d9b33-125">storeName</span></span>|<span data-ttu-id="d9b33-126">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="d9b33-126">Enumeration.</span></span> <span data-ttu-id="d9b33-127">Jedno ze systémových úložišť, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d9b33-127">One of the system stores to search.</span></span>|  
|<span data-ttu-id="d9b33-128">x509FindType</span><span class="sxs-lookup"><span data-stu-id="d9b33-128">x509FindType</span></span>|<span data-ttu-id="d9b33-129">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="d9b33-129">Enumeration.</span></span> <span data-ttu-id="d9b33-130">Jedno z polí certifikátu, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d9b33-130">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="d9b33-131">findValue – atribut</span><span class="sxs-lookup"><span data-stu-id="d9b33-131">findValue Attribute</span></span>  
  
|<span data-ttu-id="d9b33-132">Value</span><span class="sxs-lookup"><span data-stu-id="d9b33-132">Value</span></span>|<span data-ttu-id="d9b33-133">Popis</span><span class="sxs-lookup"><span data-stu-id="d9b33-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d9b33-134">String</span><span class="sxs-lookup"><span data-stu-id="d9b33-134">String</span></span>|<span data-ttu-id="d9b33-135">Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván.</span><span class="sxs-lookup"><span data-stu-id="d9b33-135">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="d9b33-136">Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.</span><span class="sxs-lookup"><span data-stu-id="d9b33-136">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="d9b33-137">x509FindType – atribut</span><span class="sxs-lookup"><span data-stu-id="d9b33-137">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="d9b33-138">Value</span><span class="sxs-lookup"><span data-stu-id="d9b33-138">Value</span></span>|<span data-ttu-id="d9b33-139">Popis</span><span class="sxs-lookup"><span data-stu-id="d9b33-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d9b33-140">Výčet</span><span class="sxs-lookup"><span data-stu-id="d9b33-140">Enumeration</span></span>|<span data-ttu-id="d9b33-141">Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="d9b33-141">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="d9b33-142">storeLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="d9b33-142">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="d9b33-143">Value</span><span class="sxs-lookup"><span data-stu-id="d9b33-143">Value</span></span>|<span data-ttu-id="d9b33-144">Popis</span><span class="sxs-lookup"><span data-stu-id="d9b33-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d9b33-145">Výčet</span><span class="sxs-lookup"><span data-stu-id="d9b33-145">Enumeration</span></span>|<span data-ttu-id="d9b33-146">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="d9b33-146">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="d9b33-147">storeName – atribut</span><span class="sxs-lookup"><span data-stu-id="d9b33-147">storeName Attribute</span></span>  
  
|<span data-ttu-id="d9b33-148">Value</span><span class="sxs-lookup"><span data-stu-id="d9b33-148">Value</span></span>|<span data-ttu-id="d9b33-149">Popis</span><span class="sxs-lookup"><span data-stu-id="d9b33-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d9b33-150">Výčet</span><span class="sxs-lookup"><span data-stu-id="d9b33-150">Enumeration</span></span>|<span data-ttu-id="d9b33-151">Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="d9b33-151">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9b33-152">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d9b33-152">Child Elements</span></span>  
 <span data-ttu-id="d9b33-153">Žádné</span><span class="sxs-lookup"><span data-stu-id="d9b33-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9b33-154">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d9b33-154">Parent Elements</span></span>  
  
|<span data-ttu-id="d9b33-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="d9b33-155">Element</span></span>|<span data-ttu-id="d9b33-156">Popis</span><span class="sxs-lookup"><span data-stu-id="d9b33-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9b33-157">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="d9b33-157">\<knownCertificates></span></span>](knowncertificates.md)|<span data-ttu-id="d9b33-158">Představuje kolekci certifikátů X. 509, které poskytuje služba tokenů zabezpečení (STS) pro ověřování tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d9b33-158">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9b33-159">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9b33-159">Remarks</span></span>  
 <span data-ttu-id="d9b33-160">Scénář vydaného tokenu má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="d9b33-160">The issued token scenario has three stages.</span></span> <span data-ttu-id="d9b33-161">V první fázi se klientovi, který se pokouší o přístup ke službě, říká *služba tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="d9b33-161">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="d9b33-162">Služba tokenů zabezpečení potom ověří klienta a následně vydá token klienta, obvykle token SAML (Security Assert Markup Language).</span><span class="sxs-lookup"><span data-stu-id="d9b33-162">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="d9b33-163">Klient se pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="d9b33-163">The client then returns to the service with the token.</span></span> <span data-ttu-id="d9b33-164">Služba prověřuje token pro data, která umožňují službě ověřit token, a tedy klienta.</span><span class="sxs-lookup"><span data-stu-id="d9b33-164">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="d9b33-165">Chcete-li ověřit token, je nutné, aby služba používala certifikát, který používá služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d9b33-165">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="d9b33-166">Element [IssuedTokenAuthentication > je úložištěm těchto certifikátů služby tokenů zabezpečení. \<](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="d9b33-166">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="d9b33-167">K přidání certifikátů použijte [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="d9b33-167">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="d9b33-168">Pro každý certifikát vložte element [ \<Add > elementu knownCertificates >, jak je znázorněno v následujícím příkladu. \<](add-of-knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="d9b33-168">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="d9b33-169">Ve výchozím nastavení se certifikáty musí získat ze služby zabezpečeného tokenu.</span><span class="sxs-lookup"><span data-stu-id="d9b33-169">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="d9b33-170">Tyto "známé" certifikáty zajistí, že ke službě budou mít přístup jenom legitimní klienti.</span><span class="sxs-lookup"><span data-stu-id="d9b33-170">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="d9b33-171">Chcete-li zkontrolovat podmínky požadované pro ověření klienta federované službou a další informace o použití tohoto prvku konfigurace, přečtěte si téma [How to: Konfigurace přihlašovacích údajů na](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)služba FS (Federation Service).</span><span class="sxs-lookup"><span data-stu-id="d9b33-171">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="d9b33-172">Další informace o federovaných scénářích najdete v tématu [federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="d9b33-172">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9b33-173">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9b33-173">Example</span></span>  
 <span data-ttu-id="d9b33-174">Následující příklad přidá certifikát do úložiště pro všechny certifikáty STS.</span><span class="sxs-lookup"><span data-stu-id="d9b33-174">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d9b33-175">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9b33-175">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="d9b33-176">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="d9b33-176">\<knownCertificates></span></span>](knowncertificates.md)
- [<span data-ttu-id="d9b33-177">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="d9b33-177">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d9b33-178">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d9b33-178">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d9b33-179">Postupy: Konfigurace přihlašovacích údajů na služba FS (Federation Service)</span><span class="sxs-lookup"><span data-stu-id="d9b33-179">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="d9b33-180">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d9b33-180">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
