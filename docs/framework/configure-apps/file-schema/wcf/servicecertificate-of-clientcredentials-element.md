---
title: '&lt;serviceCertificate&gt; elementu &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 1d54c39fd681e0686e419b7b73243703e9184d1f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="5cc65-102">&lt;serviceCertificate&gt; elementu &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="5cc65-102">&lt;serviceCertificate&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="5cc65-103">Určuje certifikát pro použití při ověřování služby klienta.</span><span class="sxs-lookup"><span data-stu-id="5cc65-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="5cc65-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5cc65-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5cc65-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5cc65-105">\<behaviors></span></span>  
<span data-ttu-id="5cc65-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5cc65-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5cc65-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5cc65-107">\<behavior></span></span>  
<span data-ttu-id="5cc65-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5cc65-108">\<clientCredentials></span></span>  
<span data-ttu-id="5cc65-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="5cc65-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc65-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cc65-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cc65-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5cc65-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5cc65-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5cc65-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cc65-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="5cc65-113">Attributes</span></span>  
 <span data-ttu-id="5cc65-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="5cc65-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5cc65-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5cc65-115">Child Elements</span></span>  
  
|<span data-ttu-id="5cc65-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="5cc65-116">Element</span></span>|<span data-ttu-id="5cc65-117">Popis</span><span class="sxs-lookup"><span data-stu-id="5cc65-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cc65-118">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="5cc65-118">\<defaultCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|<span data-ttu-id="5cc65-119">Určuje certifikát X.509, který se má použít při služby nebo služby tokenů zabezpečení neposkytuje jeden prostřednictvím vyjednávání protokolu.</span><span class="sxs-lookup"><span data-stu-id="5cc65-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="5cc65-120">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="5cc65-120">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="5cc65-121">Představuje kolekci certifikáty X.509, které jsou součástí konkrétní služby (obor) pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="5cc65-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="5cc65-122">Tato kolekce se obvykle používá k určení certifikáty služby pro služby tokenů zabezpečení ve scénáři federované.</span><span class="sxs-lookup"><span data-stu-id="5cc65-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="5cc65-123">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="5cc65-123">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|<span data-ttu-id="5cc65-124">Určuje chování ověřování pro certifikáty služby, které klient používá.</span><span class="sxs-lookup"><span data-stu-id="5cc65-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5cc65-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5cc65-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5cc65-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="5cc65-126">Element</span></span>|<span data-ttu-id="5cc65-127">Popis</span><span class="sxs-lookup"><span data-stu-id="5cc65-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cc65-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5cc65-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="5cc65-129">Určuje pověření používaná klientem k vlastnímu ověření služby.</span><span class="sxs-lookup"><span data-stu-id="5cc65-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cc65-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5cc65-130">Remarks</span></span>  
 <span data-ttu-id="5cc65-131">Tento element konfigurace určuje nastavení používaná klientem ověřit certifikát předložený služby pomocí ověřování protokolem SSL.</span><span class="sxs-lookup"><span data-stu-id="5cc65-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="5cc65-132">Obsahuje taky libovolný certifikát pro službu, která je explicitně nakonfigurovaná na straně klienta, který chcete použít pro šifrování zpráv pomocí zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="5cc65-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="5cc65-133">Atributy `serviceCertificate` element jsou stejné jako atributy [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="5cc65-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc65-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cc65-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 [<span data-ttu-id="5cc65-135">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5cc65-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="5cc65-136">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="5cc65-136">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="5cc65-137">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="5cc65-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="5cc65-138">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5cc65-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
