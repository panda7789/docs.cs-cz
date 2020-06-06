---
title: <security> z <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
ms.openlocfilehash: 77009dc950a608da9e0db3a7d09be67e1ed46137
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738633"
---
# <a name="security-of-webhttpbinding"></a><span data-ttu-id="93dc9-102">\<security> z \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="93dc9-102">\<security> of \<webHttpBinding></span></span>
<span data-ttu-id="93dc9-103">Určuje požadavky na zabezpečení pro koncový bod nakonfigurovaný pomocí [\<webHttpBinding>](webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="93dc9-103">Specifies the security requirements for an endpoint configured with a [\<webHttpBinding>](webhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="93dc9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93dc9-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93dc9-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="93dc9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="93dc9-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="93dc9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93dc9-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="93dc9-107">Attributes</span></span>  
  
|<span data-ttu-id="93dc9-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="93dc9-108">Attribute</span></span>|<span data-ttu-id="93dc9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="93dc9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93dc9-110">režim</span><span class="sxs-lookup"><span data-stu-id="93dc9-110">mode</span></span>|<span data-ttu-id="93dc9-111">Určuje, zda koncový bod nepoužívá zabezpečení na úrovni přenosu nebo žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="93dc9-111">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="93dc9-112">Výchozí formát je `None`.</span><span class="sxs-lookup"><span data-stu-id="93dc9-112">The default is `None`.</span></span> <span data-ttu-id="93dc9-113">Tento atribut je typu <xref:System.ServiceModel.WebHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="93dc9-113">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="93dc9-114">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="93dc9-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="93dc9-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="93dc9-115">Value</span></span>|<span data-ttu-id="93dc9-116">Description</span><span class="sxs-lookup"><span data-stu-id="93dc9-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="93dc9-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="93dc9-117">None</span></span>|<span data-ttu-id="93dc9-118">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="93dc9-118">Security is disabled.</span></span>|  
|<span data-ttu-id="93dc9-119">Přenos</span><span class="sxs-lookup"><span data-stu-id="93dc9-119">Transport</span></span>|<span data-ttu-id="93dc9-120">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="93dc9-120">Security is provided using HTTPS.</span></span> <span data-ttu-id="93dc9-121">Služba musí být nakonfigurovaná s certifikáty SSL.</span><span class="sxs-lookup"><span data-stu-id="93dc9-121">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="93dc9-122">Zpráva je zcela zabezpečená pomocí protokolu HTTPS a služba je ověřena klientem pomocí certifikátu protokolu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="93dc9-122">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="93dc9-123">Ověřování klienta je řízeno pomocí `ClientCredentialType` atributu [\<transport>](transport-of-webhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="93dc9-123">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="93dc9-124">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="93dc9-124">TransportCredentialOnly</span></span>|<span data-ttu-id="93dc9-125">Tento režim neposkytuje integritu a důvěrnost zpráv.</span><span class="sxs-lookup"><span data-stu-id="93dc9-125">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="93dc9-126">Poskytuje ověřování klientů založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="93dc9-126">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="93dc9-127">Tento režim by se měl používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="93dc9-127">This mode should be used with caution.</span></span> <span data-ttu-id="93dc9-128">Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="93dc9-128">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93dc9-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="93dc9-129">Child Elements</span></span>  
  
|<span data-ttu-id="93dc9-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="93dc9-130">Element</span></span>|<span data-ttu-id="93dc9-131">Description</span><span class="sxs-lookup"><span data-stu-id="93dc9-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-webhttpbinding.md)|<span data-ttu-id="93dc9-132">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="93dc9-132">Defines the transport security settings.</span></span> <span data-ttu-id="93dc9-133">Tento prvek odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="93dc9-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93dc9-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="93dc9-134">Parent Elements</span></span>  
  
|<span data-ttu-id="93dc9-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="93dc9-135">Element</span></span>|<span data-ttu-id="93dc9-136">Description</span><span class="sxs-lookup"><span data-stu-id="93dc9-136">Description</span></span>|  
|-------------|-----------------|  
|[\<webHttpBinding>](webhttpbinding.md)|<span data-ttu-id="93dc9-137">Prvek vazby, který slouží ke konfiguraci koncových bodů pro webové služby Windows Communication Foundation (WCF), které reagují na požadavky HTTP namísto zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="93dc9-137">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93dc9-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="93dc9-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.WebHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.WebHttpSecurity>
- [<span data-ttu-id="93dc9-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="93dc9-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="93dc9-140">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="93dc9-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="93dc9-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="93dc9-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="93dc9-142">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="93dc9-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="93dc9-143">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="93dc9-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="93dc9-144">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="93dc9-144">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
