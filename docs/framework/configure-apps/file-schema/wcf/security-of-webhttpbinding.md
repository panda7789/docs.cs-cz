---
title: <security> z <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 806cf8524ed1a1439ca85a4b918e8e486e5dc94b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936591"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="21ac0-102">\<> zabezpečení > \<WebHttpBinding</span><span class="sxs-lookup"><span data-stu-id="21ac0-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="21ac0-103">Určuje požadavky na zabezpečení pro koncový bod nakonfigurovaný s [ \<> WebHttpBinding](webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="21ac0-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
 <span data-ttu-id="21ac0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="21ac0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="21ac0-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="21ac0-105">\<bindings></span></span>  
<span data-ttu-id="21ac0-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="21ac0-106">\<webHttpBinding></span></span>  
<span data-ttu-id="21ac0-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="21ac0-107">\<binding></span></span>  
<span data-ttu-id="21ac0-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="21ac0-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21ac0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21ac0-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <bindings>
    <webHttpBinding>
      <binding name = "String">
        <security mode="None/Transport/TransportCredentialOnly">
          <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                     realm="String" />
        </security>
      </binding>
    </webHttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21ac0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="21ac0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="21ac0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="21ac0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21ac0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="21ac0-112">Attributes</span></span>  
  
|<span data-ttu-id="21ac0-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="21ac0-113">Attribute</span></span>|<span data-ttu-id="21ac0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="21ac0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21ac0-115">režim</span><span class="sxs-lookup"><span data-stu-id="21ac0-115">mode</span></span>|<span data-ttu-id="21ac0-116">Určuje, zda koncový bod nepoužívá zabezpečení na úrovni přenosu nebo žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="21ac0-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="21ac0-117">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="21ac0-117">The default is `None`.</span></span> <span data-ttu-id="21ac0-118">Tento atribut je typu <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="21ac0-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="21ac0-119">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="21ac0-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="21ac0-120">Value</span><span class="sxs-lookup"><span data-stu-id="21ac0-120">Value</span></span>|<span data-ttu-id="21ac0-121">Popis</span><span class="sxs-lookup"><span data-stu-id="21ac0-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="21ac0-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="21ac0-122">None</span></span>|<span data-ttu-id="21ac0-123">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="21ac0-123">Security is disabled.</span></span>|  
|<span data-ttu-id="21ac0-124">Přepravu</span><span class="sxs-lookup"><span data-stu-id="21ac0-124">Transport</span></span>|<span data-ttu-id="21ac0-125">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="21ac0-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="21ac0-126">Služba musí být nakonfigurovaná s certifikáty SSL.</span><span class="sxs-lookup"><span data-stu-id="21ac0-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="21ac0-127">Zpráva je zcela zabezpečená pomocí protokolu HTTPS a služba je ověřena klientem pomocí certifikátu protokolu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="21ac0-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="21ac0-128">Ověřování klienta se řídí `ClientCredentialType` atributem [ \<> přenosů](transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="21ac0-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="21ac0-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="21ac0-129">TransportCredentialOnly</span></span>|<span data-ttu-id="21ac0-130">Tento režim neposkytuje integritu a důvěrnost zpráv.</span><span class="sxs-lookup"><span data-stu-id="21ac0-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="21ac0-131">Poskytuje ověřování klientů založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="21ac0-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="21ac0-132">Tento režim by se měl používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="21ac0-132">This mode should be used with caution.</span></span> <span data-ttu-id="21ac0-133">Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="21ac0-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21ac0-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="21ac0-134">Child Elements</span></span>  
  
|<span data-ttu-id="21ac0-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="21ac0-135">Element</span></span>|<span data-ttu-id="21ac0-136">Popis</span><span class="sxs-lookup"><span data-stu-id="21ac0-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21ac0-137">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="21ac0-137">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="21ac0-138">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="21ac0-138">Defines the transport security settings.</span></span> <span data-ttu-id="21ac0-139">Tento prvek odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="21ac0-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21ac0-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="21ac0-140">Parent Elements</span></span>  
  
|<span data-ttu-id="21ac0-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="21ac0-141">Element</span></span>|<span data-ttu-id="21ac0-142">Popis</span><span class="sxs-lookup"><span data-stu-id="21ac0-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21ac0-143">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="21ac0-143">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="21ac0-144">Prvek vazby, který slouží ke konfiguraci koncových bodů pro webové služby Windows Communication Foundation (WCF), které reagují na požadavky HTTP namísto zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="21ac0-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21ac0-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21ac0-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="21ac0-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="21ac0-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="21ac0-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="21ac0-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="21ac0-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="21ac0-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="21ac0-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="21ac0-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="21ac0-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="21ac0-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="21ac0-151">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="21ac0-151">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="21ac0-152">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="21ac0-152">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
