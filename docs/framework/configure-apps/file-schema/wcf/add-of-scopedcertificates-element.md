---
title: <add><scopedCertificates> elementu
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 9756d37527fcf888cad930b24677ae8e6a2c8fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920046"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="d4b71-102">\<Přidat > \<prvku > scopedCertificates</span><span class="sxs-lookup"><span data-stu-id="d4b71-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="d4b71-103">Přidá certifikát X. 509 do kolekce certifikátů s vymezeným oborem.</span><span class="sxs-lookup"><span data-stu-id="d4b71-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="d4b71-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d4b71-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d4b71-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="d4b71-105">\<behaviors></span></span>  
<span data-ttu-id="d4b71-106">oddíl endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="d4b71-106">endpointBehaviors section</span></span>  
<span data-ttu-id="d4b71-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="d4b71-107">\<behavior></span></span>  
<span data-ttu-id="d4b71-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="d4b71-108">\<clientCredentials></span></span>  
<span data-ttu-id="d4b71-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="d4b71-109">\<serviceCertificate></span></span>  
<span data-ttu-id="d4b71-110">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="d4b71-110">\<scopedCertificates></span></span>  
<span data-ttu-id="d4b71-111">\<Přidat > element pro \<> scopedCertificates</span><span class="sxs-lookup"><span data-stu-id="d4b71-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b71-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4b71-112">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4b71-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d4b71-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d4b71-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d4b71-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4b71-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="d4b71-115">Attributes</span></span>  
  
|<span data-ttu-id="d4b71-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="d4b71-116">Attribute</span></span>|<span data-ttu-id="d4b71-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d4b71-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4b71-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="d4b71-118">targetUri</span></span>|<span data-ttu-id="d4b71-119">Řetezce.</span><span class="sxs-lookup"><span data-stu-id="d4b71-119">String.</span></span> <span data-ttu-id="d4b71-120">Určuje identifikátor URI služby přidružené k certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d4b71-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="d4b71-121">findValue</span><span class="sxs-lookup"><span data-stu-id="d4b71-121">findValue</span></span>|<span data-ttu-id="d4b71-122">Řetezce.</span><span class="sxs-lookup"><span data-stu-id="d4b71-122">String.</span></span> <span data-ttu-id="d4b71-123">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d4b71-123">The value to search for.</span></span>|  
|<span data-ttu-id="d4b71-124">x509FindType</span><span class="sxs-lookup"><span data-stu-id="d4b71-124">x509FindType</span></span>|<span data-ttu-id="d4b71-125">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="d4b71-125">Enumeration.</span></span> <span data-ttu-id="d4b71-126">Jedno z polí certifikátu, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d4b71-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="d4b71-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="d4b71-127">storeLocation</span></span>|<span data-ttu-id="d4b71-128">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="d4b71-128">Enumeration.</span></span> <span data-ttu-id="d4b71-129">Jedno ze dvou umístění úložiště, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d4b71-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="d4b71-130">storeName</span><span class="sxs-lookup"><span data-stu-id="d4b71-130">storeName</span></span>|<span data-ttu-id="d4b71-131">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="d4b71-131">Enumeration.</span></span> <span data-ttu-id="d4b71-132">Jedno ze systémových úložišť, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d4b71-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="d4b71-133">findValue – atribut</span><span class="sxs-lookup"><span data-stu-id="d4b71-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="d4b71-134">Value</span><span class="sxs-lookup"><span data-stu-id="d4b71-134">Value</span></span>|<span data-ttu-id="d4b71-135">Popis</span><span class="sxs-lookup"><span data-stu-id="d4b71-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4b71-136">String</span><span class="sxs-lookup"><span data-stu-id="d4b71-136">String</span></span>|<span data-ttu-id="d4b71-137">Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván.</span><span class="sxs-lookup"><span data-stu-id="d4b71-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="d4b71-138">Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.</span><span class="sxs-lookup"><span data-stu-id="d4b71-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="d4b71-139">x509FindType – atribut</span><span class="sxs-lookup"><span data-stu-id="d4b71-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="d4b71-140">Value</span><span class="sxs-lookup"><span data-stu-id="d4b71-140">Value</span></span>|<span data-ttu-id="d4b71-141">Popis</span><span class="sxs-lookup"><span data-stu-id="d4b71-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4b71-142">Výčet</span><span class="sxs-lookup"><span data-stu-id="d4b71-142">Enumeration</span></span>|<span data-ttu-id="d4b71-143">Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="d4b71-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="d4b71-144">storeLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="d4b71-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="d4b71-145">Value</span><span class="sxs-lookup"><span data-stu-id="d4b71-145">Value</span></span>|<span data-ttu-id="d4b71-146">Popis</span><span class="sxs-lookup"><span data-stu-id="d4b71-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4b71-147">Výčet</span><span class="sxs-lookup"><span data-stu-id="d4b71-147">Enumeration</span></span>|<span data-ttu-id="d4b71-148">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="d4b71-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="d4b71-149">storeName – atribut</span><span class="sxs-lookup"><span data-stu-id="d4b71-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="d4b71-150">Value</span><span class="sxs-lookup"><span data-stu-id="d4b71-150">Value</span></span>|<span data-ttu-id="d4b71-151">Popis</span><span class="sxs-lookup"><span data-stu-id="d4b71-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4b71-152">Výčet</span><span class="sxs-lookup"><span data-stu-id="d4b71-152">Enumeration</span></span>|<span data-ttu-id="d4b71-153">Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="d4b71-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4b71-154">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d4b71-154">Child Elements</span></span>  
 <span data-ttu-id="d4b71-155">Žádné</span><span class="sxs-lookup"><span data-stu-id="d4b71-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4b71-156">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d4b71-156">Parent Elements</span></span>  
  
