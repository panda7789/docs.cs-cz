---
title: "&lt;security&gt; – &lt;webHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b3d5d00dcc79a746818975a6a8b125d3dc33933b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="94e9e-102">&lt;security&gt; – &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="94e9e-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="94e9e-103">Určuje koncovým bodem nakonfigurovaným s požadavky na zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="94e9e-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="94e9e-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="94e9e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="94e9e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="94e9e-105">\<bindings></span></span>  
<span data-ttu-id="94e9e-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="94e9e-106">\<webHttpBinding></span></span>  
<span data-ttu-id="94e9e-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="94e9e-107">\<binding></span></span>  
<span data-ttu-id="94e9e-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="94e9e-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94e9e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94e9e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94e9e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="94e9e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="94e9e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="94e9e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94e9e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="94e9e-112">Attributes</span></span>  
  
|<span data-ttu-id="94e9e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="94e9e-113">Attribute</span></span>|<span data-ttu-id="94e9e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="94e9e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94e9e-115">režim</span><span class="sxs-lookup"><span data-stu-id="94e9e-115">mode</span></span>|<span data-ttu-id="94e9e-116">Určuje, jestli je koncový bod používá zabezpečení na úrovni přenosu nebo žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="94e9e-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="94e9e-117">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="94e9e-117">The default is `None`.</span></span> <span data-ttu-id="94e9e-118">Tento atribut je typu <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="94e9e-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="94e9e-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="94e9e-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="94e9e-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="94e9e-120">Value</span></span>|<span data-ttu-id="94e9e-121">Popis</span><span class="sxs-lookup"><span data-stu-id="94e9e-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="94e9e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="94e9e-122">None</span></span>|<span data-ttu-id="94e9e-123">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="94e9e-123">Security is disabled.</span></span>|  
|<span data-ttu-id="94e9e-124">Přenos</span><span class="sxs-lookup"><span data-stu-id="94e9e-124">Transport</span></span>|<span data-ttu-id="94e9e-125">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="94e9e-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="94e9e-126">Službu je potřeba nakonfigurovat s certifikáty protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="94e9e-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="94e9e-127">Zpráva zcela zabezpečené pomocí protokolu HTTPS a službu ověření klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="94e9e-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="94e9e-128">Ověření klienta je řízen pomocí `ClientCredentialType` atribut [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="94e9e-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="94e9e-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="94e9e-129">TransportCredentialOnly</span></span>|<span data-ttu-id="94e9e-130">Tento režim neposkytuje integrity a důvěrnosti zpráv.</span><span class="sxs-lookup"><span data-stu-id="94e9e-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="94e9e-131">Poskytuje ověření klienta založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="94e9e-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="94e9e-132">Tento režim musí být použit s opatrní.</span><span class="sxs-lookup"><span data-stu-id="94e9e-132">This mode should be used with caution.</span></span> <span data-ttu-id="94e9e-133">By být používána v prostředích, kde se jiným způsobem (například IPSec) zajišťuje zabezpečení přenosu a zajišťuje pouze ověřování klienta [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="94e9e-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94e9e-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="94e9e-134">Child Elements</span></span>  
  
|<span data-ttu-id="94e9e-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="94e9e-135">Element</span></span>|<span data-ttu-id="94e9e-136">Popis</span><span class="sxs-lookup"><span data-stu-id="94e9e-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94e9e-137">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="94e9e-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="94e9e-138">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="94e9e-138">Defines the transport security settings.</span></span> <span data-ttu-id="94e9e-139">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="94e9e-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94e9e-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="94e9e-140">Parent Elements</span></span>  
  
|<span data-ttu-id="94e9e-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="94e9e-141">Element</span></span>|<span data-ttu-id="94e9e-142">Popis</span><span class="sxs-lookup"><span data-stu-id="94e9e-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94e9e-143">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="94e9e-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="94e9e-144">Element vazby, který slouží ke konfiguraci koncových bodů pro [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] webové služby tohoto reakce na požadavky HTTP místo protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="94e9e-144">A binding element that is used to configure endpoints for [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94e9e-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="94e9e-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="94e9e-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="94e9e-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="94e9e-147">Výběr typu pověření</span><span class="sxs-lookup"><span data-stu-id="94e9e-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="94e9e-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="94e9e-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="94e9e-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="94e9e-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="94e9e-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="94e9e-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="94e9e-151">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="94e9e-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="94e9e-152">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="94e9e-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
