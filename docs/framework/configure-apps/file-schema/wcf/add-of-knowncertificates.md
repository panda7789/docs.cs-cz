---
title: <add> z <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400613"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="71c82-102">\<add> z \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="71c82-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="71c82-103">Přidá certifikát X. 509 do kolekce známých certifikátů.</span><span class="sxs-lookup"><span data-stu-id="71c82-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="71c82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71c82-104">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71c82-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="71c82-105">Attributes and Elements</span></span>  
 <span data-ttu-id="71c82-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="71c82-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71c82-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="71c82-107">Attributes</span></span>  
  
|<span data-ttu-id="71c82-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="71c82-108">Attribute</span></span>|<span data-ttu-id="71c82-109">Popis</span><span class="sxs-lookup"><span data-stu-id="71c82-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71c82-110">findValue</span><span class="sxs-lookup"><span data-stu-id="71c82-110">findValue</span></span>|<span data-ttu-id="71c82-111">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="71c82-111">String.</span></span> <span data-ttu-id="71c82-112">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="71c82-112">The value to search for.</span></span>|  
|<span data-ttu-id="71c82-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="71c82-113">storeLocation</span></span>|<span data-ttu-id="71c82-114">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="71c82-114">Enumeration.</span></span> <span data-ttu-id="71c82-115">Jedno ze dvou umístění úložiště, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="71c82-115">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="71c82-116">storeName</span><span class="sxs-lookup"><span data-stu-id="71c82-116">storeName</span></span>|<span data-ttu-id="71c82-117">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="71c82-117">Enumeration.</span></span> <span data-ttu-id="71c82-118">Jedno ze systémových úložišť, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="71c82-118">One of the system stores to search.</span></span>|  
|<span data-ttu-id="71c82-119">x509FindType</span><span class="sxs-lookup"><span data-stu-id="71c82-119">x509FindType</span></span>|<span data-ttu-id="71c82-120">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="71c82-120">Enumeration.</span></span> <span data-ttu-id="71c82-121">Jedno z polí certifikátu, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="71c82-121">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="71c82-122">findValue – atribut</span><span class="sxs-lookup"><span data-stu-id="71c82-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="71c82-123">Hodnota</span><span class="sxs-lookup"><span data-stu-id="71c82-123">Value</span></span>|<span data-ttu-id="71c82-124">Description</span><span class="sxs-lookup"><span data-stu-id="71c82-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71c82-125">Řetězec</span><span class="sxs-lookup"><span data-stu-id="71c82-125">String</span></span>|<span data-ttu-id="71c82-126">Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván.</span><span class="sxs-lookup"><span data-stu-id="71c82-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="71c82-127">Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.</span><span class="sxs-lookup"><span data-stu-id="71c82-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="71c82-128">x509FindType – atribut</span><span class="sxs-lookup"><span data-stu-id="71c82-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="71c82-129">Hodnota</span><span class="sxs-lookup"><span data-stu-id="71c82-129">Value</span></span>|<span data-ttu-id="71c82-130">Description</span><span class="sxs-lookup"><span data-stu-id="71c82-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71c82-131">Výčet</span><span class="sxs-lookup"><span data-stu-id="71c82-131">Enumeration</span></span>|<span data-ttu-id="71c82-132">Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="71c82-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="71c82-133">storeLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="71c82-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="71c82-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="71c82-134">Value</span></span>|<span data-ttu-id="71c82-135">Description</span><span class="sxs-lookup"><span data-stu-id="71c82-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71c82-136">Výčet</span><span class="sxs-lookup"><span data-stu-id="71c82-136">Enumeration</span></span>|<span data-ttu-id="71c82-137">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="71c82-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="71c82-138">storeName – atribut</span><span class="sxs-lookup"><span data-stu-id="71c82-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="71c82-139">Hodnota</span><span class="sxs-lookup"><span data-stu-id="71c82-139">Value</span></span>|<span data-ttu-id="71c82-140">Description</span><span class="sxs-lookup"><span data-stu-id="71c82-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71c82-141">Výčet</span><span class="sxs-lookup"><span data-stu-id="71c82-141">Enumeration</span></span>|<span data-ttu-id="71c82-142">Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="71c82-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71c82-143">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="71c82-143">Child Elements</span></span>  
 <span data-ttu-id="71c82-144">Žádné</span><span class="sxs-lookup"><span data-stu-id="71c82-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71c82-145">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="71c82-145">Parent Elements</span></span>  
  
|<span data-ttu-id="71c82-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="71c82-146">Element</span></span>|<span data-ttu-id="71c82-147">Description</span><span class="sxs-lookup"><span data-stu-id="71c82-147">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="71c82-148">Představuje kolekci certifikátů X. 509, které poskytuje služba tokenů zabezpečení (STS) pro ověřování tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="71c82-148">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71c82-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71c82-149">Remarks</span></span>  
 <span data-ttu-id="71c82-150">Scénář vydaného tokenu má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="71c82-150">The issued token scenario has three stages.</span></span> <span data-ttu-id="71c82-151">V první fázi se klientovi, který se pokouší o přístup ke službě, říká *služba tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="71c82-151">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="71c82-152">Služba tokenů zabezpečení potom ověří klienta a následně vydá token klienta, obvykle token SAML (Security Assert Markup Language).</span><span class="sxs-lookup"><span data-stu-id="71c82-152">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="71c82-153">Klient se pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="71c82-153">The client then returns to the service with the token.</span></span> <span data-ttu-id="71c82-154">Služba prověřuje token pro data, která umožňují službě ověřit token, a tedy klienta.</span><span class="sxs-lookup"><span data-stu-id="71c82-154">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="71c82-155">Chcete-li ověřit token, je nutné, aby služba používala certifikát, který používá služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="71c82-155">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="71c82-156">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)Element je úložištěm těchto certifikátů služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="71c82-156">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="71c82-157">Chcete-li přidat certifikáty, použijte [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="71c82-157">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="71c82-158">Vložte [ \<add> \<knownCertificates> element](add-of-knowncertificates.md) elementu pro každý certifikát, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="71c82-158">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="71c82-159">Ve výchozím nastavení se certifikáty musí získat ze služby zabezpečeného tokenu.</span><span class="sxs-lookup"><span data-stu-id="71c82-159">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="71c82-160">Tyto "známé" certifikáty zajistí, že ke službě budou mít přístup jenom legitimní klienti.</span><span class="sxs-lookup"><span data-stu-id="71c82-160">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="71c82-161">Chcete-li zkontrolovat podmínky požadované pro ověření klienta federované službou a další informace o použití tohoto prvku konfigurace, přečtěte si téma [How to: Configure a Credentials on a služba FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="71c82-161">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="71c82-162">Další informace o federovaných scénářích najdete v tématu [federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="71c82-162">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71c82-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="71c82-163">Example</span></span>  
 <span data-ttu-id="71c82-164">Následující příklad přidá certifikát do úložiště pro všechny certifikáty STS.</span><span class="sxs-lookup"><span data-stu-id="71c82-164">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="71c82-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="71c82-165">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="71c82-166">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="71c82-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="71c82-167">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="71c82-167">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="71c82-168">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="71c82-168">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="71c82-169">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="71c82-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
