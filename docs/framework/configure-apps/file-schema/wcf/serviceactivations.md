---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 7a091ecfbc0f4773ece620f93a9f21c219fcccb6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256701"
---
# <a name="serviceactivations"></a><span data-ttu-id="d8ae9-101">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="d8ae9-101">\<serviceActivations></span></span>
<span data-ttu-id="d8ae9-102">Konfigurace element, který slouží k přidání nastavení, jenž definuje nastavení aktivace virtuální služby, která je namapována na daný typ služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d8ae9-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="d8ae9-103">To umožňuje aktivovat službám hostovaným ve WAS / IIS bez souboru .svc.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="d8ae9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d8ae9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d8ae9-105">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="d8ae9-105">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="d8ae9-106">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="d8ae9-106">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ae9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8ae9-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8ae9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d8ae9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d8ae9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8ae9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d8ae9-110">Attributes</span></span>  
 <span data-ttu-id="d8ae9-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="d8ae9-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8ae9-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d8ae9-112">Child Elements</span></span>  
  
|<span data-ttu-id="d8ae9-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8ae9-113">Element</span></span>|<span data-ttu-id="d8ae9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d8ae9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8ae9-115">\<add></span><span class="sxs-lookup"><span data-stu-id="d8ae9-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="d8ae9-116">Přidá prvek konfigurace, který určuje aktivace aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-116">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8ae9-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d8ae9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d8ae9-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8ae9-118">Element</span></span>|<span data-ttu-id="d8ae9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d8ae9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8ae9-120">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="d8ae9-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="d8ae9-121">Definuje typ, který vytvoří instanci hostitelským prostředím služby pro konkrétní přenos.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8ae9-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8ae9-122">Remarks</span></span>  
 <span data-ttu-id="d8ae9-123">Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-123">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="d8ae9-124">Pomocí této konfigurace, můžete aktivovat GreetingService bez použití souboru .svc.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-124">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="d8ae9-125">Všimněte si, že `<serviceHostingEnvironment>` je konfigurace na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-125">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="d8ae9-126">Je nutné umístit `web.config` obsahující konfiguraci v kořenu virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-126">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="d8ae9-127">Kromě toho `serviceHostingEnvironment` machinetoApplication odvoditelný oddíl.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-127">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="d8ae9-128">Když si zaregistrujete jedinou službou v kořenové složce na počítači, každá služba aplikace zdědí tuto službu.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-128">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="d8ae9-129">Aktivace podle konfigurace podporuje aktivaci přes protokol http a jiným protokolem než http.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-129">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="d8ae9-130">Vyžaduje rozšíření v relatativeAddress, tj. .svc, XOML nebo .xamlx.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-130">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="d8ae9-131">Vlastní rozšíření můžete namapovat buildProviders ví, která vám pak umožní k aktivaci služby přes jakékoli rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-131">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="d8ae9-132">Při konfliktu `<serviceActivations>` části přepíše .svc registrace.</span><span class="sxs-lookup"><span data-stu-id="d8ae9-132">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ae9-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8ae9-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
