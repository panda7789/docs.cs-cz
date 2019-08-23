---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: c3e756f49b7054d6553eb6c3f1850f0fbce14943
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926115"
---
# <a name="clientcredentials"></a><span data-ttu-id="19c80-101">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="19c80-101">\<clientCredentials></span></span>
<span data-ttu-id="19c80-102">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="19c80-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="19c80-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="19c80-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="19c80-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="19c80-104">\<behaviors></span></span>  
<span data-ttu-id="19c80-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="19c80-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="19c80-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="19c80-106">\<behavior></span></span>  
<span data-ttu-id="19c80-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="19c80-107">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19c80-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19c80-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19c80-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="19c80-109">Attributes and Elements</span></span>  
 <span data-ttu-id="19c80-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="19c80-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19c80-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="19c80-111">Attributes</span></span>  
  
|<span data-ttu-id="19c80-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="19c80-112">Attribute</span></span>|<span data-ttu-id="19c80-113">Popis</span><span class="sxs-lookup"><span data-stu-id="19c80-113">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="19c80-114">Logická hodnota určující, zda může být interaktivní uživatel zapojen do výběru přihlašovacích údajů klienta za běhu.</span><span class="sxs-lookup"><span data-stu-id="19c80-114">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="19c80-115">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="19c80-115">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="19c80-116">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="19c80-116">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19c80-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="19c80-117">Child Elements</span></span>  
  
|<span data-ttu-id="19c80-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="19c80-118">Element</span></span>|<span data-ttu-id="19c80-119">Popis</span><span class="sxs-lookup"><span data-stu-id="19c80-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19c80-120">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="19c80-120">\<clientCertificate></span></span>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="19c80-121">Určuje certifikát, který se používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="19c80-121">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="19c80-122">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="19c80-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="19c80-123">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="19c80-123">\<httpDigest></span></span>](httpdigest-element.md)|<span data-ttu-id="19c80-124">Určuje výtah, který se používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="19c80-124">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="19c80-125">Tento prvek je typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="19c80-125">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="19c80-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="19c80-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="19c80-127">Určuje vlastní typ tokenu, který se používá k ověření klienta ke službě tokenů zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="19c80-127">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="19c80-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="19c80-128">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="19c80-129">\<peer></span><span class="sxs-lookup"><span data-stu-id="19c80-129">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="19c80-130">Určuje aktuální přihlašovací údaje partnerského vztahu.</span><span class="sxs-lookup"><span data-stu-id="19c80-130">Specifies a current peer credential.</span></span> <span data-ttu-id="19c80-131">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="19c80-131">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="19c80-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="19c80-132">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="19c80-133">Určuje certifikát použitý k ověření služby klientovi a poskytuje strukturu pro nastavení možností certifikátu.</span><span class="sxs-lookup"><span data-stu-id="19c80-133">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="19c80-134">Tento certifikát musí být dodán od služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="19c80-134">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="19c80-135">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="19c80-135">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="19c80-136">\<windows></span><span class="sxs-lookup"><span data-stu-id="19c80-136">\<windows></span></span>](windows-of-clientcredentials-element.md)|<span data-ttu-id="19c80-137">Určuje pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="19c80-137">Specifies a Windows credential.</span></span> <span data-ttu-id="19c80-138">Výchozí hodnota je přihlašovací údaje aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="19c80-138">The default is the credential of the current thread.</span></span> <span data-ttu-id="19c80-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="19c80-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19c80-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="19c80-140">Parent Elements</span></span>  
  
|<span data-ttu-id="19c80-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="19c80-141">Element</span></span>|<span data-ttu-id="19c80-142">Popis</span><span class="sxs-lookup"><span data-stu-id="19c80-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19c80-143">\<> chování</span><span class="sxs-lookup"><span data-stu-id="19c80-143">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="19c80-144">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="19c80-144">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19c80-145">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19c80-145">Remarks</span></span>  
 <span data-ttu-id="19c80-146">Pověření klienta slouží k ověřování klienta se službami v případech, kdy je nutné vzájemné ověřování.</span><span class="sxs-lookup"><span data-stu-id="19c80-146">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="19c80-147">Tento oddíl konfigurace lze také použít k určení certifikátů služby pro scénáře, ve kterých musí klient zabezpečit zprávy do služby pomocí certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="19c80-147">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c80-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19c80-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="19c80-149">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="19c80-149">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="19c80-150">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="19c80-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
