---
title: <security> z <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738633"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="0dded-102">> \<zabezpečení \<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0dded-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="0dded-103">Určuje požadavky na zabezpečení pro koncový bod nakonfigurovaný pomocí [\<webHttpBinding >](webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0dded-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
<span data-ttu-id="0dded-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0dded-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0dded-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="0dded-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0dded-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0dded-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0dded-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webHttpBinding >** ](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="0dded-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="0dded-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="0dded-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="0dded-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpečení >**</span><span class="sxs-lookup"><span data-stu-id="0dded-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dded-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0dded-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0dded-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0dded-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0dded-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0dded-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0dded-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="0dded-113">Attributes</span></span>  
  
|<span data-ttu-id="0dded-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="0dded-114">Attribute</span></span>|<span data-ttu-id="0dded-115">Popis</span><span class="sxs-lookup"><span data-stu-id="0dded-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0dded-116">režim</span><span class="sxs-lookup"><span data-stu-id="0dded-116">mode</span></span>|<span data-ttu-id="0dded-117">Určuje, zda koncový bod nepoužívá zabezpečení na úrovni přenosu nebo žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0dded-117">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="0dded-118">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="0dded-118">The default is `None`.</span></span> <span data-ttu-id="0dded-119">Tento atribut je typu <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="0dded-119">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0dded-120">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="0dded-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="0dded-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0dded-121">Value</span></span>|<span data-ttu-id="0dded-122">Popis</span><span class="sxs-lookup"><span data-stu-id="0dded-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0dded-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="0dded-123">None</span></span>|<span data-ttu-id="0dded-124">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="0dded-124">Security is disabled.</span></span>|  
|<span data-ttu-id="0dded-125">Přepravu</span><span class="sxs-lookup"><span data-stu-id="0dded-125">Transport</span></span>|<span data-ttu-id="0dded-126">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0dded-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="0dded-127">Služba musí být nakonfigurovaná s certifikáty SSL.</span><span class="sxs-lookup"><span data-stu-id="0dded-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="0dded-128">Zpráva je zcela zabezpečená pomocí protokolu HTTPS a služba je ověřena klientem pomocí certifikátu protokolu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="0dded-128">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="0dded-129">Ověřování klienta se řídí pomocí atributu `ClientCredentialType` [\<> přenosu](transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0dded-129">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="0dded-130">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="0dded-130">TransportCredentialOnly</span></span>|<span data-ttu-id="0dded-131">Tento režim neposkytuje integritu a důvěrnost zpráv.</span><span class="sxs-lookup"><span data-stu-id="0dded-131">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="0dded-132">Poskytuje ověřování klientů založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0dded-132">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="0dded-133">Tento režim by se měl používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="0dded-133">This mode should be used with caution.</span></span> <span data-ttu-id="0dded-134">Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="0dded-134">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0dded-135">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0dded-135">Child Elements</span></span>  
  
|<span data-ttu-id="0dded-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="0dded-136">Element</span></span>|<span data-ttu-id="0dded-137">Popis</span><span class="sxs-lookup"><span data-stu-id="0dded-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0dded-138">> přenos \<</span><span class="sxs-lookup"><span data-stu-id="0dded-138">\<transport></span></span>](transport-of-webhttpbinding.md)|<span data-ttu-id="0dded-139">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="0dded-139">Defines the transport security settings.</span></span> <span data-ttu-id="0dded-140">Tento prvek odpovídá typu <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="0dded-140">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0dded-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0dded-141">Parent Elements</span></span>  
  
|<span data-ttu-id="0dded-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="0dded-142">Element</span></span>|<span data-ttu-id="0dded-143">Popis</span><span class="sxs-lookup"><span data-stu-id="0dded-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0dded-144">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0dded-144">\<webHttpBinding></span></span>](webhttpbinding.md)|<span data-ttu-id="0dded-145">Prvek vazby, který slouží ke konfiguraci koncových bodů pro webové služby Windows Communication Foundation (WCF), které reagují na požadavky HTTP namísto zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="0dded-145">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0dded-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0dded-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="0dded-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0dded-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0dded-148">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="0dded-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="0dded-149">Vazby</span><span class="sxs-lookup"><span data-stu-id="0dded-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0dded-150">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="0dded-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0dded-151">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0dded-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0dded-152">vazba \<</span><span class="sxs-lookup"><span data-stu-id="0dded-152">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="0dded-153">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="0dded-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
