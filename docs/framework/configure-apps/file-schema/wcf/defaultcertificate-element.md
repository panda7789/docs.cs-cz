---
title: Element <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400418"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="04d8a-102">Element \<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="04d8a-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="04d8a-103">Určuje certifikát X. 509, který se použije, když služba nebo STS neposkytne protokol pro vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="04d8a-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="04d8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04d8a-104">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04d8a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="04d8a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="04d8a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="04d8a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04d8a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="04d8a-107">Attributes</span></span>  
  
|<span data-ttu-id="04d8a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="04d8a-108">Attribute</span></span>|<span data-ttu-id="04d8a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="04d8a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04d8a-110">findValue</span><span class="sxs-lookup"><span data-stu-id="04d8a-110">findValue</span></span>|<span data-ttu-id="04d8a-111">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="04d8a-111">String.</span></span> <span data-ttu-id="04d8a-112">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="04d8a-112">The value to search for.</span></span>|  
|<span data-ttu-id="04d8a-113">x509FindType</span><span class="sxs-lookup"><span data-stu-id="04d8a-113">x509FindType</span></span>|<span data-ttu-id="04d8a-114">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="04d8a-114">Enumeration.</span></span> <span data-ttu-id="04d8a-115">Jedno z polí certifikátu, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="04d8a-115">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="04d8a-116">storeLocation</span><span class="sxs-lookup"><span data-stu-id="04d8a-116">storeLocation</span></span>|<span data-ttu-id="04d8a-117">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="04d8a-117">Enumeration.</span></span> <span data-ttu-id="04d8a-118">Jedno ze dvou umístění úložiště systému, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="04d8a-118">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="04d8a-119">storeName</span><span class="sxs-lookup"><span data-stu-id="04d8a-119">storeName</span></span>|<span data-ttu-id="04d8a-120">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="04d8a-120">Enumeration.</span></span> <span data-ttu-id="04d8a-121">Jedno ze systémových úložišť, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="04d8a-121">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="04d8a-122">findValue – atribut</span><span class="sxs-lookup"><span data-stu-id="04d8a-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="04d8a-123">Hodnota</span><span class="sxs-lookup"><span data-stu-id="04d8a-123">Value</span></span>|<span data-ttu-id="04d8a-124">Description</span><span class="sxs-lookup"><span data-stu-id="04d8a-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04d8a-125">Řetězec</span><span class="sxs-lookup"><span data-stu-id="04d8a-125">String</span></span>|<span data-ttu-id="04d8a-126">Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván.</span><span class="sxs-lookup"><span data-stu-id="04d8a-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="04d8a-127">Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.</span><span class="sxs-lookup"><span data-stu-id="04d8a-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="04d8a-128">x509FindType – atribut</span><span class="sxs-lookup"><span data-stu-id="04d8a-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="04d8a-129">Hodnota</span><span class="sxs-lookup"><span data-stu-id="04d8a-129">Value</span></span>|<span data-ttu-id="04d8a-130">Description</span><span class="sxs-lookup"><span data-stu-id="04d8a-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04d8a-131">Výčet</span><span class="sxs-lookup"><span data-stu-id="04d8a-131">Enumeration</span></span>|<span data-ttu-id="04d8a-132">Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="04d8a-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="04d8a-133">storeLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="04d8a-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="04d8a-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="04d8a-134">Value</span></span>|<span data-ttu-id="04d8a-135">Description</span><span class="sxs-lookup"><span data-stu-id="04d8a-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04d8a-136">Výčet</span><span class="sxs-lookup"><span data-stu-id="04d8a-136">Enumeration</span></span>|<span data-ttu-id="04d8a-137">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="04d8a-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="04d8a-138">storeName – atribut</span><span class="sxs-lookup"><span data-stu-id="04d8a-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="04d8a-139">Hodnota</span><span class="sxs-lookup"><span data-stu-id="04d8a-139">Value</span></span>|<span data-ttu-id="04d8a-140">Description</span><span class="sxs-lookup"><span data-stu-id="04d8a-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04d8a-141">Výčet</span><span class="sxs-lookup"><span data-stu-id="04d8a-141">Enumeration</span></span>|<span data-ttu-id="04d8a-142">Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="04d8a-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04d8a-143">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="04d8a-143">Child Elements</span></span>  
 <span data-ttu-id="04d8a-144">Žádné</span><span class="sxs-lookup"><span data-stu-id="04d8a-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04d8a-145">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="04d8a-145">Parent Elements</span></span>  
  
|<span data-ttu-id="04d8a-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="04d8a-146">Element</span></span>|<span data-ttu-id="04d8a-147">Description</span><span class="sxs-lookup"><span data-stu-id="04d8a-147">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="04d8a-148">Určuje certifikát, který se má použít při ověřování služby pro klienta.</span><span class="sxs-lookup"><span data-stu-id="04d8a-148">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04d8a-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04d8a-149">Remarks</span></span>  
 <span data-ttu-id="04d8a-150">Pro vazby, které používají zabezpečení zpráv založené na certifikátech, se certifikát zadaný pomocí tohoto elementu konfigurace používá k šifrování zpráv do služby a očekává se, že služba bude službu používat k podepisování odpovědí klientovi.</span><span class="sxs-lookup"><span data-stu-id="04d8a-150">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="04d8a-151">Ukládá se jeden certifikát, který se použije, když služba nezadá žádný certifikát.</span><span class="sxs-lookup"><span data-stu-id="04d8a-151">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04d8a-152">Příklad</span><span class="sxs-lookup"><span data-stu-id="04d8a-152">Example</span></span>  
 <span data-ttu-id="04d8a-153">Následující příklad určuje certifikát, který má být použit pro koncové body, jejichž identifikátor URI začíná `http://www.contoso.com` a certifikát, který má být použit pro všechny ostatní koncové body, které neprovádějí vyjednávání certifikátů.</span><span class="sxs-lookup"><span data-stu-id="04d8a-153">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="04d8a-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="04d8a-154">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="04d8a-155">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="04d8a-155">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="04d8a-156">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="04d8a-156">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="04d8a-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="04d8a-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
