---
title: <defaultCertificate> Prvek
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: c94531d10b7c0ef5ca0ee1f2d5683d0a259a2537
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100597"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="63a57-102">\<defaultCertificate > – Element</span><span class="sxs-lookup"><span data-stu-id="63a57-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="63a57-103">Určuje certifikát X.509, který se má použít při služba nebo STS neposkytne pomocí protokolu vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="63a57-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="63a57-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="63a57-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="63a57-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="63a57-105">\<behaviors></span></span>  
<span data-ttu-id="63a57-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="63a57-106">endpointBehaviors section</span></span>  
<span data-ttu-id="63a57-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="63a57-107">\<behavior></span></span>  
<span data-ttu-id="63a57-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="63a57-108">\<clientCredentials></span></span>  
<span data-ttu-id="63a57-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="63a57-109">\<serviceCertificate></span></span>  
<span data-ttu-id="63a57-110">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="63a57-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63a57-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63a57-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63a57-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="63a57-112">Attributes and Elements</span></span>  
 <span data-ttu-id="63a57-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="63a57-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63a57-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="63a57-114">Attributes</span></span>  
  
|<span data-ttu-id="63a57-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="63a57-115">Attribute</span></span>|<span data-ttu-id="63a57-116">Popis</span><span class="sxs-lookup"><span data-stu-id="63a57-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63a57-117">findValue</span><span class="sxs-lookup"><span data-stu-id="63a57-117">findValue</span></span>|<span data-ttu-id="63a57-118">řetězec.</span><span class="sxs-lookup"><span data-stu-id="63a57-118">String.</span></span> <span data-ttu-id="63a57-119">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="63a57-119">The value to search for.</span></span>|  
|<span data-ttu-id="63a57-120">x509FindType</span><span class="sxs-lookup"><span data-stu-id="63a57-120">x509FindType</span></span>|<span data-ttu-id="63a57-121">Výčet.</span><span class="sxs-lookup"><span data-stu-id="63a57-121">Enumeration.</span></span> <span data-ttu-id="63a57-122">Jeden z pole certifikátu k prohledání.</span><span class="sxs-lookup"><span data-stu-id="63a57-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="63a57-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="63a57-123">storeLocation</span></span>|<span data-ttu-id="63a57-124">Výčet.</span><span class="sxs-lookup"><span data-stu-id="63a57-124">Enumeration.</span></span> <span data-ttu-id="63a57-125">Jedno ze dvou systémových úložišť k prohledání.</span><span class="sxs-lookup"><span data-stu-id="63a57-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="63a57-126">storeName</span><span class="sxs-lookup"><span data-stu-id="63a57-126">storeName</span></span>|<span data-ttu-id="63a57-127">Výčet.</span><span class="sxs-lookup"><span data-stu-id="63a57-127">Enumeration.</span></span> <span data-ttu-id="63a57-128">Jedno ze systémových úložišť k prohledání.</span><span class="sxs-lookup"><span data-stu-id="63a57-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="63a57-129">findValue atribut</span><span class="sxs-lookup"><span data-stu-id="63a57-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="63a57-130">Value</span><span class="sxs-lookup"><span data-stu-id="63a57-130">Value</span></span>|<span data-ttu-id="63a57-131">Popis</span><span class="sxs-lookup"><span data-stu-id="63a57-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63a57-132">String</span><span class="sxs-lookup"><span data-stu-id="63a57-132">String</span></span>|<span data-ttu-id="63a57-133">Hodnota závisí na poli (určenému atributem X509FindType) být vyhledán.</span><span class="sxs-lookup"><span data-stu-id="63a57-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="63a57-134">Například pokud hledání kryptografickým otiskem, hodnota musí být řetězec šestnáctkových čísel.</span><span class="sxs-lookup"><span data-stu-id="63a57-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="63a57-135">Atribut x509FindType</span><span class="sxs-lookup"><span data-stu-id="63a57-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="63a57-136">Value</span><span class="sxs-lookup"><span data-stu-id="63a57-136">Value</span></span>|<span data-ttu-id="63a57-137">Popis</span><span class="sxs-lookup"><span data-stu-id="63a57-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63a57-138">Výčet</span><span class="sxs-lookup"><span data-stu-id="63a57-138">Enumeration</span></span>|<span data-ttu-id="63a57-139">Mezi hodnoty patří: FindByThumbprint FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="63a57-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="63a57-140">storeLocation atribut</span><span class="sxs-lookup"><span data-stu-id="63a57-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="63a57-141">Value</span><span class="sxs-lookup"><span data-stu-id="63a57-141">Value</span></span>|<span data-ttu-id="63a57-142">Popis</span><span class="sxs-lookup"><span data-stu-id="63a57-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63a57-143">Výčet</span><span class="sxs-lookup"><span data-stu-id="63a57-143">Enumeration</span></span>|<span data-ttu-id="63a57-144">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="63a57-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="63a57-145">storeName atribut</span><span class="sxs-lookup"><span data-stu-id="63a57-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="63a57-146">Value</span><span class="sxs-lookup"><span data-stu-id="63a57-146">Value</span></span>|<span data-ttu-id="63a57-147">Popis</span><span class="sxs-lookup"><span data-stu-id="63a57-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63a57-148">Výčet</span><span class="sxs-lookup"><span data-stu-id="63a57-148">Enumeration</span></span>|<span data-ttu-id="63a57-149">Mezi hodnoty patří: Adresáře, AuthRoot, CertificateAuthority zakázané, My, Root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="63a57-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63a57-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="63a57-150">Child Elements</span></span>  
 <span data-ttu-id="63a57-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="63a57-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63a57-152">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="63a57-152">Parent Elements</span></span>  
  
|<span data-ttu-id="63a57-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="63a57-153">Element</span></span>|<span data-ttu-id="63a57-154">Popis</span><span class="sxs-lookup"><span data-stu-id="63a57-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63a57-155">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="63a57-155">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="63a57-156">Určuje certifikát používaný při ověřování služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="63a57-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63a57-157">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63a57-157">Remarks</span></span>  
 <span data-ttu-id="63a57-158">U vazeb, které používají zabezpečení na základě certifikátů zpráv certifikát určený tento prvek konfigurace se používá k šifrování zpráv ve službě a měl by používat službu pro podepisování odpovědi klientovi.</span><span class="sxs-lookup"><span data-stu-id="63a57-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="63a57-159">Ukládají se jeden certifikát má být použit při služby je určen žádný certifikát.</span><span class="sxs-lookup"><span data-stu-id="63a57-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63a57-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="63a57-160">Example</span></span>  
 <span data-ttu-id="63a57-161">Následující příklad určuje certifikát používaný pro koncové body, jehož identifikátor URI začíná `http://www.contoso.com` a certifikát má použít pro všechny ostatní koncové body, které neprovádějte vyjednávání certifikátu.</span><span class="sxs-lookup"><span data-stu-id="63a57-161">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="63a57-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63a57-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="63a57-163">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="63a57-163">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="63a57-164">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="63a57-164">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="63a57-165">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="63a57-165">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="63a57-166">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="63a57-166">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
