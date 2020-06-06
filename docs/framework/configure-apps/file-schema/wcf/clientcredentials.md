---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: f295fe48e194611c80b78c0c23ab3e66ea1c0b64
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400500"
---
# \<clientCredentials>
<span data-ttu-id="07905-101">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="07905-101">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="07905-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07905-102">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07905-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="07905-103">Attributes and Elements</span></span>  
 <span data-ttu-id="07905-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="07905-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07905-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="07905-105">Attributes</span></span>  
  
|<span data-ttu-id="07905-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="07905-106">Attribute</span></span>|<span data-ttu-id="07905-107">Popis</span><span class="sxs-lookup"><span data-stu-id="07905-107">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="07905-108">Logická hodnota určující, zda může být interaktivní uživatel zapojen do výběru přihlašovacích údajů klienta za běhu.</span><span class="sxs-lookup"><span data-stu-id="07905-108">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="07905-109">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="07905-109">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="07905-110">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="07905-110">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07905-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="07905-111">Child Elements</span></span>  
  
|<span data-ttu-id="07905-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="07905-112">Element</span></span>|<span data-ttu-id="07905-113">Description</span><span class="sxs-lookup"><span data-stu-id="07905-113">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="07905-114">Určuje certifikát, který se používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="07905-114">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="07905-115">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement> .</span><span class="sxs-lookup"><span data-stu-id="07905-115">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[\<httpDigest>](httpdigest-element.md)|<span data-ttu-id="07905-116">Určuje výtah, který se používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="07905-116">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="07905-117">Tento prvek je typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement> .</span><span class="sxs-lookup"><span data-stu-id="07905-117">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="07905-118">Určuje vlastní typ tokenu, který se používá k ověření klienta ke službě tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="07905-118">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="07905-119">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement> .</span><span class="sxs-lookup"><span data-stu-id="07905-119">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="07905-120">Určuje aktuální přihlašovací údaje partnerského vztahu.</span><span class="sxs-lookup"><span data-stu-id="07905-120">Specifies a current peer credential.</span></span> <span data-ttu-id="07905-121">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="07905-121">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="07905-122">Určuje certifikát použitý k ověření služby klientovi a poskytuje strukturu pro nastavení možností certifikátu.</span><span class="sxs-lookup"><span data-stu-id="07905-122">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="07905-123">Tento certifikát musí být dodán od služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="07905-123">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="07905-124">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement> .</span><span class="sxs-lookup"><span data-stu-id="07905-124">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[\<windows>](windows-of-clientcredentials-element.md)|<span data-ttu-id="07905-125">Určuje pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="07905-125">Specifies a Windows credential.</span></span> <span data-ttu-id="07905-126">Výchozí hodnota je přihlašovací údaje aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="07905-126">The default is the credential of the current thread.</span></span> <span data-ttu-id="07905-127">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsClientElement> .</span><span class="sxs-lookup"><span data-stu-id="07905-127">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="07905-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="07905-128">Parent Elements</span></span>  
  
|<span data-ttu-id="07905-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="07905-129">Element</span></span>|<span data-ttu-id="07905-130">Description</span><span class="sxs-lookup"><span data-stu-id="07905-130">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="07905-131">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="07905-131">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07905-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07905-132">Remarks</span></span>  
 <span data-ttu-id="07905-133">Pověření klienta slouží k ověřování klienta se službami v případech, kdy je nutné vzájemné ověřování.</span><span class="sxs-lookup"><span data-stu-id="07905-133">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="07905-134">Tento oddíl konfigurace lze také použít k určení certifikátů služby pro scénáře, ve kterých musí klient zabezpečit zprávy do služby pomocí certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="07905-134">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07905-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="07905-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="07905-136">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="07905-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="07905-137">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="07905-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
