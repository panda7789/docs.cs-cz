---
title: <serviceCertificate><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4c7489a171bdd5cb4b747ca99f1b7ff6dd65517b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399683"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="05f7b-102">\<serviceCertificate > \<elementu ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="05f7b-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="05f7b-103">Určuje certifikát, který se má použít při ověřování služby pro klienta.</span><span class="sxs-lookup"><span data-stu-id="05f7b-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
<span data-ttu-id="05f7b-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="05f7b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="05f7b-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="05f7b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="05f7b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="05f7b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="05f7b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="05f7b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="05f7b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="05f7b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="05f7b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="05f7b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="05f7b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCertificate >**</span><span class="sxs-lookup"><span data-stu-id="05f7b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05f7b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05f7b-111">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05f7b-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="05f7b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="05f7b-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="05f7b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05f7b-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="05f7b-114">Attributes</span></span>  
 <span data-ttu-id="05f7b-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="05f7b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05f7b-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="05f7b-116">Child Elements</span></span>  
  
|<span data-ttu-id="05f7b-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="05f7b-117">Element</span></span>|<span data-ttu-id="05f7b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="05f7b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05f7b-119">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="05f7b-119">\<defaultCertificate></span></span>](defaultcertificate-element.md)|<span data-ttu-id="05f7b-120">Určuje certifikát X. 509, který se použije, když služba nebo STS neposkytne protokol pro vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="05f7b-120">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="05f7b-121">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="05f7b-121">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="05f7b-122">Představuje kolekci certifikátů X. 509 poskytovaných konkrétními službami (vymezenými) pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="05f7b-122">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="05f7b-123">Tato kolekce se obvykle používá k určení certifikátů služby pro služby tokenů zabezpečení ve federovaném scénáři.</span><span class="sxs-lookup"><span data-stu-id="05f7b-123">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="05f7b-124">\<> ověřování</span><span class="sxs-lookup"><span data-stu-id="05f7b-124">\<authentication></span></span>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="05f7b-125">Určuje chování ověřování pro certifikáty služeb používané klientem.</span><span class="sxs-lookup"><span data-stu-id="05f7b-125">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05f7b-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="05f7b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="05f7b-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="05f7b-127">Element</span></span>|<span data-ttu-id="05f7b-128">Popis</span><span class="sxs-lookup"><span data-stu-id="05f7b-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05f7b-129">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="05f7b-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="05f7b-130">Určuje přihlašovací údaje, které klient používá k ověření samotné služby.</span><span class="sxs-lookup"><span data-stu-id="05f7b-130">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05f7b-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05f7b-131">Remarks</span></span>  
 <span data-ttu-id="05f7b-132">Tento prvek konfigurace určuje nastavení, pomocí kterých klient ověří certifikát prezentovaný službou pomocí ověřování SSL.</span><span class="sxs-lookup"><span data-stu-id="05f7b-132">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="05f7b-133">Obsahuje taky všechny certifikáty pro službu, která je explicitně nakonfigurovaná na straně klienta, aby se mohla používat k šifrování zpráv do služby pomocí zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="05f7b-133">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="05f7b-134">Atributy `serviceCertificate` prvku jsou stejné jako atributy [ \<> ClientCertificate](clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="05f7b-134">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f7b-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05f7b-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="05f7b-136">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="05f7b-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="05f7b-137">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="05f7b-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="05f7b-138">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="05f7b-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="05f7b-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="05f7b-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
