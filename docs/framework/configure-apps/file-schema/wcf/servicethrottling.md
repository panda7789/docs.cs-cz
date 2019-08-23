---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 77ed5e91f09d9e658deeb7996baaca445b4e0c90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937112"
---
# <a name="servicethrottling"></a><span data-ttu-id="b6a69-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="b6a69-101">\<serviceThrottling></span></span>
<span data-ttu-id="b6a69-102">Určuje mechanismus omezování služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b6a69-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="b6a69-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b6a69-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b6a69-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="b6a69-104">\<behaviors></span></span>  
<span data-ttu-id="b6a69-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b6a69-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="b6a69-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="b6a69-106">\<behavior></span></span>  
<span data-ttu-id="b6a69-107">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="b6a69-107">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6a69-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6a69-108">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6a69-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b6a69-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b6a69-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b6a69-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6a69-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b6a69-111">Attributes</span></span>  
  
|<span data-ttu-id="b6a69-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b6a69-112">Attribute</span></span>|<span data-ttu-id="b6a69-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b6a69-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6a69-114">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="b6a69-114">maxConcurrentCalls</span></span>|<span data-ttu-id="b6a69-115">Kladné celé číslo omezující počet zpráv, které jsou aktuálně zpracovány v rámci <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b6a69-115">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="b6a69-116">Volání přesahující limit jsou zařazená do fronty.</span><span class="sxs-lookup"><span data-stu-id="b6a69-116">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="b6a69-117">Nastavení této hodnoty na 0 je ekvivalentem nastavení Int32. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="b6a69-117">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="b6a69-118">Výchozí hodnota je 16 × počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="b6a69-118">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="b6a69-119">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="b6a69-119">maxConcurrentInstances</span></span>|<span data-ttu-id="b6a69-120">Kladné celé číslo, které omezuje počet <xref:System.ServiceModel.InstanceContext> objektů, které jsou spouštěny v jednom okamžiku <xref:System.ServiceModel.ServiceHost>napříč.</span><span class="sxs-lookup"><span data-stu-id="b6a69-120">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="b6a69-121">Žádosti o vytvoření dalších instancí se zařadí do fronty a dokončí, když se uvolní slot pod limitem.</span><span class="sxs-lookup"><span data-stu-id="b6a69-121">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="b6a69-122">Výchozí hodnota je součet hodnot maxConcurrentSessions a MaxConcurrentCalls.</span><span class="sxs-lookup"><span data-stu-id="b6a69-122">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="b6a69-123">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="b6a69-123">maxConcurrentSessions</span></span>|<span data-ttu-id="b6a69-124">Kladné celé číslo omezující počet relací <xref:System.ServiceModel.ServiceHost> , které může objekt přijmout.</span><span class="sxs-lookup"><span data-stu-id="b6a69-124">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="b6a69-125">Služba bude přijímat připojení přesahující limit, ale budou aktivní jenom kanály pod limitem (zprávy se čtou z kanálu).</span><span class="sxs-lookup"><span data-stu-id="b6a69-125">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="b6a69-126">Nastavení této hodnoty na 0 je ekvivalentem nastavení Int32. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="b6a69-126">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="b6a69-127">Výchozí hodnota je 100 × počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="b6a69-127">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6a69-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b6a69-128">Child Elements</span></span>  
 <span data-ttu-id="b6a69-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="b6a69-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6a69-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b6a69-130">Parent Elements</span></span>  
  
|<span data-ttu-id="b6a69-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6a69-131">Element</span></span>|<span data-ttu-id="b6a69-132">Popis</span><span class="sxs-lookup"><span data-stu-id="b6a69-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6a69-133">\<> chování</span><span class="sxs-lookup"><span data-stu-id="b6a69-133">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b6a69-134">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="b6a69-134">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6a69-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6a69-135">Remarks</span></span>  
 <span data-ttu-id="b6a69-136">Omezení ovládacích prvků omezuje počet souběžných volání, instancí nebo relací, které zabrání přečerpání prostředků.</span><span class="sxs-lookup"><span data-stu-id="b6a69-136">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="b6a69-137">Trasování je zapsáno pokaždé, když je dosaženo hodnoty atributů.</span><span class="sxs-lookup"><span data-stu-id="b6a69-137">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="b6a69-138">První trasování je zapsáno jako varování.</span><span class="sxs-lookup"><span data-stu-id="b6a69-138">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6a69-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6a69-139">Example</span></span>  
 <span data-ttu-id="b6a69-140">Následující příklad konfigurace určuje, že služba omezuje maximální počet souběžných volání na 2 a maximální počet souběžných instancí na 10.</span><span class="sxs-lookup"><span data-stu-id="b6a69-140">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="b6a69-141">Podrobný příklad spuštění tohoto příkladu naleznete v tématu [omezování](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="b6a69-141">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="b6a69-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6a69-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="b6a69-143">Řízení výkonu služby WCF pomocí ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="b6a69-143">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
