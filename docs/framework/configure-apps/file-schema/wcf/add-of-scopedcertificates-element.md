---
title: '&lt;add&gt; elementu &lt;scopedCertificates&gt;'
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: a173d3b137833abfe8a69aed55b972c9b6469890
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146092"
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a><span data-ttu-id="aabc8-102">&lt;add&gt; elementu &lt;scopedCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="aabc8-102">&lt;add&gt; of &lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="aabc8-103">Přidá certifikát X.509 do kolekce vymezených certifikátů.</span><span class="sxs-lookup"><span data-stu-id="aabc8-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="aabc8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="aabc8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="aabc8-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="aabc8-105">\<behaviors></span></span>  
<span data-ttu-id="aabc8-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="aabc8-106">endpointBehaviors section</span></span>  
<span data-ttu-id="aabc8-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="aabc8-107">\<behavior></span></span>  
<span data-ttu-id="aabc8-108">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="aabc8-108">\<clientCredentials></span></span>  
<span data-ttu-id="aabc8-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="aabc8-109">\<serviceCertificate></span></span>  
<span data-ttu-id="aabc8-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="aabc8-110">\<scopedCertificates></span></span>  
<span data-ttu-id="aabc8-111">\<Přidat > – element pro \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="aabc8-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aabc8-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aabc8-112">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aabc8-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aabc8-113">Attributes and Elements</span></span>  
 <span data-ttu-id="aabc8-114">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aabc8-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aabc8-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="aabc8-115">Attributes</span></span>  
  
|<span data-ttu-id="aabc8-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="aabc8-116">Attribute</span></span>|<span data-ttu-id="aabc8-117">Popis</span><span class="sxs-lookup"><span data-stu-id="aabc8-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aabc8-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="aabc8-118">targetUri</span></span>|<span data-ttu-id="aabc8-119">řetězec.</span><span class="sxs-lookup"><span data-stu-id="aabc8-119">String.</span></span> <span data-ttu-id="aabc8-120">Určuje identifikátor URI služby přidruženého k certifikátu.</span><span class="sxs-lookup"><span data-stu-id="aabc8-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="aabc8-121">findValue</span><span class="sxs-lookup"><span data-stu-id="aabc8-121">findValue</span></span>|<span data-ttu-id="aabc8-122">řetězec.</span><span class="sxs-lookup"><span data-stu-id="aabc8-122">String.</span></span> <span data-ttu-id="aabc8-123">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="aabc8-123">The value to search for.</span></span>|  
|<span data-ttu-id="aabc8-124">X509FindType</span><span class="sxs-lookup"><span data-stu-id="aabc8-124">x509FindType</span></span>|<span data-ttu-id="aabc8-125">Výčet.</span><span class="sxs-lookup"><span data-stu-id="aabc8-125">Enumeration.</span></span> <span data-ttu-id="aabc8-126">Jeden z pole certifikátu k prohledání.</span><span class="sxs-lookup"><span data-stu-id="aabc8-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="aabc8-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="aabc8-127">storeLocation</span></span>|<span data-ttu-id="aabc8-128">Výčet.</span><span class="sxs-lookup"><span data-stu-id="aabc8-128">Enumeration.</span></span> <span data-ttu-id="aabc8-129">Jedno ze dvou umístění úložišť k prohledání.</span><span class="sxs-lookup"><span data-stu-id="aabc8-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="aabc8-130">storeName</span><span class="sxs-lookup"><span data-stu-id="aabc8-130">storeName</span></span>|<span data-ttu-id="aabc8-131">Výčet.</span><span class="sxs-lookup"><span data-stu-id="aabc8-131">Enumeration.</span></span> <span data-ttu-id="aabc8-132">Jedno ze systémových úložišť k prohledání.</span><span class="sxs-lookup"><span data-stu-id="aabc8-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="aabc8-133">findValue atribut</span><span class="sxs-lookup"><span data-stu-id="aabc8-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="aabc8-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="aabc8-134">Value</span></span>|<span data-ttu-id="aabc8-135">Popis</span><span class="sxs-lookup"><span data-stu-id="aabc8-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aabc8-136">String</span><span class="sxs-lookup"><span data-stu-id="aabc8-136">String</span></span>|<span data-ttu-id="aabc8-137">Hodnota závisí na poli (určenému atributem X509FindType) být vyhledán.</span><span class="sxs-lookup"><span data-stu-id="aabc8-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="aabc8-138">Například pokud hledání kryptografickým otiskem, hodnota musí být řetězec šestnáctkových čísel.</span><span class="sxs-lookup"><span data-stu-id="aabc8-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="aabc8-139">Atribut x509FindType</span><span class="sxs-lookup"><span data-stu-id="aabc8-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="aabc8-140">Hodnota</span><span class="sxs-lookup"><span data-stu-id="aabc8-140">Value</span></span>|<span data-ttu-id="aabc8-141">Popis</span><span class="sxs-lookup"><span data-stu-id="aabc8-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aabc8-142">Výčet</span><span class="sxs-lookup"><span data-stu-id="aabc8-142">Enumeration</span></span>|<span data-ttu-id="aabc8-143">Mezi hodnoty patří: FindByThumbprint FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="aabc8-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="aabc8-144">storeLocation atribut</span><span class="sxs-lookup"><span data-stu-id="aabc8-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="aabc8-145">Hodnota</span><span class="sxs-lookup"><span data-stu-id="aabc8-145">Value</span></span>|<span data-ttu-id="aabc8-146">Popis</span><span class="sxs-lookup"><span data-stu-id="aabc8-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aabc8-147">Výčet</span><span class="sxs-lookup"><span data-stu-id="aabc8-147">Enumeration</span></span>|<span data-ttu-id="aabc8-148">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="aabc8-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="aabc8-149">storeName atribut</span><span class="sxs-lookup"><span data-stu-id="aabc8-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="aabc8-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="aabc8-150">Value</span></span>|<span data-ttu-id="aabc8-151">Popis</span><span class="sxs-lookup"><span data-stu-id="aabc8-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aabc8-152">Výčet</span><span class="sxs-lookup"><span data-stu-id="aabc8-152">Enumeration</span></span>|<span data-ttu-id="aabc8-153">Mezi hodnoty patří: Adresáře, AuthRoot, CertificateAuthority zakázané, My, Root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="aabc8-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aabc8-154">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aabc8-154">Child Elements</span></span>  
 <span data-ttu-id="aabc8-155">Žádné</span><span class="sxs-lookup"><span data-stu-id="aabc8-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aabc8-156">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aabc8-156">Parent Elements</span></span>  
  
