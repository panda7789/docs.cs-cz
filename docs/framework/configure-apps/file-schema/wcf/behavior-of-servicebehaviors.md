---
title: <behavior> z <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 115f94fc3f17dc5b4dd1ee3a090f2c9d121f810b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139729"
---
# <a name="behavior-of-servicebehaviors"></a><span data-ttu-id="a18bd-102">\<behavior> z \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a18bd-102">\<behavior> of \<serviceBehaviors></span></span>
<span data-ttu-id="a18bd-103">`behavior` Element obsahuje nastavení pro chování služby kolekce.</span><span class="sxs-lookup"><span data-stu-id="a18bd-103">The `behavior` element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="a18bd-104">Každý chování je indexované podle jeho `name`.</span><span class="sxs-lookup"><span data-stu-id="a18bd-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="a18bd-105">Služby lze propojit s každým chováním pomocí tohoto názvu pomocí `behaviorConfiguration` atributu [\<endpoint>](endpoint-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="a18bd-105">Services can link to each behavior through this name using the `behaviorConfiguration` attribute of the [\<endpoint>](endpoint-element.md) element.</span></span> <span data-ttu-id="a18bd-106">To umožňuje koncové body sdílení obvyklé chování konfigurace bez předefinování nastavení.</span><span class="sxs-lookup"><span data-stu-id="a18bd-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span> <span data-ttu-id="a18bd-107">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="a18bd-107">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a18bd-108">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a18bd-108">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a18bd-109">Prvky chování specifické pro aktivity Windows Workflow, jako je například [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, jsou zdokumentovány [ \<behavior> \<serviceBehaviors> na](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) stránce.</span><span class="sxs-lookup"><span data-stu-id="a18bd-109">Behavior elements specific to Windows Workflow activities, such as the [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) element, are documented in the [\<behavior> of \<serviceBehaviors>](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) page.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="a18bd-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a18bd-110">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a18bd-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a18bd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a18bd-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a18bd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a18bd-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a18bd-113">Attributes</span></span>  
  
|<span data-ttu-id="a18bd-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a18bd-114">Attribute</span></span>|<span data-ttu-id="a18bd-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a18bd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a18bd-116">name</span><span class="sxs-lookup"><span data-stu-id="a18bd-116">name</span></span>|<span data-ttu-id="a18bd-117">Jedinečný řetězec, který obsahuje název konfigurace chování.</span><span class="sxs-lookup"><span data-stu-id="a18bd-117">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="a18bd-118">Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element.</span><span class="sxs-lookup"><span data-stu-id="a18bd-118">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="a18bd-119">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="a18bd-119">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a18bd-120">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a18bd-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a18bd-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a18bd-121">Child Elements</span></span>  
  
|<span data-ttu-id="a18bd-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="a18bd-122">Element</span></span>|<span data-ttu-id="a18bd-123">Description</span><span class="sxs-lookup"><span data-stu-id="a18bd-123">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|<span data-ttu-id="a18bd-124">Obsahuje konfigurační data pro DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="a18bd-124">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<persistenceProvider>](persistenceprovider.md)|<span data-ttu-id="a18bd-125">Určuje typ používané implementace poskytovatele trvalosti a také časový limit pro operace trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="a18bd-125">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>|  
|[\<routing>](routing-of-servicebehavior.md)|<span data-ttu-id="a18bd-126">Poskytuje přístup ke směrovací službě za běhu, aby umožňoval dynamickou úpravu konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="a18bd-126">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|<span data-ttu-id="a18bd-127">Poskytuje prvek konfigurace pracovního postupu, který na úrovni služby zřídí platnost přenosu, zprávy nebo původce.</span><span class="sxs-lookup"><span data-stu-id="a18bd-127">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|<span data-ttu-id="a18bd-128">Určuje nastavení, které autorizují přístup k operacím služby.</span><span class="sxs-lookup"><span data-stu-id="a18bd-128">Specifies settings that authorize access to service operations.</span></span>|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="a18bd-129">Určuje přihlašovací údaje, které se mají použít při ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="a18bd-129">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>|  
|[\<serviceDebug>](servicedebug.md)|<span data-ttu-id="a18bd-130">Určuje funkce ladění a informací o nápovědě pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a18bd-130">Specifies debugging and help information features for a Windows Communication Foundation (WCF) service.</span></span>|  
|[\<serviceDiscovery>](servicediscovery.md)|<span data-ttu-id="a18bd-131">Určuje zjistitelnost koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="a18bd-131">Specifies the discoverability of service endpoints.</span></span>|  
|[\<serviceMetadata>](servicemetadata.md)|<span data-ttu-id="a18bd-132">Určuje publikování metadat služby a přidružených informací.</span><span class="sxs-lookup"><span data-stu-id="a18bd-132">Specifies the publication of service metadata and associated information.</span></span>|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|<span data-ttu-id="a18bd-133">Určuje nastavení, které povoluje auditování událostí zabezpečení během operací služby.</span><span class="sxs-lookup"><span data-stu-id="a18bd-133">Specifies settings that enable auditing of security events during service operations.</span></span>|  
|[\<serviceThrottling>](servicethrottling.md)|<span data-ttu-id="a18bd-134">Určuje mechanismus omezování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="a18bd-134">Specifies the throttling mechanism of a WCF service.</span></span>|  
|[\<serviceTimeouts>](servicetimeouts.md)|<span data-ttu-id="a18bd-135">Určuje časový limit služby.</span><span class="sxs-lookup"><span data-stu-id="a18bd-135">Specifies the timeout for a service.</span></span>|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="a18bd-136">Určuje nastavení pro instanci aktivity typu WorkflowRuntime pro hostování služeb WCF založených na pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="a18bd-136">Specifies settings for an instance of WorkflowRuntime for hosting workflow-based WCF services.</span></span>|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="a18bd-137">Umožňuje načtení informací o adrese metadat ze záhlaví zpráv požadavku.</span><span class="sxs-lookup"><span data-stu-id="a18bd-137">Enables the retrieval of metadata address information from the request message headers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a18bd-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a18bd-138">Parent Elements</span></span>  
  
|<span data-ttu-id="a18bd-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="a18bd-139">Element</span></span>|<span data-ttu-id="a18bd-140">Description</span><span class="sxs-lookup"><span data-stu-id="a18bd-140">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="a18bd-141">Kolekce elementů chování služby.</span><span class="sxs-lookup"><span data-stu-id="a18bd-141">A collection of service behavior elements.</span></span>|
