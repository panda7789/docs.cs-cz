---
title: <serviceCertificate> z <clientCredentials> – Element
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 7134e8b3d253575bf26f26490372aa94549c73b7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279679"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="6a602-102">\<serviceCertificate > z \<clientCredentials > – Element</span><span class="sxs-lookup"><span data-stu-id="6a602-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="6a602-103">Určuje certifikát používaný při ověřování služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="6a602-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="6a602-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6a602-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6a602-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="6a602-105">\<behaviors></span></span>  
<span data-ttu-id="6a602-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="6a602-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="6a602-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="6a602-107">\<behavior></span></span>  
<span data-ttu-id="6a602-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="6a602-108">\<clientCredentials></span></span>  
<span data-ttu-id="6a602-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="6a602-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a602-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a602-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a602-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6a602-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6a602-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6a602-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a602-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="6a602-113">Attributes</span></span>  
 <span data-ttu-id="6a602-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="6a602-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6a602-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6a602-115">Child Elements</span></span>  
  
|<span data-ttu-id="6a602-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="6a602-116">Element</span></span>|<span data-ttu-id="6a602-117">Popis</span><span class="sxs-lookup"><span data-stu-id="6a602-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a602-118">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="6a602-118">\<defaultCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|<span data-ttu-id="6a602-119">Určuje certifikát X.509, který se má použít při služba nebo STS neposkytne pomocí protokolu vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="6a602-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="6a602-120">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="6a602-120">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="6a602-121">Představuje kolekci certifikátů X.509 poskytnuty konkrétní službou pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="6a602-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="6a602-122">Tato kolekce se obvykle používá k určení certifikáty služeb pro služby tokenu zabezpečení v případě federovaných.</span><span class="sxs-lookup"><span data-stu-id="6a602-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="6a602-123">\<authentication></span><span class="sxs-lookup"><span data-stu-id="6a602-123">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|<span data-ttu-id="6a602-124">Určuje chování ověřování pro klientem používané certifikáty služeb.</span><span class="sxs-lookup"><span data-stu-id="6a602-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a602-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6a602-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6a602-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="6a602-126">Element</span></span>|<span data-ttu-id="6a602-127">Popis</span><span class="sxs-lookup"><span data-stu-id="6a602-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a602-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="6a602-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="6a602-129">Určuje pověření, která používá klient ke svému ověření ke službě.</span><span class="sxs-lookup"><span data-stu-id="6a602-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a602-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a602-130">Remarks</span></span>  
 <span data-ttu-id="6a602-131">Tento prvek konfigurace určuje nastavení klient ověřit certifikát předložený službou pomocí ověřování protokolem SSL.</span><span class="sxs-lookup"><span data-stu-id="6a602-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="6a602-132">Obsahuje také jakýkoliv certifikát pro službu, která je explicitně nakonfigurovaná na straně klienta má použít k zašifrování zprávy do služby pomocí zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="6a602-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="6a602-133">Atributy `serviceCertificate` jsou stejné jako atributy elementu [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="6a602-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a602-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a602-134">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="6a602-135">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6a602-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6a602-136">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="6a602-136">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="6a602-137">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="6a602-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="6a602-138">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6a602-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
