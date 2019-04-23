---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: ebe976df9af0c316e95a1e089412e57a575a6df1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157232"
---
# <a name="clientcredentials"></a><span data-ttu-id="06ab4-101">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="06ab4-101">\<clientCredentials></span></span>
<span data-ttu-id="06ab4-102">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="06ab4-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="06ab4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="06ab4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="06ab4-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="06ab4-104">\<behaviors></span></span>  
<span data-ttu-id="06ab4-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="06ab4-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="06ab4-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="06ab4-106">\<behavior></span></span>  
<span data-ttu-id="06ab4-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="06ab4-107">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06ab4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06ab4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06ab4-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="06ab4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="06ab4-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="06ab4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06ab4-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="06ab4-111">Attributes</span></span>  
  
|<span data-ttu-id="06ab4-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="06ab4-112">Attribute</span></span>|<span data-ttu-id="06ab4-113">Popis</span><span class="sxs-lookup"><span data-stu-id="06ab4-113">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="06ab4-114">Logická hodnota, která určuje, zda může být interaktivní uživatelské součástí výběru pověření klienta za běhu.</span><span class="sxs-lookup"><span data-stu-id="06ab4-114">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="06ab4-115">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="06ab4-115">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="06ab4-116">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="06ab4-116">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06ab4-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="06ab4-117">Child Elements</span></span>  
  
|<span data-ttu-id="06ab4-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="06ab4-118">Element</span></span>|<span data-ttu-id="06ab4-119">Popis</span><span class="sxs-lookup"><span data-stu-id="06ab4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06ab4-120">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="06ab4-120">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="06ab4-121">Určuje certifikát používaný k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="06ab4-121">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="06ab4-122">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="06ab4-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="06ab4-123">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="06ab4-123">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="06ab4-124">Určuje algoritmu digest pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="06ab4-124">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="06ab4-125">Tento prvek je typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="06ab4-125">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="06ab4-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="06ab4-126">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="06ab4-127">Určuje vlastní typ tokenu pro ověření klienta k zabezpečení tokenu služby (STS).</span><span class="sxs-lookup"><span data-stu-id="06ab4-127">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="06ab4-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="06ab4-128">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="06ab4-129">\<peer></span><span class="sxs-lookup"><span data-stu-id="06ab4-129">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="06ab4-130">Určuje aktuální peer pověření.</span><span class="sxs-lookup"><span data-stu-id="06ab4-130">Specifies a current peer credential.</span></span> <span data-ttu-id="06ab4-131">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="06ab4-131">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="06ab4-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="06ab4-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="06ab4-133">Určuje certifikát používaný k ověřování klienta a poskytuje strukturu pro nastavení možnosti certifikátu.</span><span class="sxs-lookup"><span data-stu-id="06ab4-133">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="06ab4-134">Tento certifikát musí být zadaný out-of-band ze služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="06ab4-134">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="06ab4-135">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="06ab4-135">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="06ab4-136">\<windows></span><span class="sxs-lookup"><span data-stu-id="06ab4-136">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="06ab4-137">Určuje přihlašovací údaje Windows.</span><span class="sxs-lookup"><span data-stu-id="06ab4-137">Specifies a Windows credential.</span></span> <span data-ttu-id="06ab4-138">Výchozí hodnota je přihlašovacích údajů aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="06ab4-138">The default is the credential of the current thread.</span></span> <span data-ttu-id="06ab4-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="06ab4-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06ab4-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="06ab4-140">Parent Elements</span></span>  
  
|<span data-ttu-id="06ab4-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="06ab4-141">Element</span></span>|<span data-ttu-id="06ab4-142">Popis</span><span class="sxs-lookup"><span data-stu-id="06ab4-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06ab4-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="06ab4-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="06ab4-144">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="06ab4-144">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06ab4-145">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06ab4-145">Remarks</span></span>  
 <span data-ttu-id="06ab4-146">Přihlašovací údaje pro klienta se používají k ověření klienta ke službám v případech, kdy je vyžaduje vzájemné ověřování.</span><span class="sxs-lookup"><span data-stu-id="06ab4-146">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="06ab4-147">Tento oddíl konfigurace lze také určení certifikátů služby pro scénáře, ve kterém musí klient zabezpečené zprávy do služby pomocí certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="06ab4-147">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ab4-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06ab4-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="06ab4-149">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="06ab4-149">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="06ab4-150">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="06ab4-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
