---
title: Element <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 3c06159709df0afe2a475de1e186b0114af32bc2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399957"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="bbb4a-102">\<scopedCertificates – element ></span><span class="sxs-lookup"><span data-stu-id="bbb4a-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="bbb4a-103">Představuje kolekci certifikátů X. 509 poskytovaných konkrétními službami (vymezenými) pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="bbb4a-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="bbb4a-104">Tato kolekce se obvykle používá k určení certifikátů služby pro služby tokenů zabezpečení ve federovaném scénáři.</span><span class="sxs-lookup"><span data-stu-id="bbb4a-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
<span data-ttu-id="bbb4a-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bbb4a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bbb4a-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bbb4a-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bbb4a-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bbb4a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bbb4a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bbb4a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="bbb4a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bbb4a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="bbb4a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="bbb4a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="bbb4a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="bbb4a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="bbb4a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<scopedCertificates >**</span><span class="sxs-lookup"><span data-stu-id="bbb4a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbb4a-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbb4a-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbb4a-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bbb4a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="bbb4a-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bbb4a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbb4a-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="bbb4a-116">Attributes</span></span>  
 <span data-ttu-id="bbb4a-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="bbb4a-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bbb4a-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bbb4a-118">Child Elements</span></span>  
  
|<span data-ttu-id="bbb4a-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="bbb4a-119">Element</span></span>|<span data-ttu-id="bbb4a-120">Popis</span><span class="sxs-lookup"><span data-stu-id="bbb4a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbb4a-121">\<add></span><span class="sxs-lookup"><span data-stu-id="bbb4a-121">\<add></span></span>](add-of-scopedcertificates-element.md)|<span data-ttu-id="bbb4a-122">Přidá certifikát X. 509 do kolekce certifikátů s vymezeným oborem.</span><span class="sxs-lookup"><span data-stu-id="bbb4a-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bbb4a-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bbb4a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bbb4a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="bbb4a-124">Element</span></span>|<span data-ttu-id="bbb4a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="bbb4a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbb4a-126">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="bbb4a-126">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="bbb4a-127">Určuje certifikát, který se má použít při ověřování služby pro klienta.</span><span class="sxs-lookup"><span data-stu-id="bbb4a-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbb4a-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbb4a-128">Remarks</span></span>  
 <span data-ttu-id="bbb4a-129">Tato kolekce umožňuje klientovi nakonfigurovat certifikáty služby tak, aby se používaly na základě adresy URL služby, se kterou komunikuje.</span><span class="sxs-lookup"><span data-stu-id="bbb4a-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="bbb4a-130">To je užitečné hlavně ve scénářích vydaných tokenů, kde klient může komunikovat s více službami (koncová služba i zprostředkující služba tokenů zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="bbb4a-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="bbb4a-131">U vazeb, které používají zabezpečení zpráv založených na certifikátech, se tento certifikát používá k šifrování zpráv do služby a očekává se, že služba bude službu používat k podepisování odpovědí klientovi.</span><span class="sxs-lookup"><span data-stu-id="bbb4a-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="bbb4a-132">Pokud vazba vyžaduje certifikát pro službu a v ScopedCertificates se nenajde žádný konkrétní certifikát pro adresu URL služby, použije se výchozí certifikát.</span><span class="sxs-lookup"><span data-stu-id="bbb4a-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="bbb4a-133">Další informace najdete v části ["vymezené certifikáty" v tématu Postupy: Vytvoření federovaného klienta](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="bbb4a-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbb4a-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="bbb4a-134">Example</span></span>  
 <span data-ttu-id="bbb4a-135">Následující příklad určuje certifikát služby, který má klient použít při komunikaci s koncovými body, jejichž název domény `http://www.contoso.com` je přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="bbb4a-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="bbb4a-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbb4a-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="bbb4a-137">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="bbb4a-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="bbb4a-138">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="bbb4a-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="bbb4a-139">\<add></span><span class="sxs-lookup"><span data-stu-id="bbb4a-139">\<add></span></span>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="bbb4a-140">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="bbb4a-140">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="bbb4a-141">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="bbb4a-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
