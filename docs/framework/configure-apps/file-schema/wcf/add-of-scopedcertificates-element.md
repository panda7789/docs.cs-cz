---
title: <add> z <scopedCertificates> – Element
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 06a624d0146745581dfe907d044d1f7d3b857902
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673860"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="4b20d-102">\<Přidat > z \<scopedCertificates > – Element</span><span class="sxs-lookup"><span data-stu-id="4b20d-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="4b20d-103">Přidá certifikát X.509 do kolekce vymezených certifikátů.</span><span class="sxs-lookup"><span data-stu-id="4b20d-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="4b20d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4b20d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4b20d-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4b20d-105">\<behaviors></span></span>  
<span data-ttu-id="4b20d-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="4b20d-106">endpointBehaviors section</span></span>  
<span data-ttu-id="4b20d-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4b20d-107">\<behavior></span></span>  
<span data-ttu-id="4b20d-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="4b20d-108">\<clientCredentials></span></span>  
<span data-ttu-id="4b20d-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="4b20d-109">\<serviceCertificate></span></span>  
<span data-ttu-id="4b20d-110">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="4b20d-110">\<scopedCertificates></span></span>  
<span data-ttu-id="4b20d-111">\<Přidat > – element pro \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="4b20d-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b20d-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b20d-112">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b20d-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4b20d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4b20d-114">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4b20d-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b20d-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="4b20d-115">Attributes</span></span>  
  
|<span data-ttu-id="4b20d-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="4b20d-116">Attribute</span></span>|<span data-ttu-id="4b20d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="4b20d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b20d-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="4b20d-118">targetUri</span></span>|<span data-ttu-id="4b20d-119">řetězec.</span><span class="sxs-lookup"><span data-stu-id="4b20d-119">String.</span></span> <span data-ttu-id="4b20d-120">Určuje identifikátor URI služby přidruženého k certifikátu.</span><span class="sxs-lookup"><span data-stu-id="4b20d-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="4b20d-121">findValue</span><span class="sxs-lookup"><span data-stu-id="4b20d-121">findValue</span></span>|<span data-ttu-id="4b20d-122">řetězec.</span><span class="sxs-lookup"><span data-stu-id="4b20d-122">String.</span></span> <span data-ttu-id="4b20d-123">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="4b20d-123">The value to search for.</span></span>|  
|<span data-ttu-id="4b20d-124">x509FindType</span><span class="sxs-lookup"><span data-stu-id="4b20d-124">x509FindType</span></span>|<span data-ttu-id="4b20d-125">Výčet.</span><span class="sxs-lookup"><span data-stu-id="4b20d-125">Enumeration.</span></span> <span data-ttu-id="4b20d-126">Jeden z pole certifikátu k prohledání.</span><span class="sxs-lookup"><span data-stu-id="4b20d-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="4b20d-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="4b20d-127">storeLocation</span></span>|<span data-ttu-id="4b20d-128">Výčet.</span><span class="sxs-lookup"><span data-stu-id="4b20d-128">Enumeration.</span></span> <span data-ttu-id="4b20d-129">Jedno ze dvou umístění úložišť k prohledání.</span><span class="sxs-lookup"><span data-stu-id="4b20d-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="4b20d-130">storeName</span><span class="sxs-lookup"><span data-stu-id="4b20d-130">storeName</span></span>|<span data-ttu-id="4b20d-131">Výčet.</span><span class="sxs-lookup"><span data-stu-id="4b20d-131">Enumeration.</span></span> <span data-ttu-id="4b20d-132">Jedno ze systémových úložišť k prohledání.</span><span class="sxs-lookup"><span data-stu-id="4b20d-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="4b20d-133">findValue atribut</span><span class="sxs-lookup"><span data-stu-id="4b20d-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="4b20d-134">Value</span><span class="sxs-lookup"><span data-stu-id="4b20d-134">Value</span></span>|<span data-ttu-id="4b20d-135">Popis</span><span class="sxs-lookup"><span data-stu-id="4b20d-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4b20d-136">String</span><span class="sxs-lookup"><span data-stu-id="4b20d-136">String</span></span>|<span data-ttu-id="4b20d-137">Hodnota závisí na poli (určenému atributem X509FindType) být vyhledán.</span><span class="sxs-lookup"><span data-stu-id="4b20d-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="4b20d-138">Například pokud hledání kryptografickým otiskem, hodnota musí být řetězec šestnáctkových čísel.</span><span class="sxs-lookup"><span data-stu-id="4b20d-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="4b20d-139">Atribut x509FindType</span><span class="sxs-lookup"><span data-stu-id="4b20d-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="4b20d-140">Value</span><span class="sxs-lookup"><span data-stu-id="4b20d-140">Value</span></span>|<span data-ttu-id="4b20d-141">Popis</span><span class="sxs-lookup"><span data-stu-id="4b20d-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4b20d-142">Výčet</span><span class="sxs-lookup"><span data-stu-id="4b20d-142">Enumeration</span></span>|<span data-ttu-id="4b20d-143">Mezi hodnoty patří: FindByThumbprint FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="4b20d-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="4b20d-144">storeLocation atribut</span><span class="sxs-lookup"><span data-stu-id="4b20d-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="4b20d-145">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4b20d-145">Value</span></span>|<span data-ttu-id="4b20d-146">Popis</span><span class="sxs-lookup"><span data-stu-id="4b20d-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4b20d-147">Výčet</span><span class="sxs-lookup"><span data-stu-id="4b20d-147">Enumeration</span></span>|<span data-ttu-id="4b20d-148">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="4b20d-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="4b20d-149">storeName atribut</span><span class="sxs-lookup"><span data-stu-id="4b20d-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="4b20d-150">Value</span><span class="sxs-lookup"><span data-stu-id="4b20d-150">Value</span></span>|<span data-ttu-id="4b20d-151">Popis</span><span class="sxs-lookup"><span data-stu-id="4b20d-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4b20d-152">Výčet</span><span class="sxs-lookup"><span data-stu-id="4b20d-152">Enumeration</span></span>|<span data-ttu-id="4b20d-153">Mezi hodnoty patří: Adresáře, AuthRoot, CertificateAuthority zakázané, My, Root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="4b20d-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b20d-154">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4b20d-154">Child Elements</span></span>  
 <span data-ttu-id="4b20d-155">Žádné</span><span class="sxs-lookup"><span data-stu-id="4b20d-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b20d-156">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4b20d-156">Parent Elements</span></span>  
  
