---
title: <serviceCertificate><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: a3013d0f7efd3014892cf6400447d708809c5fcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936339"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="3b160-102">\<serviceCertificate > \<elementu ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="3b160-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="3b160-103">Určuje certifikát, který se má použít při ověřování služby pro klienta.</span><span class="sxs-lookup"><span data-stu-id="3b160-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="3b160-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3b160-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3b160-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="3b160-105">\<behaviors></span></span>  
<span data-ttu-id="3b160-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="3b160-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="3b160-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="3b160-107">\<behavior></span></span>  
<span data-ttu-id="3b160-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="3b160-108">\<clientCredentials></span></span>  
<span data-ttu-id="3b160-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="3b160-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b160-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b160-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b160-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3b160-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3b160-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3b160-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b160-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="3b160-113">Attributes</span></span>  
 <span data-ttu-id="3b160-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="3b160-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3b160-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3b160-115">Child Elements</span></span>  
  
|<span data-ttu-id="3b160-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="3b160-116">Element</span></span>|<span data-ttu-id="3b160-117">Popis</span><span class="sxs-lookup"><span data-stu-id="3b160-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b160-118">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="3b160-118">\<defaultCertificate></span></span>](defaultcertificate-element.md)|<span data-ttu-id="3b160-119">Určuje certifikát X. 509, který se použije, když služba nebo STS neposkytne protokol pro vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="3b160-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="3b160-120">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="3b160-120">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="3b160-121">Představuje kolekci certifikátů X. 509 poskytovaných konkrétními službami (vymezenými) pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="3b160-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="3b160-122">Tato kolekce se obvykle používá k určení certifikátů služby pro služby tokenů zabezpečení ve federovaném scénáři.</span><span class="sxs-lookup"><span data-stu-id="3b160-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="3b160-123">\<> ověřování</span><span class="sxs-lookup"><span data-stu-id="3b160-123">\<authentication></span></span>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="3b160-124">Určuje chování ověřování pro certifikáty služeb používané klientem.</span><span class="sxs-lookup"><span data-stu-id="3b160-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b160-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3b160-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3b160-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="3b160-126">Element</span></span>|<span data-ttu-id="3b160-127">Popis</span><span class="sxs-lookup"><span data-stu-id="3b160-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b160-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="3b160-128">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="3b160-129">Určuje přihlašovací údaje, které klient používá k ověření samotné služby.</span><span class="sxs-lookup"><span data-stu-id="3b160-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b160-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b160-130">Remarks</span></span>  
 <span data-ttu-id="3b160-131">Tento prvek konfigurace určuje nastavení, pomocí kterých klient ověří certifikát prezentovaný službou pomocí ověřování SSL.</span><span class="sxs-lookup"><span data-stu-id="3b160-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="3b160-132">Obsahuje taky všechny certifikáty pro službu, která je explicitně nakonfigurovaná na straně klienta, aby se mohla používat k šifrování zpráv do služby pomocí zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="3b160-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="3b160-133">Atributy `serviceCertificate` prvku jsou stejné jako atributy [ \<> ClientCertificate](clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="3b160-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b160-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b160-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="3b160-135">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3b160-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3b160-136">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="3b160-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="3b160-137">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="3b160-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3b160-138">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3b160-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
