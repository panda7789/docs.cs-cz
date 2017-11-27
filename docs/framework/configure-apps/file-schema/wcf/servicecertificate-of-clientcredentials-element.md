---
title: '&lt;serviceCertificate&gt; elementu &lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3bd2cf4cf96fd2b80fc08523b42bd8aa2379c2d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="ddcd0-102">&lt;serviceCertificate&gt; elementu &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="ddcd0-102">&lt;serviceCertificate&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="ddcd0-103">Určuje certifikát pro použití při ověřování služby klienta.</span><span class="sxs-lookup"><span data-stu-id="ddcd0-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="ddcd0-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ddcd0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ddcd0-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ddcd0-105">\<behaviors></span></span>  
<span data-ttu-id="ddcd0-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ddcd0-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ddcd0-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ddcd0-107">\<behavior></span></span>  
<span data-ttu-id="ddcd0-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="ddcd0-108">\<clientCredentials></span></span>  
<span data-ttu-id="ddcd0-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="ddcd0-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcd0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddcd0-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddcd0-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ddcd0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ddcd0-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ddcd0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddcd0-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="ddcd0-113">Attributes</span></span>  
 <span data-ttu-id="ddcd0-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="ddcd0-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ddcd0-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ddcd0-115">Child Elements</span></span>  
  
|<span data-ttu-id="ddcd0-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="ddcd0-116">Element</span></span>|<span data-ttu-id="ddcd0-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ddcd0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddcd0-118">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="ddcd0-118">\<defaultCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|<span data-ttu-id="ddcd0-119">Určuje certifikát X.509, který se má použít při služby nebo služby tokenů zabezpečení neposkytuje jeden prostřednictvím vyjednávání protokolu.</span><span class="sxs-lookup"><span data-stu-id="ddcd0-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="ddcd0-120">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="ddcd0-120">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="ddcd0-121">Představuje kolekci certifikáty X.509, které jsou součástí konkrétní služby (obor) pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="ddcd0-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="ddcd0-122">Tato kolekce se obvykle používá k určení certifikáty služby pro služby tokenů zabezpečení ve scénáři federované.</span><span class="sxs-lookup"><span data-stu-id="ddcd0-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="ddcd0-123">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="ddcd0-123">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|<span data-ttu-id="ddcd0-124">Určuje chování ověřování pro certifikáty služby, které klient používá.</span><span class="sxs-lookup"><span data-stu-id="ddcd0-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ddcd0-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ddcd0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ddcd0-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="ddcd0-126">Element</span></span>|<span data-ttu-id="ddcd0-127">Popis</span><span class="sxs-lookup"><span data-stu-id="ddcd0-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddcd0-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="ddcd0-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="ddcd0-129">Určuje pověření používaná klientem k vlastnímu ověření služby.</span><span class="sxs-lookup"><span data-stu-id="ddcd0-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddcd0-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ddcd0-130">Remarks</span></span>  
 <span data-ttu-id="ddcd0-131">Tento element konfigurace určuje nastavení používaná klientem ověřit certifikát předložený služby pomocí ověřování protokolem SSL.</span><span class="sxs-lookup"><span data-stu-id="ddcd0-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="ddcd0-132">Obsahuje taky libovolný certifikát pro službu, která je explicitně nakonfigurovaná na straně klienta, který chcete použít pro šifrování zpráv pomocí zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="ddcd0-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="ddcd0-133">Atributy `serviceCertificate` element jsou stejné jako atributy [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="ddcd0-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcd0-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddcd0-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 [<span data-ttu-id="ddcd0-135">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ddcd0-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="ddcd0-136">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="ddcd0-136">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="ddcd0-137">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="ddcd0-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="ddcd0-138">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="ddcd0-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
