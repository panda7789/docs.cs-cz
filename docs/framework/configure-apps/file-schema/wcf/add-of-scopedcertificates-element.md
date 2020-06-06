---
title: <add><scopedCertificates>elementu
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: b00a342108beca69a906fbf6212915768e98778f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398348"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="c3357-102">\<add>\<scopedCertificates>elementu</span><span class="sxs-lookup"><span data-stu-id="c3357-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="c3357-103">Přidá certifikát X. 509 do kolekce certifikátů s vymezeným oborem.</span><span class="sxs-lookup"><span data-stu-id="c3357-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="c3357-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3357-104">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3357-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c3357-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c3357-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c3357-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3357-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="c3357-107">Attributes</span></span>  
  
|<span data-ttu-id="c3357-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="c3357-108">Attribute</span></span>|<span data-ttu-id="c3357-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c3357-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3357-110">targetUri</span><span class="sxs-lookup"><span data-stu-id="c3357-110">targetUri</span></span>|<span data-ttu-id="c3357-111">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="c3357-111">String.</span></span> <span data-ttu-id="c3357-112">Určuje identifikátor URI služby přidružené k certifikátu.</span><span class="sxs-lookup"><span data-stu-id="c3357-112">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="c3357-113">findValue</span><span class="sxs-lookup"><span data-stu-id="c3357-113">findValue</span></span>|<span data-ttu-id="c3357-114">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="c3357-114">String.</span></span> <span data-ttu-id="c3357-115">Hodnota, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="c3357-115">The value to search for.</span></span>|  
|<span data-ttu-id="c3357-116">x509FindType</span><span class="sxs-lookup"><span data-stu-id="c3357-116">x509FindType</span></span>|<span data-ttu-id="c3357-117">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="c3357-117">Enumeration.</span></span> <span data-ttu-id="c3357-118">Jedno z polí certifikátu, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="c3357-118">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="c3357-119">storeLocation</span><span class="sxs-lookup"><span data-stu-id="c3357-119">storeLocation</span></span>|<span data-ttu-id="c3357-120">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="c3357-120">Enumeration.</span></span> <span data-ttu-id="c3357-121">Jedno ze dvou umístění úložiště, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="c3357-121">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="c3357-122">storeName</span><span class="sxs-lookup"><span data-stu-id="c3357-122">storeName</span></span>|<span data-ttu-id="c3357-123">Enumeration.</span><span class="sxs-lookup"><span data-stu-id="c3357-123">Enumeration.</span></span> <span data-ttu-id="c3357-124">Jedno ze systémových úložišť, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="c3357-124">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="c3357-125">findValue – atribut</span><span class="sxs-lookup"><span data-stu-id="c3357-125">findValue Attribute</span></span>  
  
|<span data-ttu-id="c3357-126">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c3357-126">Value</span></span>|<span data-ttu-id="c3357-127">Description</span><span class="sxs-lookup"><span data-stu-id="c3357-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c3357-128">Řetězec</span><span class="sxs-lookup"><span data-stu-id="c3357-128">String</span></span>|<span data-ttu-id="c3357-129">Hodnota závisí na poli (určené atributem X509FindType), který je prohledáván.</span><span class="sxs-lookup"><span data-stu-id="c3357-129">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="c3357-130">Například pokud hledáte kryptografický otisk, hodnota musí být řetězec hexadecimálních čísel.</span><span class="sxs-lookup"><span data-stu-id="c3357-130">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="c3357-131">x509FindType – atribut</span><span class="sxs-lookup"><span data-stu-id="c3357-131">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="c3357-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c3357-132">Value</span></span>|<span data-ttu-id="c3357-133">Description</span><span class="sxs-lookup"><span data-stu-id="c3357-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c3357-134">Výčet</span><span class="sxs-lookup"><span data-stu-id="c3357-134">Enumeration</span></span>|<span data-ttu-id="c3357-135">Mezi hodnoty patří: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="c3357-135">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="c3357-136">storeLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="c3357-136">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="c3357-137">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c3357-137">Value</span></span>|<span data-ttu-id="c3357-138">Description</span><span class="sxs-lookup"><span data-stu-id="c3357-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c3357-139">Výčet</span><span class="sxs-lookup"><span data-stu-id="c3357-139">Enumeration</span></span>|<span data-ttu-id="c3357-140">CurrentUser nebo LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c3357-140">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="c3357-141">storeName – atribut</span><span class="sxs-lookup"><span data-stu-id="c3357-141">storeName Attribute</span></span>  
  
|<span data-ttu-id="c3357-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c3357-142">Value</span></span>|<span data-ttu-id="c3357-143">Description</span><span class="sxs-lookup"><span data-stu-id="c3357-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c3357-144">Výčet</span><span class="sxs-lookup"><span data-stu-id="c3357-144">Enumeration</span></span>|<span data-ttu-id="c3357-145">Mezi hodnoty patří: AddressBook, AuthRoot, CertificateAuthority, Nepovoleno, my, root, TrustedPeople a TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="c3357-145">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3357-146">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c3357-146">Child Elements</span></span>  
 <span data-ttu-id="c3357-147">Žádné</span><span class="sxs-lookup"><span data-stu-id="c3357-147">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3357-148">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c3357-148">Parent Elements</span></span>  
  
|<span data-ttu-id="c3357-149">Prvek</span><span class="sxs-lookup"><span data-stu-id="c3357-149">Element</span></span>|<span data-ttu-id="c3357-150">Description</span><span class="sxs-lookup"><span data-stu-id="c3357-150">Description</span></span>|  
|-------------|-----------------|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="c3357-151">Představuje kolekci certifikátů X. 509 poskytovaných konkrétními službami (vymezenými) pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="c3357-151">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3357-152">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3357-152">Remarks</span></span>  
 <span data-ttu-id="c3357-153">Tento prvek umožňuje klientovi nakonfigurovat certifikát služby tak, aby se použil na základě adresy URL služby, se kterou komunikuje.</span><span class="sxs-lookup"><span data-stu-id="c3357-153">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="c3357-154">To je užitečné hlavně ve scénářích vydaných tokenů, kde klient může komunikovat s více službami (koncová služba i zprostředkující služba tokenů zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="c3357-154">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="c3357-155">U vazeb, které používají zabezpečení zpráv založených na certifikátech, se tento certifikát používá k šifrování zpráv do služby a očekává se, že služba bude službu používat k podepisování odpovědí klientovi.</span><span class="sxs-lookup"><span data-stu-id="c3357-155">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="c3357-156">Pokud vazba vyžaduje certifikát pro službu a v ScopedCertificates se nenajde žádný konkrétní certifikát pro adresu URL služby, použije se výchozí certifikát.</span><span class="sxs-lookup"><span data-stu-id="c3357-156">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="c3357-157">Další informace najdete v části "vymezené certifikáty" v tématu [Postupy: vytvoření federovaného klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="c3357-157">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3357-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3357-158">Example</span></span>  
 <span data-ttu-id="c3357-159">Následující příklad přidá do kolekce certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="c3357-159">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3357-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3357-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="c3357-161">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="c3357-161">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="c3357-162">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="c3357-162">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c3357-163">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="c3357-163">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c3357-164">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c3357-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
