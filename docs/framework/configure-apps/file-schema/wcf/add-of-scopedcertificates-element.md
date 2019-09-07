---
title: <add><scopedCertificates> elementu
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: b00a342108beca69a906fbf6212915768e98778f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398348"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="c86d9-102">\<Přidat > \<prvku > scopedCertificates</span><span class="sxs-lookup"><span data-stu-id="c86d9-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="c86d9-103">Přidá certifikát X. 509 do kolekce certifikátů s vymezeným oborem.</span><span class="sxs-lookup"><span data-stu-id="c86d9-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
<span data-ttu-id="c86d9-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c86d9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c86d9-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c86d9-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c86d9-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c86d9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c86d9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c86d9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="c86d9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c86d9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="c86d9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c86d9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="c86d9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="c86d9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="c86d9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<scopedCertificates >** ](scopedcertificates-element.md)</span><span class="sxs-lookup"><span data-stu-id="c86d9-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)</span></span>\
<span data-ttu-id="c86d9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="c86d9-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c86d9-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c86d9-113">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c86d9-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c86d9-114">Attributes and Elements</span></span>  
 <span data-ttu-id="c86d9-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c86d9-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c86d9-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="c86d9-116">Attributes</span></span>  
  
|<span data-ttu-id="c86d9-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="c86d9-117">Attribute</span></span>|<span data-ttu-id="c86d9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="c86d9-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c86d9-119">targetUri</span><span class="sxs-lookup"><span data-stu-id="c86d9-119">targetUri</span></span>|<span data-ttu-id="c86d9-120">Řetezce.</span><span class="sxs-lookup"><span data-stu-id="c86d9-120">String.</span></span> <span data-ttu-id="c86d9-121">Určuje identifikátor URI služby přidružené k certifikátu.</span><span class="sxs-lookup"><span data-stu-id="c86d9-121">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="c86d9-122">findValue</span><span class="sxs-lookup"><span data-stu-id="c86d9-122">findValue</span></span>|<span data-ttu-id="c86d9-123">Řetezce.</span><span class="sxs-lookup"><span data-stu-id="c86d9-123">String.</span></span> <span data-ttu-id="c86d9-124">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="c86d9-124">The value to search for.</span></span>|  
|<span data-ttu-id="c86d9-125">x509FindType</span><span class="sxs-lookup"><span data-stu-id="c86d9-125">x509FindType</span></span>|<span data-ttu-id="c86d9-126">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="c86d9-126">Enumeration.</span></span> <span data-ttu-id="c86d9-127">Jedno z polí certifikátu, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="c86d9-127">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="c86d9-128">storeLocation</span><span class="sxs-lookup"><span data-stu-id="c86d9-128">storeLocation</span></span>|<span data-ttu-id="c86d9-129">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="c86d9-129">Enumeration.</span></span> <span data-ttu-id="c86d9-130">Jedno ze dvou umístění úložiště, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="c86d9-130">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="c86d9-131">storeName</span><span class="sxs-lookup"><span data-stu-id="c86d9-131">storeName</span></span>|<span data-ttu-id="c86d9-132">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="c86d9-132">Enumeration.</span></span> <span data-ttu-id="c86d9-133">Jedno ze systémových úložišť, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="c86d9-133">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="c86d9-134">findValue – atribut</span><span class="sxs-lookup"><span data-stu-id="c86d9-134">findValue Attribute</span></span>  
  
