---
title: Element &lt;defaultCertificate&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4424b8b5e0389c0a0395550fddb71ac34e0fb987
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaultcertificategt-element"></a><span data-ttu-id="2c4e1-102">Element &lt;defaultCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="2c4e1-102">&lt;defaultCertificate&gt; Element</span></span>
<span data-ttu-id="2c4e1-103">Určuje certifikát X.509, který se má použít při služby nebo služby tokenů zabezpečení neposkytuje jeden prostřednictvím vyjednávání protokolu.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="2c4e1-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2c4e1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2c4e1-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2c4e1-105">\<behaviors></span></span>  
<span data-ttu-id="2c4e1-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="2c4e1-106">endpointBehaviors section</span></span>  
<span data-ttu-id="2c4e1-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2c4e1-107">\<behavior></span></span>  
<span data-ttu-id="2c4e1-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="2c4e1-108">\<clientCredentials></span></span>  
<span data-ttu-id="2c4e1-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="2c4e1-109">\<serviceCertificate></span></span>  
<span data-ttu-id="2c4e1-110">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="2c4e1-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c4e1-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c4e1-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c4e1-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2c4e1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2c4e1-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2c4e1-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c4e1-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="2c4e1-114">Attributes</span></span>  
  
|<span data-ttu-id="2c4e1-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="2c4e1-115">Attribute</span></span>|<span data-ttu-id="2c4e1-116">Popis</span><span class="sxs-lookup"><span data-stu-id="2c4e1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c4e1-117">findValue</span><span class="sxs-lookup"><span data-stu-id="2c4e1-117">findValue</span></span>|<span data-ttu-id="2c4e1-118">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-118">String.</span></span> <span data-ttu-id="2c4e1-119">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-119">The value to search for.</span></span>|  
|<span data-ttu-id="2c4e1-120">X509FindType</span><span class="sxs-lookup"><span data-stu-id="2c4e1-120">x509FindType</span></span>|<span data-ttu-id="2c4e1-121">Výčet.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-121">Enumeration.</span></span> <span data-ttu-id="2c4e1-122">Jeden z pole certifikátu pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="2c4e1-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="2c4e1-123">storeLocation</span></span>|<span data-ttu-id="2c4e1-124">Výčet.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-124">Enumeration.</span></span> <span data-ttu-id="2c4e1-125">Mezi dvěma systému úložiště prohledávaných umístění.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="2c4e1-126">storeName</span><span class="sxs-lookup"><span data-stu-id="2c4e1-126">storeName</span></span>|<span data-ttu-id="2c4e1-127">Výčet.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-127">Enumeration.</span></span> <span data-ttu-id="2c4e1-128">Jeden z úložiště systému pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="2c4e1-129">findValue atribut</span><span class="sxs-lookup"><span data-stu-id="2c4e1-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="2c4e1-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2c4e1-130">Value</span></span>|<span data-ttu-id="2c4e1-131">Popis</span><span class="sxs-lookup"><span data-stu-id="2c4e1-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c4e1-132">String</span><span class="sxs-lookup"><span data-stu-id="2c4e1-132">String</span></span>|<span data-ttu-id="2c4e1-133">Hodnota závisí na poli (zadané v atributu X509FindType) být vyhledán.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="2c4e1-134">Například pokud hledání kryptografický otisk, hodnota musí být řetězec o délce hexadecimální číslice.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="2c4e1-135">Atribut x509FindType</span><span class="sxs-lookup"><span data-stu-id="2c4e1-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="2c4e1-136">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2c4e1-136">Value</span></span>|<span data-ttu-id="2c4e1-137">Popis</span><span class="sxs-lookup"><span data-stu-id="2c4e1-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c4e1-138">Výčet</span><span class="sxs-lookup"><span data-stu-id="2c4e1-138">Enumeration</span></span>|<span data-ttu-id="2c4e1-139">Hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="2c4e1-140">storeLocation atribut</span><span class="sxs-lookup"><span data-stu-id="2c4e1-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="2c4e1-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2c4e1-141">Value</span></span>|<span data-ttu-id="2c4e1-142">Popis</span><span class="sxs-lookup"><span data-stu-id="2c4e1-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c4e1-143">Výčet</span><span class="sxs-lookup"><span data-stu-id="2c4e1-143">Enumeration</span></span>|<span data-ttu-id="2c4e1-144">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="2c4e1-145">storeName atribut</span><span class="sxs-lookup"><span data-stu-id="2c4e1-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="2c4e1-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2c4e1-146">Value</span></span>|<span data-ttu-id="2c4e1-147">Popis</span><span class="sxs-lookup"><span data-stu-id="2c4e1-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c4e1-148">Výčet</span><span class="sxs-lookup"><span data-stu-id="2c4e1-148">Enumeration</span></span>|<span data-ttu-id="2c4e1-149">Hodnoty patří: CertificateAuthority adresáře, AuthRoot, zakázané, Moje, Root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c4e1-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2c4e1-150">Child Elements</span></span>  
 <span data-ttu-id="2c4e1-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="2c4e1-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c4e1-152">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2c4e1-152">Parent Elements</span></span>  
  
|<span data-ttu-id="2c4e1-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="2c4e1-153">Element</span></span>|<span data-ttu-id="2c4e1-154">Popis</span><span class="sxs-lookup"><span data-stu-id="2c4e1-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c4e1-155">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="2c4e1-155">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="2c4e1-156">Určuje certifikát pro použití při ověřování služby klienta.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c4e1-157">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c4e1-157">Remarks</span></span>  
 <span data-ttu-id="2c4e1-158">U vazeb, které používají zabezpečení zpráv pomocí certifikátů certifikát určený element tato konfigurace se používá k šifrování zpráv do služby a očekává se použije pro podepisování odpovědi klientovi službou.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="2c4e1-159">Ukládají se jeden certifikát, který se má použít, když je zadán žádný certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c4e1-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c4e1-160">Example</span></span>  
 <span data-ttu-id="2c4e1-161">Následující příklad určuje certifikát má použít pro koncové body, jejichž URI začíná http://www.contoso.com a certifikát má použít pro všechny ostatní koncové body, které neprovádět vyjednávání certifikátu.</span><span class="sxs-lookup"><span data-stu-id="2c4e1-161">The following example specifies a certificate to use for endpoints whose URI begins with http://www.contoso.com and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c4e1-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c4e1-162">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [<span data-ttu-id="2c4e1-163">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="2c4e1-163">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="2c4e1-164">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="2c4e1-164">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="2c4e1-165">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="2c4e1-165">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="2c4e1-166">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2c4e1-166">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
