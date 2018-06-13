---
title: '&lt;security&gt; – &lt;webHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2df10c0a35a5547dc2f1dafc6a2b9c0f9bbdc0a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350449"
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="c0cbe-102">&lt;security&gt; – &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="c0cbe-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="c0cbe-103">Určuje koncovým bodem nakonfigurovaným s požadavky na zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c0cbe-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="c0cbe-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c0cbe-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c0cbe-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="c0cbe-105">\<bindings></span></span>  
<span data-ttu-id="c0cbe-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c0cbe-106">\<webHttpBinding></span></span>  
<span data-ttu-id="c0cbe-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="c0cbe-107">\<binding></span></span>  
<span data-ttu-id="c0cbe-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="c0cbe-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0cbe-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0cbe-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0cbe-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c0cbe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c0cbe-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0cbe-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c0cbe-112">Attributes</span></span>  
  
|<span data-ttu-id="c0cbe-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c0cbe-113">Attribute</span></span>|<span data-ttu-id="c0cbe-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c0cbe-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0cbe-115">režim</span><span class="sxs-lookup"><span data-stu-id="c0cbe-115">mode</span></span>|<span data-ttu-id="c0cbe-116">Určuje, jestli je koncový bod používá zabezpečení na úrovni přenosu nebo žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="c0cbe-117">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-117">The default is `None`.</span></span> <span data-ttu-id="c0cbe-118">Tento atribut je typu <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="c0cbe-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="c0cbe-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="c0cbe-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c0cbe-120">Value</span></span>|<span data-ttu-id="c0cbe-121">Popis</span><span class="sxs-lookup"><span data-stu-id="c0cbe-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0cbe-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="c0cbe-122">None</span></span>|<span data-ttu-id="c0cbe-123">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-123">Security is disabled.</span></span>|  
|<span data-ttu-id="c0cbe-124">Přenos</span><span class="sxs-lookup"><span data-stu-id="c0cbe-124">Transport</span></span>|<span data-ttu-id="c0cbe-125">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="c0cbe-126">Službu je potřeba nakonfigurovat s certifikáty protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="c0cbe-127">Zpráva zcela zabezpečené pomocí protokolu HTTPS a službu ověření klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="c0cbe-128">Ověření klienta je řízen pomocí `ClientCredentialType` atribut [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c0cbe-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="c0cbe-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="c0cbe-129">TransportCredentialOnly</span></span>|<span data-ttu-id="c0cbe-130">Tento režim neposkytuje integrity a důvěrnosti zpráv.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="c0cbe-131">Poskytuje ověření klienta založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="c0cbe-132">Tento režim musí být použit s opatrní.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-132">This mode should be used with caution.</span></span> <span data-ttu-id="c0cbe-133">By být používána v prostředích, kde se zajišťuje zabezpečení přenosu jiným způsobem (například IPSec) a infrastruktura WCF se poskytuje pouze ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0cbe-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c0cbe-134">Child Elements</span></span>  
  
|<span data-ttu-id="c0cbe-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="c0cbe-135">Element</span></span>|<span data-ttu-id="c0cbe-136">Popis</span><span class="sxs-lookup"><span data-stu-id="c0cbe-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0cbe-137">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="c0cbe-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="c0cbe-138">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-138">Defines the transport security settings.</span></span> <span data-ttu-id="c0cbe-139">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0cbe-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c0cbe-140">Parent Elements</span></span>  
  
|<span data-ttu-id="c0cbe-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="c0cbe-141">Element</span></span>|<span data-ttu-id="c0cbe-142">Popis</span><span class="sxs-lookup"><span data-stu-id="c0cbe-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0cbe-143">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c0cbe-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="c0cbe-144">Element vazby, který slouží ke konfiguraci koncových bodů pro Windows Communication Foundation (WCF) webové služby tohoto reakce na požadavky HTTP místo protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0cbe-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0cbe-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0cbe-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="c0cbe-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c0cbe-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="c0cbe-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="c0cbe-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="c0cbe-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="c0cbe-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c0cbe-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="c0cbe-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c0cbe-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="c0cbe-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="c0cbe-151">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="c0cbe-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="c0cbe-152">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="c0cbe-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
