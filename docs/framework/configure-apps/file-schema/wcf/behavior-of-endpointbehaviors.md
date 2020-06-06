---
title: <behavior> z <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: 489678a5adeae3965acae90a847c4b087478354d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140808"
---
# <a name="behavior-of-endpointbehaviors"></a><span data-ttu-id="69680-102">\<behavior> z \<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="69680-102">\<behavior> of \<endpointBehaviors></span></span>
<span data-ttu-id="69680-103">`behavior`Element obsahuje kolekci nastavení chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="69680-103">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="69680-104">Každý chování je indexované podle jeho `name`.</span><span class="sxs-lookup"><span data-stu-id="69680-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="69680-105">Koncové body se můžou propojit s každým chováním prostřednictvím tohoto názvu.</span><span class="sxs-lookup"><span data-stu-id="69680-105">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="69680-106">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="69680-106">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="69680-107">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="69680-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="69680-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69680-108">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69680-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="69680-109">Attributes and Elements</span></span>  
 <span data-ttu-id="69680-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="69680-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69680-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="69680-111">Attributes</span></span>  
  
|<span data-ttu-id="69680-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="69680-112">Attribute</span></span>|<span data-ttu-id="69680-113">Popis</span><span class="sxs-lookup"><span data-stu-id="69680-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69680-114">name</span><span class="sxs-lookup"><span data-stu-id="69680-114">name</span></span>|<span data-ttu-id="69680-115">Jedinečný řetězec, který obsahuje název konfigurace chování.</span><span class="sxs-lookup"><span data-stu-id="69680-115">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="69680-116">Tato hodnota je uživatelem definovaný řetězec, který musí být jedinečný, protože funguje jako identifikační řetězec pro element.</span><span class="sxs-lookup"><span data-stu-id="69680-116">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="69680-117">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="69680-117">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="69680-118">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="69680-118">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69680-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="69680-119">Child Elements</span></span>  
  
|<span data-ttu-id="69680-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="69680-120">Element</span></span>|<span data-ttu-id="69680-121">Description</span><span class="sxs-lookup"><span data-stu-id="69680-121">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="69680-122">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="69680-122">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[\<callbackDebug>](callbackdebug.md)|<span data-ttu-id="69680-123">Určuje ladění služby pro objekt zpětného volání služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="69680-123">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>|  
|[\<callbackTimeouts>](callbacktimeouts.md)|<span data-ttu-id="69680-124">Určuje časový limit zpětného volání klienta.</span><span class="sxs-lookup"><span data-stu-id="69680-124">Specifies the timeout for the client callback.</span></span>|  
|[\<clientVia>](clientvia.md)|<span data-ttu-id="69680-125">Určuje trasu, kterou by měla zpráva trvat.</span><span class="sxs-lookup"><span data-stu-id="69680-125">Specifies the route a message should take.</span></span>|  
|[\<dataContractSerializer>](datacontractserializer.md)|<span data-ttu-id="69680-126">Obsahuje konfigurační data pro DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="69680-126">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|<span data-ttu-id="69680-127">Určuje chování koncového bodu, které umožňuje službě odesílat odpovědi asynchronně.</span><span class="sxs-lookup"><span data-stu-id="69680-127">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[\<enableWebScript>](enablewebscript.md)|<span data-ttu-id="69680-128">Umožňuje chování koncového bodu, které umožňuje využívat službu z webových stránek ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="69680-128">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="69680-129">Chování by mělo být použito pouze ve spojení se \<webHttpBinding> standardní vazbou nebo \<webMessageEncoding> prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="69680-129">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="69680-130">Určuje různá nastavení zjišťování pro koncový bod, například jeho zjistitelnost, obory a jakákoli vlastní rozšíření pro jeho metadata.</span><span class="sxs-lookup"><span data-stu-id="69680-130">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[\<soapProcessing>](soapprocessing.md)|<span data-ttu-id="69680-131">Definuje chování koncového bodu klienta používaného k zařazování zpráv mezi různými typy vazeb a verzemi zpráv.</span><span class="sxs-lookup"><span data-stu-id="69680-131">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[\<synchronousReceive>](synchronousreceive-element.md)|<span data-ttu-id="69680-132">Určuje chování za běhu pro příjem zpráv v klientské aplikaci nebo službě.</span><span class="sxs-lookup"><span data-stu-id="69680-132">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="69680-133">Neobsahuje žádné atributy ani podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="69680-133">It does not have any attributes or child elements.</span></span>|  
|[\<transactedBatching>](transactedbatching.md)|<span data-ttu-id="69680-134">Určuje, zda je pro operace Receive podporována dávkování transakcí.</span><span class="sxs-lookup"><span data-stu-id="69680-134">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[\<webHttp>](webhttp.md)|<span data-ttu-id="69680-135">Určuje WebHttpBehavior na koncovém bodu prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="69680-135">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="69680-136">Toto chování, při použití ve spojení se \<webHttpBinding> standardní vazbou, umožňuje model webového programování pro službu WCF.</span><span class="sxs-lookup"><span data-stu-id="69680-136">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a WCF service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69680-137">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="69680-137">Parent Elements</span></span>  
  
|<span data-ttu-id="69680-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="69680-138">Element</span></span>|<span data-ttu-id="69680-139">Description</span><span class="sxs-lookup"><span data-stu-id="69680-139">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="69680-140">Kolekce elementů chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="69680-140">A collection of endpoint behavior elements.</span></span>|
