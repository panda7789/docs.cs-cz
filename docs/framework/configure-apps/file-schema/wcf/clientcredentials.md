---
title: '&lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eaf46953d7b2c3f89e1f5b107dc9ddf5d1597875
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltclientcredentialsgt"></a><span data-ttu-id="a6b44-102">&lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="a6b44-102">&lt;clientCredentials&gt;</span></span>
<span data-ttu-id="a6b44-103">Určuje pověření, která používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="a6b44-103">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="a6b44-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a6b44-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a6b44-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a6b44-105">\<behaviors></span></span>  
<span data-ttu-id="a6b44-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a6b44-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="a6b44-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a6b44-107">\<behavior></span></span>  
<span data-ttu-id="a6b44-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="a6b44-108">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6b44-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6b44-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6b44-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a6b44-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a6b44-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a6b44-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6b44-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a6b44-112">Attributes</span></span>  
  
|<span data-ttu-id="a6b44-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a6b44-113">Attribute</span></span>|<span data-ttu-id="a6b44-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a6b44-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="a6b44-115">Logická hodnota, která určuje, zda může být při výběru pověření klienta v době běhu zapojeno interaktivního uživatele.</span><span class="sxs-lookup"><span data-stu-id="a6b44-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="a6b44-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="a6b44-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="a6b44-117">Řetězec, který určuje typ tohoto elementu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a6b44-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6b44-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a6b44-118">Child Elements</span></span>  
  
|<span data-ttu-id="a6b44-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6b44-119">Element</span></span>|<span data-ttu-id="a6b44-120">Popis</span><span class="sxs-lookup"><span data-stu-id="a6b44-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6b44-121">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="a6b44-121">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="a6b44-122">Určuje certifikát používaný k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="a6b44-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="a6b44-123">Tento element je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a6b44-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="a6b44-124">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="a6b44-124">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="a6b44-125">Určuje hodnotou hash používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="a6b44-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="a6b44-126">Tento element je typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a6b44-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="a6b44-127">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="a6b44-127">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="a6b44-128">Určuje vlastní typ tokenu, který používá k ověření klienta k zabezpečení tokenu služby (STS).</span><span class="sxs-lookup"><span data-stu-id="a6b44-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="a6b44-129">Tento element je typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a6b44-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="a6b44-130">\<sdílené ></span><span class="sxs-lookup"><span data-stu-id="a6b44-130">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="a6b44-131">Určuje aktuální přihlašovací údaje partnera.</span><span class="sxs-lookup"><span data-stu-id="a6b44-131">Specifies a current peer credential.</span></span> <span data-ttu-id="a6b44-132">Tento element je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="a6b44-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="a6b44-133">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="a6b44-133">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="a6b44-134">Určuje certifikát používaný k ověřování klienta a poskytuje strukturu pro nastavení možností certifikátu.</span><span class="sxs-lookup"><span data-stu-id="a6b44-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="a6b44-135">Tento certifikát musí být zadaný out-of-band ze služby do klienta.</span><span class="sxs-lookup"><span data-stu-id="a6b44-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="a6b44-136">Tento element je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a6b44-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="a6b44-137">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="a6b44-137">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="a6b44-138">Určuje pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a6b44-138">Specifies a Windows credential.</span></span> <span data-ttu-id="a6b44-139">Výchozí hodnota je přihlašovací údaje aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="a6b44-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="a6b44-140">Tento element je typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a6b44-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6b44-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a6b44-141">Parent Elements</span></span>  
  
|<span data-ttu-id="a6b44-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6b44-142">Element</span></span>|<span data-ttu-id="a6b44-143">Popis</span><span class="sxs-lookup"><span data-stu-id="a6b44-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6b44-144">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a6b44-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a6b44-145">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a6b44-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6b44-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6b44-146">Remarks</span></span>  
 <span data-ttu-id="a6b44-147">Pověření klienta slouží k ověření klienta ke službám v případech, kdy je potřeba vzájemné ověřování.</span><span class="sxs-lookup"><span data-stu-id="a6b44-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="a6b44-148">Tento oddíl konfigurace mohou sloužit také k určení certifikáty služby pro scénáře, kde klient musíte zabezpečit zprávy služby pomocí certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="a6b44-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b44-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6b44-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [<span data-ttu-id="a6b44-150">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a6b44-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="a6b44-151">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="a6b44-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