|<span data-ttu-id="aabc8-157">Prvek</span><span class="sxs-lookup"><span data-stu-id="aabc8-157">Element</span></span>|<span data-ttu-id="aabc8-158">Popis</span><span class="sxs-lookup"><span data-stu-id="aabc8-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aabc8-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="aabc8-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="aabc8-160">Představuje kolekci certifikátů X.509 poskytnuty konkrétní službou pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="aabc8-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aabc8-161">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aabc8-161">Remarks</span></span>  
 <span data-ttu-id="aabc8-162">Tento prvek umožňuje klientovi konfigurace certifikátu služby k použití na základě adresy URL služby, se kterým komunikuje.</span><span class="sxs-lookup"><span data-stu-id="aabc8-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="aabc8-163">To je zvláště užitečná v vydaný token situacích, kdy může klient komunikovat k více službám (ukončení služby také služby tokenu zabezpečení zprostředkující).</span><span class="sxs-lookup"><span data-stu-id="aabc8-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="aabc8-164">U vazeb, které používají zabezpečení na základě certifikátů zpráv tento certifikát se používá k šifrování zpráv ve službě a očekává se využívat službu k podepisování odpovědi klientovi.</span><span class="sxs-lookup"><span data-stu-id="aabc8-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="aabc8-165">Pokud vazba vyžaduje certifikát pro službu a žádné konkrétní certifikát pro službu, kterou adresy URL se nachází v ScopedCertificates, použije se výchozí certifikát.</span><span class="sxs-lookup"><span data-stu-id="aabc8-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="aabc8-166">Další informace najdete v části "Obor certifikáty" v [jak: Vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="aabc8-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aabc8-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="aabc8-167">Example</span></span>  
 <span data-ttu-id="aabc8-168">Následující příklad přidá certifikát X.509 do kolekce.</span><span class="sxs-lookup"><span data-stu-id="aabc8-168">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aabc8-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="aabc8-169">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="aabc8-170">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="aabc8-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="aabc8-171">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="aabc8-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="aabc8-172">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="aabc8-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="aabc8-173">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="aabc8-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
