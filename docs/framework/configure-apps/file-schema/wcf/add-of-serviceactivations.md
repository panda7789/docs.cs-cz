---
title: "&lt;add&gt; – &lt;serviceActivations&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c49845169265e48b232963ed5a2e6215be75d3fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a><span data-ttu-id="f86be-102">&lt;add&gt; – &lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="f86be-102">&lt;add&gt; of &lt;serviceActivations&gt;</span></span>
<span data-ttu-id="f86be-103">Konfigurace element, který umožňuje definovat nastavení aktivace virtuální služby, pomocí které jsou namapovány na vaše [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] typů služeb.</span><span class="sxs-lookup"><span data-stu-id="f86be-103">A configuration element that allows you to define virtual service activation settings that map to your [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service types.</span></span> <span data-ttu-id="f86be-104">Díky tomu je možné aktivovat služby hostované v WAS nebo IIS bez souborů .svc.</span><span class="sxs-lookup"><span data-stu-id="f86be-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="f86be-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f86be-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f86be-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f86be-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86be-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f86be-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f86be-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f86be-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f86be-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f86be-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f86be-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f86be-110">Attributes</span></span>  
  
|<span data-ttu-id="f86be-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f86be-111">Attribute</span></span>|<span data-ttu-id="f86be-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f86be-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f86be-113">objekt pro vytváření</span><span class="sxs-lookup"><span data-stu-id="f86be-113">factory</span></span>|<span data-ttu-id="f86be-114">Řetězec, který určuje název typu CLR objekt factory, který generuje element aktivace služby.</span><span class="sxs-lookup"><span data-stu-id="f86be-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|  
|<span data-ttu-id="f86be-115">service</span><span class="sxs-lookup"><span data-stu-id="f86be-115">service</span></span>|<span data-ttu-id="f86be-116">ServiceType, který implementuje službu (úplná kvalifikovaný Typename nebo krátké Typename (Pokud je umístěn ve složce App_Code).</span><span class="sxs-lookup"><span data-stu-id="f86be-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|  
|<span data-ttu-id="f86be-117">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="f86be-117">relativeAddress</span></span>|<span data-ttu-id="f86be-118">Relativní adresa v aktuální aplikaci služby IIS – například "Service.svc".</span><span class="sxs-lookup"><span data-stu-id="f86be-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="f86be-119">Tato relativní adresa WCF 4.0 musí obsahovat jeden z známé přípon (.svc, .xamlx,...). Žádný fyzický soubor musí existovat pro relativeUrl</span><span class="sxs-lookup"><span data-stu-id="f86be-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f86be-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f86be-120">Child Elements</span></span>  
 <span data-ttu-id="f86be-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="f86be-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f86be-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f86be-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f86be-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="f86be-123">Element</span></span>|<span data-ttu-id="f86be-124">Popis</span><span class="sxs-lookup"><span data-stu-id="f86be-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f86be-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f86be-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="f86be-126">Konfigurační oddíl, který popisuje nastavení aktivace.</span><span class="sxs-lookup"><span data-stu-id="f86be-126">A configuration section that describes activation settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f86be-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f86be-127">Remarks</span></span>  
 <span data-ttu-id="f86be-128">Následující příklad ukazuje, jak nakonfigurovat nastavení aktivace v souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="f86be-128">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
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
  
 <span data-ttu-id="f86be-129">Pomocí této konfigurace, můžete aktivovat GreetingService bez použití soubor SVC.</span><span class="sxs-lookup"><span data-stu-id="f86be-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="f86be-130">Všimněte si, že `<serviceHostingEnvironment>` je konfigurace na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="f86be-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="f86be-131">Je nutné umístit `web.config` obsahující konfiguraci kořenovém virtuální aplikace.</span><span class="sxs-lookup"><span data-stu-id="f86be-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="f86be-132">Kromě toho `serviceHostingEnvironment` je machinetoApplication zděditelné oddíl.</span><span class="sxs-lookup"><span data-stu-id="f86be-132">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="f86be-133">Když si zaregistrujete jedné služby v kořenu počítače, zdědí všechny služby v aplikaci tuto službu.</span><span class="sxs-lookup"><span data-stu-id="f86be-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="f86be-134">Aktivace podle konfigurace podporuje aktivaci přes protokol http a jiným protokolem než http.</span><span class="sxs-lookup"><span data-stu-id="f86be-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="f86be-135">To vyžaduje rozšíření v relatativeAddress, tj. .svc, XOML nebo .xamlx.</span><span class="sxs-lookup"><span data-stu-id="f86be-135">It requires extensions in the relatativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="f86be-136">Vlastní rozšíření můžete namapovat buildProviders přehled, který budete pak moci aktivace služby přes jakoukoli příponu.</span><span class="sxs-lookup"><span data-stu-id="f86be-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="f86be-137">Při konfliktu `<serviceActivations>` části přepsání .svc registrace.</span><span class="sxs-lookup"><span data-stu-id="f86be-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f86be-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="f86be-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
