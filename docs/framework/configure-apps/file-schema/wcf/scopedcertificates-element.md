---
title: Element <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 73e78a6ca27ed45e1eadc7121987b75f79bc6aa5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145197"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="12494-102">\<scopedCertificates > – Element</span><span class="sxs-lookup"><span data-stu-id="12494-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="12494-103">Představuje kolekci certifikátů X.509 poskytnuty konkrétní službou pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="12494-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="12494-104">Tato kolekce se obvykle používá k určení certifikáty služeb pro služby tokenu zabezpečení v případě federovaných.</span><span class="sxs-lookup"><span data-stu-id="12494-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="12494-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="12494-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="12494-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="12494-106">\<behaviors></span></span>  
<span data-ttu-id="12494-107">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="12494-107">endpointBehaviors section</span></span>  
<span data-ttu-id="12494-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="12494-108">\<behavior></span></span>  
<span data-ttu-id="12494-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="12494-109">\<clientCredentials></span></span>  
<span data-ttu-id="12494-110">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="12494-110">\<serviceCertificate></span></span>  
<span data-ttu-id="12494-111">\<scopedCertificates > – Element</span><span class="sxs-lookup"><span data-stu-id="12494-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="12494-112">\<Přidat > – element pro \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="12494-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12494-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12494-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12494-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="12494-114">Attributes and Elements</span></span>  
 <span data-ttu-id="12494-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="12494-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12494-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="12494-116">Attributes</span></span>  
 <span data-ttu-id="12494-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="12494-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="12494-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="12494-118">Child Elements</span></span>  
  
|<span data-ttu-id="12494-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="12494-119">Element</span></span>|<span data-ttu-id="12494-120">Popis</span><span class="sxs-lookup"><span data-stu-id="12494-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12494-121">\<add></span><span class="sxs-lookup"><span data-stu-id="12494-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|<span data-ttu-id="12494-122">Přidá certifikát X.509 do kolekce vymezených certifikátů.</span><span class="sxs-lookup"><span data-stu-id="12494-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12494-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="12494-123">Parent Elements</span></span>  
  
|<span data-ttu-id="12494-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="12494-124">Element</span></span>|<span data-ttu-id="12494-125">Popis</span><span class="sxs-lookup"><span data-stu-id="12494-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12494-126">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="12494-126">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="12494-127">Určuje certifikát používaný při ověřování služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="12494-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12494-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12494-128">Remarks</span></span>  
 <span data-ttu-id="12494-129">Tato kolekce umožňuje klientovi nakonfigurovat certifikáty služby, které budou používat na základě adresy URL služby, se kterým komunikuje.</span><span class="sxs-lookup"><span data-stu-id="12494-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="12494-130">To je zvláště užitečná v vydaný token situacích, kdy může klient komunikovat k více službám (ukončení služby také služby tokenu zabezpečení zprostředkující).</span><span class="sxs-lookup"><span data-stu-id="12494-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="12494-131">U vazeb, které používají zabezpečení na základě certifikátů zpráv tento certifikát se používá k šifrování zpráv ve službě a očekává se využívat službu k podepisování odpovědi klientovi.</span><span class="sxs-lookup"><span data-stu-id="12494-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="12494-132">Pokud vazba vyžaduje certifikát pro službu a žádné konkrétní certifikát pro službu, kterou adresy URL se nachází v ScopedCertificates, použije se výchozí certifikát.</span><span class="sxs-lookup"><span data-stu-id="12494-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="12494-133">Další informace najdete v části "Obor certifikáty" v [jak: Vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="12494-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="12494-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="12494-134">Example</span></span>  
 <span data-ttu-id="12494-135">Následující příklad určuje certifikátu služby pro klienta pro použití při komunikaci s koncovými body, jejichž název domény je `http://www.contoso.com` přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="12494-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12494-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12494-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="12494-137">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="12494-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="12494-138">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="12494-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="12494-139">\<add></span><span class="sxs-lookup"><span data-stu-id="12494-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)
- [<span data-ttu-id="12494-140">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="12494-140">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="12494-141">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="12494-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
