---
title: '&lt;Diagnostika&gt;'
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 0854ce6525fd7c96cf7c19d2c86dadef1b9a53bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiagnosticsgt"></a><span data-ttu-id="b22ac-102">&lt;Diagnostika&gt;</span><span class="sxs-lookup"><span data-stu-id="b22ac-102">&lt;diagnostics&gt;</span></span>
<span data-ttu-id="b22ac-103">`diagnostics` Element definuje nastavení, které lze použít správce pro spuštění kontroly a řízení.</span><span class="sxs-lookup"><span data-stu-id="b22ac-103">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="b22ac-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b22ac-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b22ac-105">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="b22ac-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b22ac-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b22ac-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <diagnostics 
      etwProviderId="String"       
      performanceCounters="Off/ServiceOnly/All/Default"              
      wmiProviderEnabled="Boolean" >       
    <endToEndTracing 
        activityTracing="Boolean"  
        messageFlowTracing="Boolean"  
        propagateActivity="Boolean" />  
    <messageLogging 
        logEntireMessage="Boolean"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b22ac-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b22ac-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b22ac-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b22ac-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b22ac-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="b22ac-109">Attributes</span></span>  
  
|<span data-ttu-id="b22ac-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="b22ac-110">Attribute</span></span>|<span data-ttu-id="b22ac-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b22ac-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b22ac-112">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="b22ac-112">etwProviderId</span></span>|<span data-ttu-id="b22ac-113">Řetězec, který určuje identifikátor pro zprostředkovatele trasování událostí, která zapisuje události relací trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="b22ac-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="b22ac-114">čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="b22ac-114">performanceCounters</span></span>|<span data-ttu-id="b22ac-115">Určuje, zda jsou povoleny čítače výkonu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="b22ac-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="b22ac-116">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="b22ac-116">Valid values are</span></span><br /><br /> <span data-ttu-id="b22ac-117">-Vypnutí: Čítače výkonu jsou zakázány.</span><span class="sxs-lookup"><span data-stu-id="b22ac-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="b22ac-118">-ServiceOnly: Je povoleno pouze čítače výkonu relevantní pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="b22ac-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="b22ac-119">-Všechny: Výkonu čítače lze zobrazit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="b22ac-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="b22ac-120">-Výchozí: Je vytvořen _WCF_Admin instance čítače výkonu jeden.</span><span class="sxs-lookup"><span data-stu-id="b22ac-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="b22ac-121">Tato instance slouží k povolení shromažďování těchto dat SQM pro používá infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="b22ac-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="b22ac-122">Žádná z hodnoty čítače pro tuto instanci jsou aktualizovány a proto zůstanou na nule.</span><span class="sxs-lookup"><span data-stu-id="b22ac-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="b22ac-123">Toto je výchozí hodnota, pokud není k dispozici pro WCF žádná konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b22ac-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="b22ac-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="b22ac-124">wmiProviderEnabled</span></span>|<span data-ttu-id="b22ac-125">Logická hodnota, která určuje, zda je povoleno zprostředkovatele rozhraní WMI pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="b22ac-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="b22ac-126">Zprostředkovatel rozhraní WMI pro uživatele je potřeba k získání přístupu spuštění kontroly a řízení funkcí služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b22ac-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="b22ac-127">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b22ac-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b22ac-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b22ac-128">Child Elements</span></span>  
  
|<span data-ttu-id="b22ac-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="b22ac-129">Element</span></span>|<span data-ttu-id="b22ac-130">Popis</span><span class="sxs-lookup"><span data-stu-id="b22ac-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b22ac-131">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="b22ac-131">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="b22ac-132">Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování během spuštění aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="b22ac-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="b22ac-133">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="b22ac-133">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="b22ac-134">Popisuje nastavení pro protokolování zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="b22ac-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b22ac-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b22ac-135">Parent Elements</span></span>  
  
|<span data-ttu-id="b22ac-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="b22ac-136">Element</span></span>|<span data-ttu-id="b22ac-137">Popis</span><span class="sxs-lookup"><span data-stu-id="b22ac-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b22ac-138">ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b22ac-138">serviceModel</span></span>|<span data-ttu-id="b22ac-139">Kořenový element všechny konfigurační prvky WCF.</span><span class="sxs-lookup"><span data-stu-id="b22ac-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b22ac-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b22ac-140">Remarks</span></span>  
 <span data-ttu-id="b22ac-141">`diagnostics` Oddíl definuje nastavení diagnostiky pro všechny služby, které jsou umístěné v sestavení.</span><span class="sxs-lookup"><span data-stu-id="b22ac-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="b22ac-142">Není možné definovat nastavení samostatné diagnostiky na úrovni služby, pokud existuje jenom jedna služba v sestavení.</span><span class="sxs-lookup"><span data-stu-id="b22ac-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="b22ac-143">Atributy se nastavují v souladu s požadavky oddílu.</span><span class="sxs-lookup"><span data-stu-id="b22ac-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b22ac-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="b22ac-144">Example</span></span>  
  
```xml  
<diagnostics
    wmiProviderEnabled="false"  
    performanceCounters="all">  
  <messageLogging 
      logEntireMessage="true"  
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
  
## <a name="see-also"></a><span data-ttu-id="b22ac-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="b22ac-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>
