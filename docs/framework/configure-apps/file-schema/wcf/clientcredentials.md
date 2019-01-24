---
title: '&lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: d8171254fed64a2d9ba526d5714d5707aa1b1c1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646052"
---
# <a name="ltclientcredentialsgt"></a><span data-ttu-id="b63ba-102">&lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="b63ba-102">&lt;clientCredentials&gt;</span></span>
<span data-ttu-id="b63ba-103">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="b63ba-103">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="b63ba-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b63ba-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b63ba-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b63ba-105">\<behaviors></span></span>  
<span data-ttu-id="b63ba-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="b63ba-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="b63ba-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b63ba-107">\<behavior></span></span>  
<span data-ttu-id="b63ba-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="b63ba-108">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b63ba-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b63ba-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b63ba-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b63ba-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b63ba-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b63ba-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b63ba-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b63ba-112">Attributes</span></span>  
  
|<span data-ttu-id="b63ba-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="b63ba-113">Attribute</span></span>|<span data-ttu-id="b63ba-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b63ba-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="b63ba-115">Logická hodnota, která určuje, zda může být interaktivní uživatelské součástí výběru pověření klienta za běhu.</span><span class="sxs-lookup"><span data-stu-id="b63ba-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="b63ba-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="b63ba-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="b63ba-117">Řetězec, který určuje typ tohoto konfiguračního prvku.</span><span class="sxs-lookup"><span data-stu-id="b63ba-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b63ba-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b63ba-118">Child Elements</span></span>  
  
|<span data-ttu-id="b63ba-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="b63ba-119">Element</span></span>|<span data-ttu-id="b63ba-120">Popis</span><span class="sxs-lookup"><span data-stu-id="b63ba-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b63ba-121">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="b63ba-121">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="b63ba-122">Určuje certifikát používaný k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="b63ba-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="b63ba-123">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="b63ba-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="b63ba-124">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="b63ba-124">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="b63ba-125">Určuje algoritmu digest pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="b63ba-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="b63ba-126">Tento prvek je typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="b63ba-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="b63ba-127">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="b63ba-127">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="b63ba-128">Určuje vlastní typ tokenu pro ověření klienta k zabezpečení tokenu služby (STS).</span><span class="sxs-lookup"><span data-stu-id="b63ba-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="b63ba-129">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="b63ba-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="b63ba-130">\<peer></span><span class="sxs-lookup"><span data-stu-id="b63ba-130">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="b63ba-131">Určuje aktuální peer pověření.</span><span class="sxs-lookup"><span data-stu-id="b63ba-131">Specifies a current peer credential.</span></span> <span data-ttu-id="b63ba-132">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="b63ba-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="b63ba-133">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="b63ba-133">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="b63ba-134">Určuje certifikát používaný k ověřování klienta a poskytuje strukturu pro nastavení možnosti certifikátu.</span><span class="sxs-lookup"><span data-stu-id="b63ba-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="b63ba-135">Tento certifikát musí být zadaný out-of-band ze služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="b63ba-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="b63ba-136">Tento prvek je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="b63ba-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="b63ba-137">\<windows></span><span class="sxs-lookup"><span data-stu-id="b63ba-137">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="b63ba-138">Určuje přihlašovací údaje Windows.</span><span class="sxs-lookup"><span data-stu-id="b63ba-138">Specifies a Windows credential.</span></span> <span data-ttu-id="b63ba-139">Výchozí hodnota je přihlašovacích údajů aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="b63ba-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="b63ba-140">Tento prvek je typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="b63ba-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b63ba-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b63ba-141">Parent Elements</span></span>  
  
|<span data-ttu-id="b63ba-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="b63ba-142">Element</span></span>|<span data-ttu-id="b63ba-143">Popis</span><span class="sxs-lookup"><span data-stu-id="b63ba-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b63ba-144">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b63ba-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b63ba-145">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b63ba-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b63ba-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b63ba-146">Remarks</span></span>  
 <span data-ttu-id="b63ba-147">Přihlašovací údaje pro klienta se používají k ověření klienta ke službám v případech, kdy je vyžaduje vzájemné ověřování.</span><span class="sxs-lookup"><span data-stu-id="b63ba-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="b63ba-148">Tento oddíl konfigurace lze také určení certifikátů služby pro scénáře, ve kterém musí klient zabezpečené zprávy do služby pomocí certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="b63ba-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b63ba-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b63ba-149">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="b63ba-150">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b63ba-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b63ba-151">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="b63ba-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
