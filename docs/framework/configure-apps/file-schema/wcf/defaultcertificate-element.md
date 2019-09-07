---
title: Element <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400418"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="0df43-102">\<defaultCertificate – element ></span><span class="sxs-lookup"><span data-stu-id="0df43-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="0df43-103">Určuje certifikát X. 509, který se použije, když služba nebo STS neposkytne protokol pro vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="0df43-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
<span data-ttu-id="0df43-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0df43-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0df43-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0df43-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0df43-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0df43-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="0df43-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0df43-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="0df43-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0df43-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="0df43-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="0df43-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="0df43-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="0df43-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="0df43-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultCertificate >**</span><span class="sxs-lookup"><span data-stu-id="0df43-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0df43-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0df43-112">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0df43-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0df43-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0df43-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0df43-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0df43-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="0df43-115">Attributes</span></span>  
  
|<span data-ttu-id="0df43-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="0df43-116">Attribute</span></span>|<span data-ttu-id="0df43-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0df43-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0df43-118">findValue</span><span class="sxs-lookup"><span data-stu-id="0df43-118">findValue</span></span>|<span data-ttu-id="0df43-119">Řetezce.</span><span class="sxs-lookup"><span data-stu-id="0df43-119">String.</span></span> <span data-ttu-id="0df43-120">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="0df43-120">The value to search for.</span></span>|  
|<span data-ttu-id="0df43-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="0df43-121">x509FindType</span></span>|<span data-ttu-id="0df43-122">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="0df43-122">Enumeration.</span></span> <span data-ttu-id="0df43-123">Jedno z polí certifikátu, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="0df43-123">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="0df43-124">storeLocation</span><span class="sxs-lookup"><span data-stu-id="0df43-124">storeLocation</span></span>|<span data-ttu-id="0df43-125">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="0df43-125">Enumeration.</span></span> <span data-ttu-id="0df43-126">Jedno ze dvou umístění úložiště systému, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="0df43-126">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="0df43-127">storeName</span><span class="sxs-lookup"><span data-stu-id="0df43-127">storeName</span></span>|<span data-ttu-id="0df43-128">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="0df43-128">Enumeration.</span></span> <span data-ttu-id="0df43-129">Jedno ze systémových úložišť, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="0df43-129">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="0df43-130">findValue – atribut</span><span class="sxs-lookup"><span data-stu-id="0df43-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="0df43-131">Value</span><span class="sxs-lookup"><span data-stu-id="0df43-131">Value</span></span>|<span data-ttu-id="0df43-132">Popis</span><span class="sxs-lookup"><span data-stu-id="0df43-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0df43-133">String</span><span class="sxs-lookup"><span data-stu-id="0df43-133">String</span></span>|<span data-ttu-id="0df43-134">Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván.</span><span class="sxs-lookup"><span data-stu-id="0df43-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="0df43-135">Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.</span><span class="sxs-lookup"><span data-stu-id="0df43-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="0df43-136">x509FindType – atribut</span><span class="sxs-lookup"><span data-stu-id="0df43-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="0df43-137">Value</span><span class="sxs-lookup"><span data-stu-id="0df43-137">Value</span></span>|<span data-ttu-id="0df43-138">Popis</span><span class="sxs-lookup"><span data-stu-id="0df43-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0df43-139">Výčet</span><span class="sxs-lookup"><span data-stu-id="0df43-139">Enumeration</span></span>|<span data-ttu-id="0df43-140">Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="0df43-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="0df43-141">storeLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="0df43-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="0df43-142">Value</span><span class="sxs-lookup"><span data-stu-id="0df43-142">Value</span></span>|<span data-ttu-id="0df43-143">Popis</span><span class="sxs-lookup"><span data-stu-id="0df43-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0df43-144">Výčet</span><span class="sxs-lookup"><span data-stu-id="0df43-144">Enumeration</span></span>|<span data-ttu-id="0df43-145">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="0df43-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="0df43-146">storeName – atribut</span><span class="sxs-lookup"><span data-stu-id="0df43-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="0df43-147">Value</span><span class="sxs-lookup"><span data-stu-id="0df43-147">Value</span></span>|<span data-ttu-id="0df43-148">Popis</span><span class="sxs-lookup"><span data-stu-id="0df43-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0df43-149">Výčet</span><span class="sxs-lookup"><span data-stu-id="0df43-149">Enumeration</span></span>|<span data-ttu-id="0df43-150">Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="0df43-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0df43-151">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0df43-151">Child Elements</span></span>  
 <span data-ttu-id="0df43-152">Žádné</span><span class="sxs-lookup"><span data-stu-id="0df43-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0df43-153">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0df43-153">Parent Elements</span></span>  
  
|<span data-ttu-id="0df43-154">Prvek</span><span class="sxs-lookup"><span data-stu-id="0df43-154">Element</span></span>|<span data-ttu-id="0df43-155">Popis</span><span class="sxs-lookup"><span data-stu-id="0df43-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0df43-156">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="0df43-156">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="0df43-157">Určuje certifikát, který se má použít při ověřování služby pro klienta.</span><span class="sxs-lookup"><span data-stu-id="0df43-157">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0df43-158">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0df43-158">Remarks</span></span>  
 <span data-ttu-id="0df43-159">Pro vazby, které používají zabezpečení zpráv založené na certifikátech, se certifikát zadaný pomocí tohoto elementu konfigurace používá k šifrování zpráv do služby a očekává se, že služba bude službu používat k podepisování odpovědí klientovi.</span><span class="sxs-lookup"><span data-stu-id="0df43-159">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="0df43-160">Ukládá se jeden certifikát, který se použije, když služba nezadá žádný certifikát.</span><span class="sxs-lookup"><span data-stu-id="0df43-160">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0df43-161">Příklad</span><span class="sxs-lookup"><span data-stu-id="0df43-161">Example</span></span>  
 <span data-ttu-id="0df43-162">Následující příklad určuje certifikát, který má být použit pro koncové body, jejichž `http://www.contoso.com` identifikátor URI začíná a certifikát, který má být použit pro všechny ostatní koncové body, které neprovádějí vyjednávání certifikátů.</span><span class="sxs-lookup"><span data-stu-id="0df43-162">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0df43-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0df43-163">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="0df43-164">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="0df43-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="0df43-165">\<> ověřování</span><span class="sxs-lookup"><span data-stu-id="0df43-165">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="0df43-166">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="0df43-166">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="0df43-167">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0df43-167">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