|<span data-ttu-id="4b20d-157">Prvek</span><span class="sxs-lookup"><span data-stu-id="4b20d-157">Element</span></span>|<span data-ttu-id="4b20d-158">Popis</span><span class="sxs-lookup"><span data-stu-id="4b20d-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b20d-159">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="4b20d-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="4b20d-160">Představuje kolekci certifikátů X.509 poskytnuty konkrétní službou pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="4b20d-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b20d-161">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b20d-161">Remarks</span></span>  
 <span data-ttu-id="4b20d-162">Tento prvek umožňuje klientovi konfigurace certifikátu služby k použití na základě adresy URL služby, se kterým komunikuje.</span><span class="sxs-lookup"><span data-stu-id="4b20d-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="4b20d-163">To je zvláště užitečná v vydaný token situacích, kdy může klient komunikovat k více službám (ukončení služby také služby tokenu zabezpečení zprostředkující).</span><span class="sxs-lookup"><span data-stu-id="4b20d-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="4b20d-164">U vazeb, které používají zabezpečení na základě certifikátů zpráv tento certifikát se používá k šifrování zpráv ve službě a očekává se využívat službu k podepisování odpovědi klientovi.</span><span class="sxs-lookup"><span data-stu-id="4b20d-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="4b20d-165">Pokud vazba vyžaduje certifikát pro službu a žádné konkrétní certifikát pro službu, kterou adresy URL se nachází v ScopedCertificates, použije se výchozí certifikát.</span><span class="sxs-lookup"><span data-stu-id="4b20d-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="4b20d-166">Další informace najdete v části "Obor certifikáty" v [jak: Vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="4b20d-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b20d-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b20d-167">Example</span></span>  
 <span data-ttu-id="4b20d-168">Následující příklad přidá certifikát X.509 do kolekce.</span><span class="sxs-lookup"><span data-stu-id="4b20d-168">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4b20d-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b20d-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="4b20d-170">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="4b20d-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="4b20d-171">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="4b20d-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="4b20d-172">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="4b20d-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="4b20d-173">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4b20d-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
