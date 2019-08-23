---
title: Element <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 93410e815a156f91db1962f05fb1aa6baca7f955
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919261"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="4f6f3-102">\<defaultCertificate – element ></span><span class="sxs-lookup"><span data-stu-id="4f6f3-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="4f6f3-103">Určuje certifikát X. 509, který se použije, když služba nebo STS neposkytne protokol pro vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="4f6f3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4f6f3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4f6f3-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="4f6f3-105">\<behaviors></span></span>  
<span data-ttu-id="4f6f3-106">oddíl endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="4f6f3-106">endpointBehaviors section</span></span>  
<span data-ttu-id="4f6f3-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="4f6f3-107">\<behavior></span></span>  
<span data-ttu-id="4f6f3-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="4f6f3-108">\<clientCredentials></span></span>  
<span data-ttu-id="4f6f3-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="4f6f3-109">\<serviceCertificate></span></span>  
<span data-ttu-id="4f6f3-110">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="4f6f3-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f6f3-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f6f3-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f6f3-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4f6f3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4f6f3-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f6f3-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="4f6f3-114">Attributes</span></span>  
  
|<span data-ttu-id="4f6f3-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="4f6f3-115">Attribute</span></span>|<span data-ttu-id="4f6f3-116">Popis</span><span class="sxs-lookup"><span data-stu-id="4f6f3-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f6f3-117">findValue</span><span class="sxs-lookup"><span data-stu-id="4f6f3-117">findValue</span></span>|<span data-ttu-id="4f6f3-118">Řetezce.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-118">String.</span></span> <span data-ttu-id="4f6f3-119">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-119">The value to search for.</span></span>|  
|<span data-ttu-id="4f6f3-120">x509FindType</span><span class="sxs-lookup"><span data-stu-id="4f6f3-120">x509FindType</span></span>|<span data-ttu-id="4f6f3-121">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-121">Enumeration.</span></span> <span data-ttu-id="4f6f3-122">Jedno z polí certifikátu, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="4f6f3-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="4f6f3-123">storeLocation</span></span>|<span data-ttu-id="4f6f3-124">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-124">Enumeration.</span></span> <span data-ttu-id="4f6f3-125">Jedno ze dvou umístění úložiště systému, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="4f6f3-126">storeName</span><span class="sxs-lookup"><span data-stu-id="4f6f3-126">storeName</span></span>|<span data-ttu-id="4f6f3-127">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-127">Enumeration.</span></span> <span data-ttu-id="4f6f3-128">Jedno ze systémových úložišť, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="4f6f3-129">findValue – atribut</span><span class="sxs-lookup"><span data-stu-id="4f6f3-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="4f6f3-130">Value</span><span class="sxs-lookup"><span data-stu-id="4f6f3-130">Value</span></span>|<span data-ttu-id="4f6f3-131">Popis</span><span class="sxs-lookup"><span data-stu-id="4f6f3-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f6f3-132">String</span><span class="sxs-lookup"><span data-stu-id="4f6f3-132">String</span></span>|<span data-ttu-id="4f6f3-133">Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="4f6f3-134">Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="4f6f3-135">x509FindType – atribut</span><span class="sxs-lookup"><span data-stu-id="4f6f3-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="4f6f3-136">Value</span><span class="sxs-lookup"><span data-stu-id="4f6f3-136">Value</span></span>|<span data-ttu-id="4f6f3-137">Popis</span><span class="sxs-lookup"><span data-stu-id="4f6f3-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f6f3-138">Výčet</span><span class="sxs-lookup"><span data-stu-id="4f6f3-138">Enumeration</span></span>|<span data-ttu-id="4f6f3-139">Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="4f6f3-140">storeLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="4f6f3-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="4f6f3-141">Value</span><span class="sxs-lookup"><span data-stu-id="4f6f3-141">Value</span></span>|<span data-ttu-id="4f6f3-142">Popis</span><span class="sxs-lookup"><span data-stu-id="4f6f3-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f6f3-143">Výčet</span><span class="sxs-lookup"><span data-stu-id="4f6f3-143">Enumeration</span></span>|<span data-ttu-id="4f6f3-144">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="4f6f3-145">storeName – atribut</span><span class="sxs-lookup"><span data-stu-id="4f6f3-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="4f6f3-146">Value</span><span class="sxs-lookup"><span data-stu-id="4f6f3-146">Value</span></span>|<span data-ttu-id="4f6f3-147">Popis</span><span class="sxs-lookup"><span data-stu-id="4f6f3-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f6f3-148">Výčet</span><span class="sxs-lookup"><span data-stu-id="4f6f3-148">Enumeration</span></span>|<span data-ttu-id="4f6f3-149">Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f6f3-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4f6f3-150">Child Elements</span></span>  
 <span data-ttu-id="4f6f3-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="4f6f3-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f6f3-152">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4f6f3-152">Parent Elements</span></span>  
  
|<span data-ttu-id="4f6f3-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="4f6f3-153">Element</span></span>|<span data-ttu-id="4f6f3-154">Popis</span><span class="sxs-lookup"><span data-stu-id="4f6f3-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f6f3-155">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="4f6f3-155">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="4f6f3-156">Určuje certifikát, který se má použít při ověřování služby pro klienta.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f6f3-157">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f6f3-157">Remarks</span></span>  
 <span data-ttu-id="4f6f3-158">Pro vazby, které používají zabezpečení zpráv založené na certifikátech, se certifikát zadaný pomocí tohoto elementu konfigurace používá k šifrování zpráv do služby a očekává se, že služba bude službu používat k podepisování odpovědí klientovi.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="4f6f3-159">Ukládá se jeden certifikát, který se použije, když služba nezadá žádný certifikát.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f6f3-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f6f3-160">Example</span></span>  
 <span data-ttu-id="4f6f3-161">Následující příklad určuje certifikát, který má být použit pro koncové body, jejichž `http://www.contoso.com` identifikátor URI začíná a certifikát, který má být použit pro všechny ostatní koncové body, které neprovádějí vyjednávání certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4f6f3-161">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f6f3-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f6f3-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="4f6f3-163">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="4f6f3-163">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="4f6f3-164">\<> ověřování</span><span class="sxs-lookup"><span data-stu-id="4f6f3-164">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="4f6f3-165">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="4f6f3-165">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="4f6f3-166">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4f6f3-166">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
