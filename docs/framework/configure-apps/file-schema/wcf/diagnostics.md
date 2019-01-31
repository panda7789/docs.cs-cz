---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 2041125e5bb538a9b64beb54778219c2a51a18f7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264706"
---
# <a name="diagnostics"></a><span data-ttu-id="58676-101">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="58676-101">\<diagnostics></span></span>
<span data-ttu-id="58676-102">`diagnostics` Prvek definuje nastavení, které můžete použít správce pro řízení a kontrolu za běhu.</span><span class="sxs-lookup"><span data-stu-id="58676-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="58676-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="58676-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="58676-104">\<Diagnostika ></span><span class="sxs-lookup"><span data-stu-id="58676-104">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58676-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58676-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58676-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="58676-106">Attributes and Elements</span></span>  
 <span data-ttu-id="58676-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="58676-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58676-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="58676-108">Attributes</span></span>  
  
|<span data-ttu-id="58676-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="58676-109">Attribute</span></span>|<span data-ttu-id="58676-110">Popis</span><span class="sxs-lookup"><span data-stu-id="58676-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58676-111">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="58676-111">etwProviderId</span></span>|<span data-ttu-id="58676-112">Řetězec určující identifikátor poskytovatele trasování událostí, která zapisuje události do relací ETW.</span><span class="sxs-lookup"><span data-stu-id="58676-112">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="58676-113">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="58676-113">performanceCounters</span></span>|<span data-ttu-id="58676-114">Určuje, zda jsou povoleny čítače výkonu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="58676-114">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="58676-115">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="58676-115">Valid values are</span></span><br /><br /> <span data-ttu-id="58676-116">-Vypnuto: Čítače výkonu jsou zakázány.</span><span class="sxs-lookup"><span data-stu-id="58676-116">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="58676-117">-ServiceOnly: Je povoleno pouze čítače výkonu relevantní pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="58676-117">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="58676-118">-Všechny: Čítače výkonu lze zobrazit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="58676-118">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="58676-119">– Výchozí hodnota: Je vytvořen _WCF_Admin instance čítače výkonu jediné.</span><span class="sxs-lookup"><span data-stu-id="58676-119">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="58676-120">Tato instance se používá k povolení shromažďování dat technologie SQM pro používá infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="58676-120">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="58676-121">Žádné hodnoty čítače pro tuto instanci se aktualizují a proto bude i nadále na nule.</span><span class="sxs-lookup"><span data-stu-id="58676-121">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="58676-122">Toto je výchozí hodnota, pokud není k dispozici pro službu WCF žádná konfigurace.</span><span class="sxs-lookup"><span data-stu-id="58676-122">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="58676-123">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="58676-123">wmiProviderEnabled</span></span>|<span data-ttu-id="58676-124">Logická hodnota, která určuje, zda je povolen zprostředkovatel rozhraní WMI pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="58676-124">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="58676-125">Zprostředkovatel rozhraní WMI pro uživatele je potřeba k získání přístupu za běhu k řízení a kontrolu funkce služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="58676-125">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="58676-126">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="58676-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58676-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="58676-127">Child Elements</span></span>  
  
|<span data-ttu-id="58676-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="58676-128">Element</span></span>|<span data-ttu-id="58676-129">Popis</span><span class="sxs-lookup"><span data-stu-id="58676-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58676-130">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="58676-130">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="58676-131">Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování za běhu aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="58676-131">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="58676-132">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="58676-132">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="58676-133">Popisuje nastavení pro protokolování zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="58676-133">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58676-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="58676-134">Parent Elements</span></span>  
  
|<span data-ttu-id="58676-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="58676-135">Element</span></span>|<span data-ttu-id="58676-136">Popis</span><span class="sxs-lookup"><span data-stu-id="58676-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58676-137">serviceModel</span><span class="sxs-lookup"><span data-stu-id="58676-137">serviceModel</span></span>|<span data-ttu-id="58676-138">Kořenový element všechny elementy konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="58676-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58676-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58676-139">Remarks</span></span>  
 <span data-ttu-id="58676-140">`diagnostics` Oddíl definuje nastavení diagnostiky pro všechny služby v sestavení.</span><span class="sxs-lookup"><span data-stu-id="58676-140">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="58676-141">Není možné definovat nastavení samostatné diagnostiky na úrovni služby, dokud není v sestavení pouze pro jednu službu.</span><span class="sxs-lookup"><span data-stu-id="58676-141">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="58676-142">Atributy se nastavují podle požadavků části.</span><span class="sxs-lookup"><span data-stu-id="58676-142">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58676-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="58676-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58676-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58676-144">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
