---
title: '&lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: c62f2bd1a34aca31ea9f9d5de17840f2967b269c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="019f3-102">&lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="019f3-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="019f3-103">Konfigurace element, který umožňuje přidat nastavení, které definují nastavení aktivace virtuální služby, pomocí které jsou namapovány na vaše typů služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="019f3-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="019f3-104">Díky tomu je možné aktivovat služby hostované v WAS nebo IIS bez souborů .svc.</span><span class="sxs-lookup"><span data-stu-id="019f3-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="019f3-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="019f3-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="019f3-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="019f3-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="019f3-107">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="019f3-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="019f3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="019f3-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="019f3-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="019f3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="019f3-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="019f3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="019f3-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="019f3-111">Attributes</span></span>  
 <span data-ttu-id="019f3-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="019f3-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="019f3-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="019f3-113">Child Elements</span></span>  
  
|<span data-ttu-id="019f3-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="019f3-114">Element</span></span>|<span data-ttu-id="019f3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="019f3-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="019f3-116">\<add></span><span class="sxs-lookup"><span data-stu-id="019f3-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="019f3-117">Přidá prvek konfigurace, který určuje aktivace aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="019f3-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="019f3-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="019f3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="019f3-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="019f3-119">Element</span></span>|<span data-ttu-id="019f3-120">Popis</span><span class="sxs-lookup"><span data-stu-id="019f3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="019f3-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="019f3-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="019f3-122">Definuje typ, který vytvoří instanci služby hostování prostředí konkrétního přenosu.</span><span class="sxs-lookup"><span data-stu-id="019f3-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="019f3-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="019f3-123">Remarks</span></span>  
 <span data-ttu-id="019f3-124">Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="019f3-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
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
  
 <span data-ttu-id="019f3-125">Pomocí této konfigurace, můžete aktivovat GreetingService bez použití soubor SVC.</span><span class="sxs-lookup"><span data-stu-id="019f3-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="019f3-126">Všimněte si, že `<serviceHostingEnvironment>` je konfigurace na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="019f3-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="019f3-127">Je nutné umístit `web.config` obsahující konfiguraci kořenovém virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="019f3-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="019f3-128">Kromě toho `serviceHostingEnvironment` je machinetoApplication zděditelné oddíl.</span><span class="sxs-lookup"><span data-stu-id="019f3-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="019f3-129">Když si zaregistrujete jedné služby v kořenu počítače, zdědí všechny služby v aplikaci tuto službu.</span><span class="sxs-lookup"><span data-stu-id="019f3-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="019f3-130">Aktivace podle konfigurace podporuje aktivaci přes protokol http a jiným protokolem než http.</span><span class="sxs-lookup"><span data-stu-id="019f3-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="019f3-131">To vyžaduje rozšíření v relatativeAddress tj .svc, XOML nebo .xamlx.</span><span class="sxs-lookup"><span data-stu-id="019f3-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="019f3-132">Vlastní rozšíření můžete namapovat buildProviders přehled, který budete pak moci aktivace služby přes jakoukoli příponu.</span><span class="sxs-lookup"><span data-stu-id="019f3-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="019f3-133">Při konfliktu `<serviceActivations>` části přepsání .svc registrace.</span><span class="sxs-lookup"><span data-stu-id="019f3-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="019f3-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="019f3-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
