---
title: '&lt;add&gt; elementu &lt;scopedCertificates&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ce1a24cb9a41e5b0ef090cd898c44b481b3bbd4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a><span data-ttu-id="2a12e-102">&lt;add&gt; elementu &lt;scopedCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="2a12e-102">&lt;add&gt; of &lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="2a12e-103">Přidá do kolekce vymezená certifikátů certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="2a12e-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="2a12e-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2a12e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a12e-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2a12e-105">\<behaviors></span></span>  
<span data-ttu-id="2a12e-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="2a12e-106">endpointBehaviors section</span></span>  
<span data-ttu-id="2a12e-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2a12e-107">\<behavior></span></span>  
<span data-ttu-id="2a12e-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="2a12e-108">\<clientCredentials></span></span>  
<span data-ttu-id="2a12e-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="2a12e-109">\<serviceCertificate></span></span>  
<span data-ttu-id="2a12e-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="2a12e-110">\<scopedCertificates></span></span>  
<span data-ttu-id="2a12e-111">\<Přidat > elementu pro \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="2a12e-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a12e-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a12e-112">Syntax</span></span>  
  
```xml  
<add findValue="String"  
          storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
          targetUri="string"  
         x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"   
/>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a12e-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2a12e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2a12e-114">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2a12e-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a12e-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="2a12e-115">Attributes</span></span>  
  
|<span data-ttu-id="2a12e-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="2a12e-116">Attribute</span></span>|<span data-ttu-id="2a12e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2a12e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a12e-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="2a12e-118">targetUri</span></span>|<span data-ttu-id="2a12e-119">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="2a12e-119">String.</span></span> <span data-ttu-id="2a12e-120">Určuje identifikátor URI služby přidruženého k certifikátu.</span><span class="sxs-lookup"><span data-stu-id="2a12e-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="2a12e-121">findValue</span><span class="sxs-lookup"><span data-stu-id="2a12e-121">findValue</span></span>|<span data-ttu-id="2a12e-122">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="2a12e-122">String.</span></span> <span data-ttu-id="2a12e-123">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="2a12e-123">The value to search for.</span></span>|  
|<span data-ttu-id="2a12e-124">X509FindType</span><span class="sxs-lookup"><span data-stu-id="2a12e-124">x509FindType</span></span>|<span data-ttu-id="2a12e-125">Výčet.</span><span class="sxs-lookup"><span data-stu-id="2a12e-125">Enumeration.</span></span> <span data-ttu-id="2a12e-126">Jeden z pole certifikátu pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="2a12e-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="2a12e-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="2a12e-127">storeLocation</span></span>|<span data-ttu-id="2a12e-128">Výčet.</span><span class="sxs-lookup"><span data-stu-id="2a12e-128">Enumeration.</span></span> <span data-ttu-id="2a12e-129">Jednu ze dvou ukládat prohledávaných umístění.</span><span class="sxs-lookup"><span data-stu-id="2a12e-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="2a12e-130">storeName</span><span class="sxs-lookup"><span data-stu-id="2a12e-130">storeName</span></span>|<span data-ttu-id="2a12e-131">Výčet.</span><span class="sxs-lookup"><span data-stu-id="2a12e-131">Enumeration.</span></span> <span data-ttu-id="2a12e-132">Jeden z úložiště systému pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="2a12e-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="2a12e-133">findValue atribut</span><span class="sxs-lookup"><span data-stu-id="2a12e-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="2a12e-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2a12e-134">Value</span></span>|<span data-ttu-id="2a12e-135">Popis</span><span class="sxs-lookup"><span data-stu-id="2a12e-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a12e-136">String</span><span class="sxs-lookup"><span data-stu-id="2a12e-136">String</span></span>|<span data-ttu-id="2a12e-137">Hodnota závisí na poli (zadané v atributu X509FindType) být vyhledán.</span><span class="sxs-lookup"><span data-stu-id="2a12e-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="2a12e-138">Například pokud hledání kryptografický otisk, hodnota musí být řetězec o délce hexadecimální číslice.</span><span class="sxs-lookup"><span data-stu-id="2a12e-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="2a12e-139">Atribut x509FindType</span><span class="sxs-lookup"><span data-stu-id="2a12e-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="2a12e-140">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2a12e-140">Value</span></span>|<span data-ttu-id="2a12e-141">Popis</span><span class="sxs-lookup"><span data-stu-id="2a12e-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a12e-142">Výčet</span><span class="sxs-lookup"><span data-stu-id="2a12e-142">Enumeration</span></span>|<span data-ttu-id="2a12e-143">Hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="2a12e-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="2a12e-144">storeLocation atribut</span><span class="sxs-lookup"><span data-stu-id="2a12e-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="2a12e-145">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2a12e-145">Value</span></span>|<span data-ttu-id="2a12e-146">Popis</span><span class="sxs-lookup"><span data-stu-id="2a12e-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a12e-147">Výčet</span><span class="sxs-lookup"><span data-stu-id="2a12e-147">Enumeration</span></span>|<span data-ttu-id="2a12e-148">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="2a12e-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="2a12e-149">storeName atribut</span><span class="sxs-lookup"><span data-stu-id="2a12e-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="2a12e-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2a12e-150">Value</span></span>|<span data-ttu-id="2a12e-151">Popis</span><span class="sxs-lookup"><span data-stu-id="2a12e-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a12e-152">Výčet</span><span class="sxs-lookup"><span data-stu-id="2a12e-152">Enumeration</span></span>|<span data-ttu-id="2a12e-153">Hodnoty patří: CertificateAuthority adresáře, AuthRoot, zakázané, Moje, Root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="2a12e-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a12e-154">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2a12e-154">Child Elements</span></span>  
 <span data-ttu-id="2a12e-155">Žádné</span><span class="sxs-lookup"><span data-stu-id="2a12e-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a12e-156">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2a12e-156">Parent Elements</span></span>  
  
|<span data-ttu-id="2a12e-157">Prvek</span><span class="sxs-lookup"><span data-stu-id="2a12e-157">Element</span></span>|<span data-ttu-id="2a12e-158">Popis</span><span class="sxs-lookup"><span data-stu-id="2a12e-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a12e-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="2a12e-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="2a12e-160">Představuje kolekci certifikáty X.509, které jsou součástí konkrétní služby (obor) pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="2a12e-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a12e-161">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a12e-161">Remarks</span></span>  
 <span data-ttu-id="2a12e-162">Tento element umožňuje klientovi konfigurace certifikátu pro použití služby založené na adresu URL služby, kterým komunikuje.</span><span class="sxs-lookup"><span data-stu-id="2a12e-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="2a12e-163">To je zvlášť užitečné v vydaných tokenů scénáře, kde může klient komunikovat na více služeb (na koncové služby a také služeb tokenu zprostředkující zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="2a12e-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="2a12e-164">U vazeb, které používají zabezpečení zpráv pomocí certifikátů tento certifikát se používá k šifrování zpráv do služby a očekává se použije pro podepisování odpovědi klientovi službou.</span><span class="sxs-lookup"><span data-stu-id="2a12e-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="2a12e-165">Pokud vazba vyžaduje certifikát pro službu a žádný konkrétní certifikát pro službu, kterou adresu URL se nachází v ScopedCertificates, použije se výchozí certifikát.</span><span class="sxs-lookup"><span data-stu-id="2a12e-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="2a12e-166">Další informace najdete v části "Obor certifikáty" z [postupy: vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="2a12e-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a12e-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a12e-167">Example</span></span>  
 <span data-ttu-id="2a12e-168">Následující příklad přidá certifikát X.509 kolekce.</span><span class="sxs-lookup"><span data-stu-id="2a12e-168">The following example adds an X.509 certificate the collection.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <serviceCertificate>  
     <scopedCertificates>  
      <add targetUri="http://www.contoso.com"   
       findValue="www.Contoso.com"   
       storeLocation="LocalMachine"  
       storeName="Root"   
       x509FindType="FindByIssuerName" />  
     </scopedCertificates>  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a12e-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a12e-169">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="2a12e-170">Postupy: vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="2a12e-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="2a12e-171">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="2a12e-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="2a12e-172">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="2a12e-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="2a12e-173">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2a12e-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
