---
title: Element &lt;defaultCertificate&gt;
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 9b99ee36fdb924ea12f3023984a3aa4b590937e8
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847851"
---
# <a name="ltdefaultcertificategt-element"></a><span data-ttu-id="f6442-102">Element &lt;defaultCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="f6442-102">&lt;defaultCertificate&gt; Element</span></span>
<span data-ttu-id="f6442-103">Určuje certifikát X.509, který se má použít při služba nebo STS neposkytne pomocí protokolu vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="f6442-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="f6442-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f6442-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f6442-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f6442-105">\<behaviors></span></span>  
<span data-ttu-id="f6442-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="f6442-106">endpointBehaviors section</span></span>  
<span data-ttu-id="f6442-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f6442-107">\<behavior></span></span>  
<span data-ttu-id="f6442-108">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f6442-108">\<clientCredentials></span></span>  
<span data-ttu-id="f6442-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="f6442-109">\<serviceCertificate></span></span>  
<span data-ttu-id="f6442-110">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="f6442-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6442-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6442-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6442-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f6442-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f6442-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f6442-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6442-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="f6442-114">Attributes</span></span>  
  
|<span data-ttu-id="f6442-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="f6442-115">Attribute</span></span>|<span data-ttu-id="f6442-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f6442-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6442-117">findValue</span><span class="sxs-lookup"><span data-stu-id="f6442-117">findValue</span></span>|<span data-ttu-id="f6442-118">řetězec.</span><span class="sxs-lookup"><span data-stu-id="f6442-118">String.</span></span> <span data-ttu-id="f6442-119">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="f6442-119">The value to search for.</span></span>|  
|<span data-ttu-id="f6442-120">X509FindType</span><span class="sxs-lookup"><span data-stu-id="f6442-120">x509FindType</span></span>|<span data-ttu-id="f6442-121">Výčet.</span><span class="sxs-lookup"><span data-stu-id="f6442-121">Enumeration.</span></span> <span data-ttu-id="f6442-122">Jeden z pole certifikátu k prohledání.</span><span class="sxs-lookup"><span data-stu-id="f6442-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="f6442-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="f6442-123">storeLocation</span></span>|<span data-ttu-id="f6442-124">Výčet.</span><span class="sxs-lookup"><span data-stu-id="f6442-124">Enumeration.</span></span> <span data-ttu-id="f6442-125">Jedno ze dvou systémových úložišť k prohledání.</span><span class="sxs-lookup"><span data-stu-id="f6442-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="f6442-126">storeName</span><span class="sxs-lookup"><span data-stu-id="f6442-126">storeName</span></span>|<span data-ttu-id="f6442-127">Výčet.</span><span class="sxs-lookup"><span data-stu-id="f6442-127">Enumeration.</span></span> <span data-ttu-id="f6442-128">Jedno ze systémových úložišť k prohledání.</span><span class="sxs-lookup"><span data-stu-id="f6442-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="f6442-129">findValue atribut</span><span class="sxs-lookup"><span data-stu-id="f6442-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="f6442-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f6442-130">Value</span></span>|<span data-ttu-id="f6442-131">Popis</span><span class="sxs-lookup"><span data-stu-id="f6442-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f6442-132">String</span><span class="sxs-lookup"><span data-stu-id="f6442-132">String</span></span>|<span data-ttu-id="f6442-133">Hodnota závisí na poli (určenému atributem X509FindType) být vyhledán.</span><span class="sxs-lookup"><span data-stu-id="f6442-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="f6442-134">Například pokud hledání kryptografickým otiskem, hodnota musí být řetězec šestnáctkových čísel.</span><span class="sxs-lookup"><span data-stu-id="f6442-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="f6442-135">Atribut x509FindType</span><span class="sxs-lookup"><span data-stu-id="f6442-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="f6442-136">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f6442-136">Value</span></span>|<span data-ttu-id="f6442-137">Popis</span><span class="sxs-lookup"><span data-stu-id="f6442-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f6442-138">Výčet</span><span class="sxs-lookup"><span data-stu-id="f6442-138">Enumeration</span></span>|<span data-ttu-id="f6442-139">Mezi hodnoty patří: FindByThumbprint FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="f6442-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="f6442-140">storeLocation atribut</span><span class="sxs-lookup"><span data-stu-id="f6442-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="f6442-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f6442-141">Value</span></span>|<span data-ttu-id="f6442-142">Popis</span><span class="sxs-lookup"><span data-stu-id="f6442-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f6442-143">Výčet</span><span class="sxs-lookup"><span data-stu-id="f6442-143">Enumeration</span></span>|<span data-ttu-id="f6442-144">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="f6442-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="f6442-145">storeName atribut</span><span class="sxs-lookup"><span data-stu-id="f6442-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="f6442-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f6442-146">Value</span></span>|<span data-ttu-id="f6442-147">Popis</span><span class="sxs-lookup"><span data-stu-id="f6442-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f6442-148">Výčet</span><span class="sxs-lookup"><span data-stu-id="f6442-148">Enumeration</span></span>|<span data-ttu-id="f6442-149">Mezi hodnoty patří: adresáře, AuthRoot, CertificateAuthority zakázané, My, Root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="f6442-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6442-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f6442-150">Child Elements</span></span>  
 <span data-ttu-id="f6442-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="f6442-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6442-152">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f6442-152">Parent Elements</span></span>  
  
|<span data-ttu-id="f6442-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="f6442-153">Element</span></span>|<span data-ttu-id="f6442-154">Popis</span><span class="sxs-lookup"><span data-stu-id="f6442-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6442-155">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="f6442-155">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="f6442-156">Určuje certifikát používaný při ověřování služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="f6442-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6442-157">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6442-157">Remarks</span></span>  
 <span data-ttu-id="f6442-158">U vazeb, které používají zabezpečení na základě certifikátů zpráv certifikát určený tento prvek konfigurace se používá k šifrování zpráv ve službě a měl by používat službu pro podepisování odpovědi klientovi.</span><span class="sxs-lookup"><span data-stu-id="f6442-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="f6442-159">Ukládají se jeden certifikát má být použit při služby je určen žádný certifikát.</span><span class="sxs-lookup"><span data-stu-id="f6442-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6442-160">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6442-160">Example</span></span>  
 <span data-ttu-id="f6442-161">Následující příklad určuje certifikát používaný pro koncové body, jehož identifikátor URI začíná `http://www.contoso.com` a certifikát má použít pro všechny ostatní koncové body, které neprovádějte vyjednávání certifikátu.</span><span class="sxs-lookup"><span data-stu-id="f6442-161">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6442-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6442-162">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [<span data-ttu-id="f6442-163">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="f6442-163">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="f6442-164">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="f6442-164">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="f6442-165">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="f6442-165">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="f6442-166">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f6442-166">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