|<span data-ttu-id="c86d9-135">Value</span><span class="sxs-lookup"><span data-stu-id="c86d9-135">Value</span></span>|<span data-ttu-id="c86d9-136">Popis</span><span class="sxs-lookup"><span data-stu-id="c86d9-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c86d9-137">String</span><span class="sxs-lookup"><span data-stu-id="c86d9-137">String</span></span>|<span data-ttu-id="c86d9-138">Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván.</span><span class="sxs-lookup"><span data-stu-id="c86d9-138">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="c86d9-139">Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.</span><span class="sxs-lookup"><span data-stu-id="c86d9-139">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="c86d9-140">x509FindType – atribut</span><span class="sxs-lookup"><span data-stu-id="c86d9-140">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="c86d9-141">Value</span><span class="sxs-lookup"><span data-stu-id="c86d9-141">Value</span></span>|<span data-ttu-id="c86d9-142">Popis</span><span class="sxs-lookup"><span data-stu-id="c86d9-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c86d9-143">Výčet</span><span class="sxs-lookup"><span data-stu-id="c86d9-143">Enumeration</span></span>|<span data-ttu-id="c86d9-144">Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="c86d9-144">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="c86d9-145">storeLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="c86d9-145">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="c86d9-146">Value</span><span class="sxs-lookup"><span data-stu-id="c86d9-146">Value</span></span>|<span data-ttu-id="c86d9-147">Popis</span><span class="sxs-lookup"><span data-stu-id="c86d9-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c86d9-148">Výčet</span><span class="sxs-lookup"><span data-stu-id="c86d9-148">Enumeration</span></span>|<span data-ttu-id="c86d9-149">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c86d9-149">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="c86d9-150">storeName – atribut</span><span class="sxs-lookup"><span data-stu-id="c86d9-150">storeName Attribute</span></span>  
  
|<span data-ttu-id="c86d9-151">Value</span><span class="sxs-lookup"><span data-stu-id="c86d9-151">Value</span></span>|<span data-ttu-id="c86d9-152">Popis</span><span class="sxs-lookup"><span data-stu-id="c86d9-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c86d9-153">Výčet</span><span class="sxs-lookup"><span data-stu-id="c86d9-153">Enumeration</span></span>|<span data-ttu-id="c86d9-154">Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="c86d9-154">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c86d9-155">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c86d9-155">Child Elements</span></span>  
 <span data-ttu-id="c86d9-156">Žádné</span><span class="sxs-lookup"><span data-stu-id="c86d9-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c86d9-157">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c86d9-157">Parent Elements</span></span>  
  
|<span data-ttu-id="c86d9-158">Prvek</span><span class="sxs-lookup"><span data-stu-id="c86d9-158">Element</span></span>|<span data-ttu-id="c86d9-159">Popis</span><span class="sxs-lookup"><span data-stu-id="c86d9-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c86d9-160">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="c86d9-160">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="c86d9-161">Představuje kolekci certifikátů X. 509 poskytovaných konkrétními službami (vymezenými) pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="c86d9-161">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c86d9-162">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c86d9-162">Remarks</span></span>  
 <span data-ttu-id="c86d9-163">Tento prvek umožňuje klientovi nakonfigurovat certifikát služby tak, aby se použil na základě adresy URL služby, se kterou komunikuje.</span><span class="sxs-lookup"><span data-stu-id="c86d9-163">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="c86d9-164">To je užitečné hlavně ve scénářích vydaných tokenů, kde klient může komunikovat s více službami (koncová služba i zprostředkující služba tokenů zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="c86d9-164">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="c86d9-165">U vazeb, které používají zabezpečení zpráv založených na certifikátech, se tento certifikát používá k šifrování zpráv do služby a očekává se, že služba bude službu používat k podepisování odpovědí klientovi.</span><span class="sxs-lookup"><span data-stu-id="c86d9-165">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="c86d9-166">Pokud vazba vyžaduje certifikát pro službu a v ScopedCertificates se nenajde žádný konkrétní certifikát pro adresu URL služby, použije se výchozí certifikát.</span><span class="sxs-lookup"><span data-stu-id="c86d9-166">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="c86d9-167">Další informace najdete v části ["vymezené certifikáty" v tématu Postupy: Vytvoření federovaného klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="c86d9-167">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c86d9-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="c86d9-168">Example</span></span>  
 <span data-ttu-id="c86d9-169">Následující příklad přidá do kolekce certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="c86d9-169">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c86d9-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c86d9-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="c86d9-171">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="c86d9-171">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="c86d9-172">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="c86d9-172">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c86d9-173">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="c86d9-173">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c86d9-174">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c86d9-174">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