|<span data-ttu-id="d4b71-157">Prvek</span><span class="sxs-lookup"><span data-stu-id="d4b71-157">Element</span></span>|<span data-ttu-id="d4b71-158">Popis</span><span class="sxs-lookup"><span data-stu-id="d4b71-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4b71-159">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="d4b71-159">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="d4b71-160">Představuje kolekci certifikátů X. 509 poskytovaných konkrétními službami (vymezenými) pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="d4b71-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4b71-161">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4b71-161">Remarks</span></span>  
 <span data-ttu-id="d4b71-162">Tento prvek umožňuje klientovi nakonfigurovat certifikát služby tak, aby se použil na základě adresy URL služby, se kterou komunikuje.</span><span class="sxs-lookup"><span data-stu-id="d4b71-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="d4b71-163">To je užitečné hlavně ve scénářích vydaných tokenů, kde klient může komunikovat s více službami (koncová služba i zprostředkující služba tokenů zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="d4b71-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="d4b71-164">U vazeb, které používají zabezpečení zpráv založených na certifikátech, se tento certifikát používá k šifrování zpráv do služby a očekává se, že služba bude službu používat k podepisování odpovědí klientovi.</span><span class="sxs-lookup"><span data-stu-id="d4b71-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="d4b71-165">Pokud vazba vyžaduje certifikát pro službu a v ScopedCertificates se nenajde žádný konkrétní certifikát pro adresu URL služby, použije se výchozí certifikát.</span><span class="sxs-lookup"><span data-stu-id="d4b71-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="d4b71-166">Další informace najdete v části ["vymezené certifikáty" v tématu Postupy: Vytvoření federovaného klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="d4b71-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4b71-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4b71-167">Example</span></span>  
 <span data-ttu-id="d4b71-168">Následující příklad přidá do kolekce certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="d4b71-168">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4b71-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4b71-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="d4b71-170">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="d4b71-170">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="d4b71-171">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="d4b71-171">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d4b71-172">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="d4b71-172">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="d4b71-173">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d4b71-173">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
