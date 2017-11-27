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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8a1b3f5f7e8eea555be10870bc00f9b975c57a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientcredentialsgt"></a><span data-ttu-id="d067c-102">&lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="d067c-102">&lt;clientCredentials&gt;</span></span>
<span data-ttu-id="d067c-103">Určuje pověření, která používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="d067c-103">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="d067c-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d067c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d067c-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d067c-105">\<behaviors></span></span>  
<span data-ttu-id="d067c-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d067c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d067c-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d067c-107">\<behavior></span></span>  
<span data-ttu-id="d067c-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="d067c-108">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d067c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d067c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d067c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d067c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d067c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d067c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d067c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d067c-112">Attributes</span></span>  
  
|<span data-ttu-id="d067c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d067c-113">Attribute</span></span>|<span data-ttu-id="d067c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d067c-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="d067c-115">Logická hodnota, která určuje, zda může být při výběru pověření klienta v době běhu zapojeno interaktivního uživatele.</span><span class="sxs-lookup"><span data-stu-id="d067c-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="d067c-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="d067c-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="d067c-117">Řetězec, který určuje typ tohoto elementu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d067c-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d067c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d067c-118">Child Elements</span></span>  
  
|<span data-ttu-id="d067c-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="d067c-119">Element</span></span>|<span data-ttu-id="d067c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="d067c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d067c-121">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="d067c-121">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="d067c-122">Určuje certifikát používaný k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="d067c-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="d067c-123">Tento element je typu <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="d067c-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="d067c-124">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="d067c-124">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="d067c-125">Určuje hodnotou hash používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="d067c-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="d067c-126">Tento element je typu <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="d067c-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="d067c-127">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="d067c-127">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="d067c-128">Určuje vlastní typ tokenu, který používá k ověření klienta k zabezpečení tokenu služby (STS).</span><span class="sxs-lookup"><span data-stu-id="d067c-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="d067c-129">Tento element je typu <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="d067c-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="d067c-130">\<sdílené ></span><span class="sxs-lookup"><span data-stu-id="d067c-130">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="d067c-131">Určuje aktuální přihlašovací údaje partnera.</span><span class="sxs-lookup"><span data-stu-id="d067c-131">Specifies a current peer credential.</span></span> <span data-ttu-id="d067c-132">Tento element je typu <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="d067c-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="d067c-133">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="d067c-133">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="d067c-134">Určuje certifikát používaný k ověřování klienta a poskytuje strukturu pro nastavení možností certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d067c-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="d067c-135">Tento certifikát musí být zadaný out-of-band ze služby do klienta.</span><span class="sxs-lookup"><span data-stu-id="d067c-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="d067c-136">Tento element je typu <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="d067c-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="d067c-137">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="d067c-137">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="d067c-138">Určuje pověření systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d067c-138">Specifies a Windows credential.</span></span> <span data-ttu-id="d067c-139">Výchozí hodnota je přihlašovací údaje aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="d067c-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="d067c-140">Tento element je typu <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="d067c-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d067c-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d067c-141">Parent Elements</span></span>  
  
|<span data-ttu-id="d067c-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="d067c-142">Element</span></span>|<span data-ttu-id="d067c-143">Popis</span><span class="sxs-lookup"><span data-stu-id="d067c-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d067c-144">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d067c-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d067c-145">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d067c-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d067c-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d067c-146">Remarks</span></span>  
 <span data-ttu-id="d067c-147">Pověření klienta slouží k ověření klienta ke službám v případech, kdy je potřeba vzájemné ověřování.</span><span class="sxs-lookup"><span data-stu-id="d067c-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="d067c-148">Tento oddíl konfigurace mohou sloužit také k určení certifikáty služby pro scénáře, kde klient musíte zabezpečit zprávy služby pomocí certifikátu služby.</span><span class="sxs-lookup"><span data-stu-id="d067c-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d067c-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="d067c-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [<span data-ttu-id="d067c-150">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d067c-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="d067c-151">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="d067c-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
