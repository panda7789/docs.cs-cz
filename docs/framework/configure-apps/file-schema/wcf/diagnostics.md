---
title: '&lt;Diagnostika&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d558bf6ac71a3a19fb8c28989fd9262e7a13f0f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiagnosticsgt"></a><span data-ttu-id="52a45-102">&lt;Diagnostika&gt;</span><span class="sxs-lookup"><span data-stu-id="52a45-102">&lt;diagnostics&gt;</span></span>
<span data-ttu-id="52a45-103">`diagnostics` Element definuje nastavení, které lze použít správce pro spuštění kontroly a řízení.</span><span class="sxs-lookup"><span data-stu-id="52a45-103">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="52a45-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="52a45-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="52a45-105">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="52a45-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a45-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52a45-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics etwProviderId="String"       performanceCounters="Off/ServiceOnly/All/Default"              wmiProviderEnabled="Boolean" >       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
          maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
             <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52a45-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="52a45-107">Attributes and Elements</span></span>  
 <span data-ttu-id="52a45-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="52a45-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52a45-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="52a45-109">Attributes</span></span>  
  
|<span data-ttu-id="52a45-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="52a45-110">Attribute</span></span>|<span data-ttu-id="52a45-111">Popis</span><span class="sxs-lookup"><span data-stu-id="52a45-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52a45-112">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="52a45-112">etwProviderId</span></span>|<span data-ttu-id="52a45-113">Řetězec, který určuje identifikátor pro zprostředkovatele trasování událostí, která zapisuje události relací trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="52a45-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="52a45-114">čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="52a45-114">performanceCounters</span></span>|<span data-ttu-id="52a45-115">Určuje, zda jsou povoleny čítače výkonu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="52a45-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="52a45-116">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="52a45-116">Valid values are</span></span><br /><br /> <span data-ttu-id="52a45-117">-Vypnutí: Čítače výkonu jsou zakázány.</span><span class="sxs-lookup"><span data-stu-id="52a45-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="52a45-118">-ServiceOnly: Je povoleno pouze čítače výkonu relevantní pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="52a45-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="52a45-119">-Všechny: Výkonu čítače lze zobrazit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="52a45-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="52a45-120">-Výchozí: Je vytvořen _WCF_Admin instance čítače výkonu jeden.</span><span class="sxs-lookup"><span data-stu-id="52a45-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="52a45-121">Tato instance slouží k povolení shromažďování těchto dat SQM pro používá infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="52a45-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="52a45-122">Žádná z hodnoty čítače pro tuto instanci jsou aktualizovány a proto zůstanou na nule.</span><span class="sxs-lookup"><span data-stu-id="52a45-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="52a45-123">Toto je výchozí hodnota, pokud není k dispozici pro WCF žádná konfigurace.</span><span class="sxs-lookup"><span data-stu-id="52a45-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="52a45-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="52a45-124">wmiProviderEnabled</span></span>|<span data-ttu-id="52a45-125">Logická hodnota, která určuje, zda je povoleno zprostředkovatele rozhraní WMI pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="52a45-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="52a45-126">Zprostředkovatel rozhraní WMI pro uživatele je potřeba k získání přístupu spuštění kontroly a řízení funkcí služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="52a45-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="52a45-127">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="52a45-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52a45-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="52a45-128">Child Elements</span></span>  
  
|<span data-ttu-id="52a45-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="52a45-129">Element</span></span>|<span data-ttu-id="52a45-130">Popis</span><span class="sxs-lookup"><span data-stu-id="52a45-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52a45-131">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="52a45-131">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="52a45-132">Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování během spuštění aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="52a45-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="52a45-133">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="52a45-133">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="52a45-134">Popisuje nastavení pro protokolování zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="52a45-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52a45-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="52a45-135">Parent Elements</span></span>  
  
|<span data-ttu-id="52a45-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="52a45-136">Element</span></span>|<span data-ttu-id="52a45-137">Popis</span><span class="sxs-lookup"><span data-stu-id="52a45-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52a45-138">ServiceModel</span><span class="sxs-lookup"><span data-stu-id="52a45-138">serviceModel</span></span>|<span data-ttu-id="52a45-139">Kořenový element všechny konfigurační prvky WCF.</span><span class="sxs-lookup"><span data-stu-id="52a45-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52a45-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52a45-140">Remarks</span></span>  
 <span data-ttu-id="52a45-141">`diagnostics` Oddíl definuje nastavení diagnostiky pro všechny služby, které jsou umístěné v sestavení.</span><span class="sxs-lookup"><span data-stu-id="52a45-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="52a45-142">Není možné definovat nastavení samostatné diagnostiky na úrovni služby, pokud existuje jenom jedna služba v sestavení.</span><span class="sxs-lookup"><span data-stu-id="52a45-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="52a45-143">Atributy se nastavují v souladu s požadavky oddílu.</span><span class="sxs-lookup"><span data-stu-id="52a45-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52a45-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="52a45-144">Example</span></span>  
  
```xml  
<diagnostics wmiProviderEnabled="false"  
       performanceCounters="all">  
       <messageLogging logEntireMessage="true"  
          logMalformedMessages="true"  
          logMessagesAtServiceLevel="true"  
          logMessagesAtTransportLevel="true"  
          maxMessagesToLog="42"  
          maxSizeOfMessageToLog="42">  
         <filters>  
         <clear />  
    </filters>  
       </messageLogging>  
</diagnostics>  
```  
  
## <a name="see-also"></a><span data-ttu-id="52a45-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="52a45-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>
