---
title: '&lt;security&gt; – &lt;webHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
author: BrucePerlerMS
ms.openlocfilehash: 28cff66cfd50229eacbb7c7c4b1d65678efb40ea
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47236199"
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="5abbf-102">&lt;security&gt; – &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5abbf-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="5abbf-103">Určuje koncový bod nakonfigurovaný s požadavky na zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5abbf-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="5abbf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5abbf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5abbf-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="5abbf-105">\<bindings></span></span>  
<span data-ttu-id="5abbf-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5abbf-106">\<webHttpBinding></span></span>  
<span data-ttu-id="5abbf-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="5abbf-107">\<binding></span></span>  
<span data-ttu-id="5abbf-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="5abbf-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5abbf-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5abbf-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5abbf-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5abbf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5abbf-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5abbf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5abbf-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5abbf-112">Attributes</span></span>  
  
|<span data-ttu-id="5abbf-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5abbf-113">Attribute</span></span>|<span data-ttu-id="5abbf-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5abbf-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5abbf-115">režim</span><span class="sxs-lookup"><span data-stu-id="5abbf-115">mode</span></span>|<span data-ttu-id="5abbf-116">Určuje, zda zabezpečení transportní vrstvy nebo žádné zabezpečení používá koncový bod.</span><span class="sxs-lookup"><span data-stu-id="5abbf-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="5abbf-117">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="5abbf-117">The default is `None`.</span></span> <span data-ttu-id="5abbf-118">Tento atribut je typu <xref:System.ServiceModel.WebHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5abbf-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="5abbf-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="5abbf-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="5abbf-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5abbf-120">Value</span></span>|<span data-ttu-id="5abbf-121">Popis</span><span class="sxs-lookup"><span data-stu-id="5abbf-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5abbf-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="5abbf-122">None</span></span>|<span data-ttu-id="5abbf-123">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="5abbf-123">Security is disabled.</span></span>|  
|<span data-ttu-id="5abbf-124">Přenos</span><span class="sxs-lookup"><span data-stu-id="5abbf-124">Transport</span></span>|<span data-ttu-id="5abbf-125">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5abbf-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="5abbf-126">Služba je potřeba nakonfigurovat s využitím certifikátů SSL.</span><span class="sxs-lookup"><span data-stu-id="5abbf-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="5abbf-127">Zprávu je zcela zabezpečené pomocí protokolu HTTPS a služba je ověřený pomocí klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="5abbf-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="5abbf-128">Ověření klienta je řízen pomocí `ClientCredentialType` atribut [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5abbf-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="5abbf-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="5abbf-129">TransportCredentialOnly</span></span>|<span data-ttu-id="5abbf-130">Tento režim neposkytuje integrity a důvěrnosti zpráv.</span><span class="sxs-lookup"><span data-stu-id="5abbf-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="5abbf-131">Poskytuje ověření klienta založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5abbf-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="5abbf-132">Tento režim je třeba používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="5abbf-132">This mode should be used with caution.</span></span> <span data-ttu-id="5abbf-133">Byste měli použít ve prostředích, kde zabezpečení přenosu se neposkytujeme jiným způsobem (jako je protokol IPSec) a infrastruktura WCF se poskytuje pouze ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="5abbf-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5abbf-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5abbf-134">Child Elements</span></span>  
  
|<span data-ttu-id="5abbf-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="5abbf-135">Element</span></span>|<span data-ttu-id="5abbf-136">Popis</span><span class="sxs-lookup"><span data-stu-id="5abbf-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5abbf-137">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="5abbf-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="5abbf-138">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="5abbf-138">Defines the transport security settings.</span></span> <span data-ttu-id="5abbf-139">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="5abbf-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5abbf-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5abbf-140">Parent Elements</span></span>  
  
|<span data-ttu-id="5abbf-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="5abbf-141">Element</span></span>|<span data-ttu-id="5abbf-142">Popis</span><span class="sxs-lookup"><span data-stu-id="5abbf-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5abbf-143">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5abbf-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="5abbf-144">Prvek vazby, který se používá ke konfiguraci koncových bodů pro Windows Communication Foundation (WCF) Web services tuto odpověď na požadavky HTTP namísto zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="5abbf-144">A binding element that is used to configure endpoints for Windows Communication Foundation (WCF) Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5abbf-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="5abbf-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="5abbf-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5abbf-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5abbf-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="5abbf-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="5abbf-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="5abbf-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5abbf-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5abbf-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5abbf-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="5abbf-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5abbf-151">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="5abbf-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="5abbf-152">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="5abbf-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
