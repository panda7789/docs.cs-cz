---
title: Element &lt;scopedCertificates&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cb1d536d25186dd2d75cec962143b16cdd45260
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltscopedcertificatesgt-element"></a><span data-ttu-id="bb4b7-102">Element &lt;scopedCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="bb4b7-102">&lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="bb4b7-103">Představuje kolekci certifikáty X.509, které jsou součástí konkrétní služby (obor) pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="bb4b7-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="bb4b7-104">Tato kolekce se obvykle používá k určení certifikáty služby pro služby tokenů zabezpečení ve scénáři federované.</span><span class="sxs-lookup"><span data-stu-id="bb4b7-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="bb4b7-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bb4b7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="bb4b7-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bb4b7-106">\<behaviors></span></span>  
<span data-ttu-id="bb4b7-107">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="bb4b7-107">endpointBehaviors section</span></span>  
<span data-ttu-id="bb4b7-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bb4b7-108">\<behavior></span></span>  
<span data-ttu-id="bb4b7-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="bb4b7-109">\<clientCredentials></span></span>  
<span data-ttu-id="bb4b7-110">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="bb4b7-110">\<serviceCertificate></span></span>  
<span data-ttu-id="bb4b7-111">\<scopedCertificates > elementu</span><span class="sxs-lookup"><span data-stu-id="bb4b7-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="bb4b7-112">\<Přidat > elementu pro \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="bb4b7-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb4b7-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb4b7-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>  
      <add findValue="String"  
                storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                targetUri="string"  
            x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />   
</scopedCertificates>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb4b7-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bb4b7-114">Attributes and Elements</span></span>  
 <span data-ttu-id="bb4b7-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bb4b7-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb4b7-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="bb4b7-116">Attributes</span></span>  
 <span data-ttu-id="bb4b7-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="bb4b7-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bb4b7-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bb4b7-118">Child Elements</span></span>  
  
|<span data-ttu-id="bb4b7-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="bb4b7-119">Element</span></span>|<span data-ttu-id="bb4b7-120">Popis</span><span class="sxs-lookup"><span data-stu-id="bb4b7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb4b7-121">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="bb4b7-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|<span data-ttu-id="bb4b7-122">Přidá do kolekce vymezená certifikátů certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="bb4b7-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bb4b7-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bb4b7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bb4b7-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="bb4b7-124">Element</span></span>|<span data-ttu-id="bb4b7-125">Popis</span><span class="sxs-lookup"><span data-stu-id="bb4b7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb4b7-126">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="bb4b7-126">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="bb4b7-127">Určuje certifikát pro použití při ověřování služby klienta.</span><span class="sxs-lookup"><span data-stu-id="bb4b7-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb4b7-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb4b7-128">Remarks</span></span>  
 <span data-ttu-id="bb4b7-129">Tato kolekce umožňuje klientovi ke konfiguraci služby certifikáty, které budou používat založené na adresu URL služby, kterým komunikuje.</span><span class="sxs-lookup"><span data-stu-id="bb4b7-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="bb4b7-130">To je zvlášť užitečné v vydaných tokenů scénáře, kde může klient komunikovat na více služeb (na koncové služby a také služeb tokenu zprostředkující zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="bb4b7-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="bb4b7-131">U vazeb, které používají zabezpečení zpráv pomocí certifikátů tento certifikát se používá k šifrování zpráv do služby a očekává se použije pro podepisování odpovědi klientovi službou.</span><span class="sxs-lookup"><span data-stu-id="bb4b7-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="bb4b7-132">Pokud vazba vyžaduje certifikát pro službu a žádný konkrétní certifikát pro službu, kterou adresu URL se nachází v ScopedCertificates, použije se výchozí certifikát.</span><span class="sxs-lookup"><span data-stu-id="bb4b7-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="bb4b7-133">Další informace najdete v části "Obor certifikáty" z [postupy: vytvoření federovaného klienta](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="bb4b7-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb4b7-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb4b7-134">Example</span></span>  
 <span data-ttu-id="bb4b7-135">Následující příklad určuje certifikát služby pro klienta pro použití při komunikaci s koncovými body, jejichž název domény je http://www.contoso.com přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="bb4b7-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is http://www.contoso.com over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb4b7-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb4b7-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="bb4b7-137">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="bb4b7-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="bb4b7-138">Postupy: vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="bb4b7-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="bb4b7-139">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="bb4b7-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)  
 [<span data-ttu-id="bb4b7-140">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="bb4b7-140">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="bb4b7-141">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="bb4b7-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
