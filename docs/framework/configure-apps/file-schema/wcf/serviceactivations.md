---
title: '&lt;serviceActivations&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 43461f23476d1c387cec06f9aee893defa634201
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="43236-102">&lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="43236-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="43236-103">Konfigurace element, který umožňuje přidat nastavení, které definují nastavení aktivace virtuální služby, pomocí které jsou namapovány na vaše [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] typů služeb.</span><span class="sxs-lookup"><span data-stu-id="43236-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service types.</span></span> <span data-ttu-id="43236-104">Díky tomu je možné aktivovat služby hostované v WAS nebo IIS bez souborů .svc.</span><span class="sxs-lookup"><span data-stu-id="43236-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="43236-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="43236-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="43236-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="43236-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="43236-107">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="43236-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43236-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43236-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43236-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="43236-109">Attributes and Elements</span></span>  
 <span data-ttu-id="43236-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="43236-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43236-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="43236-111">Attributes</span></span>  
 <span data-ttu-id="43236-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="43236-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43236-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="43236-113">Child Elements</span></span>  
  
|<span data-ttu-id="43236-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="43236-114">Element</span></span>|<span data-ttu-id="43236-115">Popis</span><span class="sxs-lookup"><span data-stu-id="43236-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43236-116">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="43236-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="43236-117">Přidá prvek konfigurace, který určuje aktivace aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="43236-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43236-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="43236-118">Parent Elements</span></span>  
  
|<span data-ttu-id="43236-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="43236-119">Element</span></span>|<span data-ttu-id="43236-120">Popis</span><span class="sxs-lookup"><span data-stu-id="43236-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43236-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="43236-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="43236-122">Definuje typ, který vytvoří instanci služby hostování prostředí konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="43236-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43236-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43236-123">Remarks</span></span>  
 <span data-ttu-id="43236-124">Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="43236-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="43236-125">Pomocí této konfigurace, můžete aktivovat GreetingService bez použití soubor SVC.</span><span class="sxs-lookup"><span data-stu-id="43236-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="43236-126">Všimněte si, že `<serviceHostingEnvironment>` je konfigurace na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="43236-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="43236-127">Je nutné umístit `web.config` obsahující konfiguraci kořenovém virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="43236-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="43236-128">Kromě toho `serviceHostingEnvironment` je machinetoApplication zděditelné oddíl.</span><span class="sxs-lookup"><span data-stu-id="43236-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="43236-129">Když si zaregistrujete jedné služby v kořenu počítače, zdědí všechny služby v aplikaci tuto službu.</span><span class="sxs-lookup"><span data-stu-id="43236-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="43236-130">Aktivace podle konfigurace podporuje aktivaci přes protokol http a jiným protokolem než http.</span><span class="sxs-lookup"><span data-stu-id="43236-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="43236-131">To vyžaduje rozšíření v relatativeAddress tj .svc, XOML nebo .xamlx.</span><span class="sxs-lookup"><span data-stu-id="43236-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="43236-132">Vlastní rozšíření můžete namapovat buildProviders přehled, který budete pak moci aktivace služby přes jakoukoli příponu.</span><span class="sxs-lookup"><span data-stu-id="43236-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="43236-133">Při konfliktu `<serviceActivations>` části přepsání .svc registrace.</span><span class="sxs-lookup"><span data-stu-id="43236-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43236-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="43236-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
