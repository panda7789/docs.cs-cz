---
title: <serviceCertificate><clientCredentials>elementu
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4c7489a171bdd5cb4b747ca99f1b7ff6dd65517b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399683"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="ab05a-102">\<serviceCertificate>\<clientCredentials>elementu</span><span class="sxs-lookup"><span data-stu-id="ab05a-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="ab05a-103">Určuje certifikát, který se má použít při ověřování služby pro klienta.</span><span class="sxs-lookup"><span data-stu-id="ab05a-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="ab05a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab05a-104">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab05a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ab05a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ab05a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ab05a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab05a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="ab05a-107">Attributes</span></span>  
 <span data-ttu-id="ab05a-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="ab05a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab05a-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ab05a-109">Child Elements</span></span>  
  
|<span data-ttu-id="ab05a-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab05a-110">Element</span></span>|<span data-ttu-id="ab05a-111">Description</span><span class="sxs-lookup"><span data-stu-id="ab05a-111">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultCertificate>](defaultcertificate-element.md)|<span data-ttu-id="ab05a-112">Určuje certifikát X. 509, který se použije, když služba nebo STS neposkytne protokol pro vyjednávání.</span><span class="sxs-lookup"><span data-stu-id="ab05a-112">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="ab05a-113">Představuje kolekci certifikátů X. 509 poskytovaných konkrétními službami (vymezenými) pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab05a-113">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="ab05a-114">Tato kolekce se obvykle používá k určení certifikátů služby pro služby tokenů zabezpečení ve federovaném scénáři.</span><span class="sxs-lookup"><span data-stu-id="ab05a-114">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[\<authentication>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="ab05a-115">Určuje chování ověřování pro certifikáty služeb používané klientem.</span><span class="sxs-lookup"><span data-stu-id="ab05a-115">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab05a-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab05a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ab05a-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab05a-117">Element</span></span>|<span data-ttu-id="ab05a-118">Description</span><span class="sxs-lookup"><span data-stu-id="ab05a-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="ab05a-119">Určuje přihlašovací údaje, které klient používá k ověření samotné služby.</span><span class="sxs-lookup"><span data-stu-id="ab05a-119">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab05a-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab05a-120">Remarks</span></span>  
 <span data-ttu-id="ab05a-121">Tento prvek konfigurace určuje nastavení, pomocí kterých klient ověří certifikát prezentovaný službou pomocí ověřování SSL.</span><span class="sxs-lookup"><span data-stu-id="ab05a-121">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="ab05a-122">Obsahuje taky všechny certifikáty pro službu, která je explicitně nakonfigurovaná na straně klienta, aby se mohla používat k šifrování zpráv do služby pomocí zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="ab05a-122">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="ab05a-123">Atributy `serviceCertificate` prvku jsou stejné jako atributy [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="ab05a-123">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab05a-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab05a-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="ab05a-125">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ab05a-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ab05a-126">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="ab05a-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="ab05a-127">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="ab05a-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ab05a-128">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="ab05a-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
