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
ms.openlocfilehash: 834853d8a922148d2810cd391a64a281f2f9ae3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcredentialsgt"></a><span data-ttu-id="f18a2-102">&lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="f18a2-102">&lt;clientCredentials&gt;</span></span>
<span data-ttu-id="f18a2-103">Určuje pověření, která používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="f18a2-103">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="f18a2-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f18a2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f18a2-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f18a2-105">\<behaviors></span></span>  
<span data-ttu-id="f18a2-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f18a2-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="f18a2-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f18a2-107">\<behavior></span></span>  
<span data-ttu-id="f18a2-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f18a2-108">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f18a2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f18a2-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f18a2-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f18a2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f18a2-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f18a2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f18a2-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f18a2-112">Attributes</span></span>  
  
|<span data-ttu-id="f18a2-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f18a2-113">Attribute</span></span>|<span data-ttu-id="f18a2-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f18a2-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="f18a2-115">Logická hodnota, která určuje, zda může být při výběru pověření klienta v době běhu zapojeno interaktivního uživatele.</span><span class="sxs-lookup"><span data-stu-id="f18a2-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="f18a2-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="f18a2-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="f18a2-117">Řetězec, který určuje typ tohoto elementu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f18a2-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f18a2-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f18a2-118">Child Elements</span></span>  
  
|<span data-ttu-id="f18a2-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="f18a2-119">Element</span></span>|<span data-ttu-id="f18a2-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f18a2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f18a2-121">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="f18a2-121">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="f18a2-122">Určuje certifikát používaný k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="f18a2-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="f18a2-123">Tento element je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="f18a2-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="f18a2-124">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="f18a2-124">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="f18a2-125">Určuje hodnotou hash používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="f18a2-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="f18a2-126">Tento element je typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="f18a2-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="f18a2-127">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="f18a2-127">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="f18a2-128">Určuje vlastní typ tokenu, který používá k ověření klienta k zabezpečení tokenu služby (STS).</span><span class="sxs-lookup"><span data-stu-id="f18a2-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="f18a2-129">Tento element je typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="f18a2-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="f18a2-130">\<sdílené ></span><span class="sxs-lookup"><span data-stu-id="f18a2-130">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="f18a2-131">Určuje aktuální přihlašovací údaje partnera.</span><span class="sxs-lookup"><span data-stu-id="f18a2-131">Specifies a current peer credential.</span></span> <span data-ttu-id="f18a2-132">Tento element je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="f18a2-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="f18a2-133">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="f18a2-133">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="f18a2-134">Určuje certifikát používaný k ověřování klienta a poskytuje strukturu pro nastavení možností certifikátu.</span><span class="sxs-lookup"><span data-stu-id="f18a2-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="f18a2-135">Tento certifikát musí být zadaný out-of-band ze služby do klienta.</span><span class="sxs-lookup"><span data-stu-id="f18a2-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="f18a2-136">Tento element je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="f18a2-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="f18a2-137">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="f18a2-137">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="f18a2-138">Určuje pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f18a2-138">Specifies a Windows credential.</span></span> <span data-ttu-id="f18a2-139">Výchozí hodnota je přihlašovací údaje aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="f18a2-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="f18a2-140">Tento element je typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="f18a2-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f18a2-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f18a2-141">Parent Elements</span></span>  
  
|<span data-ttu-id="f18a2-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="f18a2-142">Element</span></span>|<span data-ttu-id="f18a2-143">Popis</span><span class="sxs-lookup"><span data-stu-id="f18a2-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f18a2-144">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f18a2-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="f18a2-145">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f18a2-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f18a2-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f18a2-146">Remarks</span></span>  
 <span data-ttu-id="f18a2-147">Pověření klienta slouží k ověření klienta ke službám v případech, kdy je potřeba vzájemné ověřování.</span><span class="sxs-lookup"><span data-stu-id="f18a2-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="f18a2-148">Tento oddíl konfigurace mohou sloužit také k určení certifikáty služby pro scénáře, kde klient musíte zabezpečit zprávy služby pomocí certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="f18a2-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f18a2-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="f18a2-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [<span data-ttu-id="f18a2-150">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f18a2-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="f18a2-151">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="f18a2-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
