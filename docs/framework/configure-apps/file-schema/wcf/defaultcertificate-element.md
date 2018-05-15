---
title: Element &lt;defaultCertificate&gt;
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: a4af1c6ec452b24634fa50162fa71f069e2451f5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltdefaultcertificategt-element"></a><span data-ttu-id="3ea46-102">Element &lt;defaultCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="3ea46-102">&lt;defaultCertificate&gt; Element</span></span>
<span data-ttu-id="3ea46-103">Určuje certifikát X.509, který se má použít při služby nebo služby tokenů zabezpečení neposkytuje jeden prostřednictvím vyjednávání protokolu.</span><span class="sxs-lookup"><span data-stu-id="3ea46-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="3ea46-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3ea46-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3ea46-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3ea46-105">\<behaviors></span></span>  
<span data-ttu-id="3ea46-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="3ea46-106">endpointBehaviors section</span></span>  
<span data-ttu-id="3ea46-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3ea46-107">\<behavior></span></span>  
<span data-ttu-id="3ea46-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="3ea46-108">\<clientCredentials></span></span>  
<span data-ttu-id="3ea46-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="3ea46-109">\<serviceCertificate></span></span>  
<span data-ttu-id="3ea46-110">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="3ea46-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea46-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ea46-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ea46-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ea46-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3ea46-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ea46-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ea46-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ea46-114">Attributes</span></span>  
  
|<span data-ttu-id="3ea46-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="3ea46-115">Attribute</span></span>|<span data-ttu-id="3ea46-116">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea46-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ea46-117">findValue</span><span class="sxs-lookup"><span data-stu-id="3ea46-117">findValue</span></span>|<span data-ttu-id="3ea46-118">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="3ea46-118">String.</span></span> <span data-ttu-id="3ea46-119">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="3ea46-119">The value to search for.</span></span>|  
|<span data-ttu-id="3ea46-120">X509FindType</span><span class="sxs-lookup"><span data-stu-id="3ea46-120">x509FindType</span></span>|<span data-ttu-id="3ea46-121">Výčet.</span><span class="sxs-lookup"><span data-stu-id="3ea46-121">Enumeration.</span></span> <span data-ttu-id="3ea46-122">Jeden z pole certifikátu pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="3ea46-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="3ea46-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="3ea46-123">storeLocation</span></span>|<span data-ttu-id="3ea46-124">Výčet.</span><span class="sxs-lookup"><span data-stu-id="3ea46-124">Enumeration.</span></span> <span data-ttu-id="3ea46-125">Mezi dvěma systému úložiště prohledávaných umístění.</span><span class="sxs-lookup"><span data-stu-id="3ea46-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="3ea46-126">storeName</span><span class="sxs-lookup"><span data-stu-id="3ea46-126">storeName</span></span>|<span data-ttu-id="3ea46-127">Výčet.</span><span class="sxs-lookup"><span data-stu-id="3ea46-127">Enumeration.</span></span> <span data-ttu-id="3ea46-128">Jeden z úložiště systému pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="3ea46-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="3ea46-129">findValue atribut</span><span class="sxs-lookup"><span data-stu-id="3ea46-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="3ea46-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3ea46-130">Value</span></span>|<span data-ttu-id="3ea46-131">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea46-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ea46-132">String</span><span class="sxs-lookup"><span data-stu-id="3ea46-132">String</span></span>|<span data-ttu-id="3ea46-133">Hodnota závisí na poli (zadané v atributu X509FindType) být vyhledán.</span><span class="sxs-lookup"><span data-stu-id="3ea46-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="3ea46-134">Například pokud hledání kryptografický otisk, hodnota musí být řetězec o délce hexadecimální číslice.</span><span class="sxs-lookup"><span data-stu-id="3ea46-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="3ea46-135">Atribut x509FindType</span><span class="sxs-lookup"><span data-stu-id="3ea46-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="3ea46-136">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3ea46-136">Value</span></span>|<span data-ttu-id="3ea46-137">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea46-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ea46-138">Výčet</span><span class="sxs-lookup"><span data-stu-id="3ea46-138">Enumeration</span></span>|<span data-ttu-id="3ea46-139">Hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="3ea46-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="3ea46-140">storeLocation atribut</span><span class="sxs-lookup"><span data-stu-id="3ea46-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="3ea46-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3ea46-141">Value</span></span>|<span data-ttu-id="3ea46-142">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea46-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ea46-143">Výčet</span><span class="sxs-lookup"><span data-stu-id="3ea46-143">Enumeration</span></span>|<span data-ttu-id="3ea46-144">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="3ea46-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="3ea46-145">storeName atribut</span><span class="sxs-lookup"><span data-stu-id="3ea46-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="3ea46-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3ea46-146">Value</span></span>|<span data-ttu-id="3ea46-147">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea46-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ea46-148">Výčet</span><span class="sxs-lookup"><span data-stu-id="3ea46-148">Enumeration</span></span>|<span data-ttu-id="3ea46-149">Hodnoty patří: CertificateAuthority adresáře, AuthRoot, zakázané, Moje, Root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="3ea46-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ea46-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ea46-150">Child Elements</span></span>  
 <span data-ttu-id="3ea46-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="3ea46-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ea46-152">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ea46-152">Parent Elements</span></span>  
  
|<span data-ttu-id="3ea46-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ea46-153">Element</span></span>|<span data-ttu-id="3ea46-154">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea46-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ea46-155">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="3ea46-155">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="3ea46-156">Určuje certifikát pro použití při ověřování služby klienta.</span><span class="sxs-lookup"><span data-stu-id="3ea46-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ea46-157">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ea46-157">Remarks</span></span>  
 <span data-ttu-id="3ea46-158">U vazeb, které používají zabezpečení zpráv pomocí certifikátů certifikát určený element tato konfigurace se používá k šifrování zpráv do služby a očekává se použije pro podepisování odpovědi klientovi službou.</span><span class="sxs-lookup"><span data-stu-id="3ea46-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="3ea46-159">Ukládají se jeden certifikát, který se má použít, když je zadán žádný certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="3ea46-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ea46-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ea46-160">Example</span></span>  
 <span data-ttu-id="3ea46-161">Následující příklad určuje certifikát má použít pro koncové body, jejichž URI začíná http://www.contoso.com a certifikát má použít pro všechny ostatní koncové body, které neprovádět vyjednávání certifikátu.</span><span class="sxs-lookup"><span data-stu-id="3ea46-161">The following example specifies a certificate to use for endpoints whose URI begins with http://www.contoso.com and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ea46-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ea46-162">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [<span data-ttu-id="3ea46-163">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="3ea46-163">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="3ea46-164">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="3ea46-164">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="3ea46-165">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="3ea46-165">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="3ea46-166">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3ea46-166">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
