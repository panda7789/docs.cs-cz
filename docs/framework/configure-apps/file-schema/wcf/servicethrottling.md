---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 995ff9979096757225c9241e977f86f755955945
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158766"
---
# <a name="servicethrottling"></a><span data-ttu-id="429e8-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="429e8-101">\<serviceThrottling></span></span>
<span data-ttu-id="429e8-102">Určuje mechanismus omezení služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="429e8-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="429e8-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="429e8-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="429e8-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="429e8-104">\<behaviors></span></span>  
<span data-ttu-id="429e8-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="429e8-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="429e8-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="429e8-106">\<behavior></span></span>  
<span data-ttu-id="429e8-107">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="429e8-107">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="429e8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="429e8-108">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="429e8-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="429e8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="429e8-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="429e8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="429e8-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="429e8-111">Attributes</span></span>  
  
|<span data-ttu-id="429e8-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="429e8-112">Attribute</span></span>|<span data-ttu-id="429e8-113">Popis</span><span class="sxs-lookup"><span data-stu-id="429e8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="429e8-114">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="429e8-114">maxConcurrentCalls</span></span>|<span data-ttu-id="429e8-115">Kladné celé číslo omezující počet zpráv, které právě zpracovat přes <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="429e8-115">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="429e8-116">Volání nad tento limit se zařadí do fronty.</span><span class="sxs-lookup"><span data-stu-id="429e8-116">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="429e8-117">Tuto hodnotu nastavíte na 0 je rovnocenná ji nastavíte na hodnotu Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="429e8-117">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="429e8-118">Výchozí hodnota je 16 \* počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="429e8-118">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="429e8-119">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="429e8-119">maxConcurrentInstances</span></span>|<span data-ttu-id="429e8-120">Kladné celé číslo omezující počet <xref:System.ServiceModel.InstanceContext> objekty, které jsou spuštěny v jednu chvíli napříč <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="429e8-120">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="429e8-121">Požadavky na vytvoření další instance se zařadí do fronty a dokončit, jakmile je k dispozici slot pod limit.</span><span class="sxs-lookup"><span data-stu-id="429e8-121">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="429e8-122">Výchozí hodnota je součtem maxConcurrentSessions a MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="429e8-122">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="429e8-123">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="429e8-123">maxConcurrentSessions</span></span>|<span data-ttu-id="429e8-124">Kladné celé číslo omezující počet relací <xref:System.ServiceModel.ServiceHost> může přijmout objekt.</span><span class="sxs-lookup"><span data-stu-id="429e8-124">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="429e8-125">Služba bude akceptovat připojení nad tento limit, ale pouze kanály pod limit jsou aktivní (zprávy načtené z kanálu).</span><span class="sxs-lookup"><span data-stu-id="429e8-125">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="429e8-126">Tuto hodnotu nastavíte na 0 je rovnocenná ji nastavíte na hodnotu Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="429e8-126">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="429e8-127">Výchozí hodnota je 100 \* počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="429e8-127">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="429e8-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="429e8-128">Child Elements</span></span>  
 <span data-ttu-id="429e8-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="429e8-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="429e8-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="429e8-130">Parent Elements</span></span>  
  
|<span data-ttu-id="429e8-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="429e8-131">Element</span></span>|<span data-ttu-id="429e8-132">Popis</span><span class="sxs-lookup"><span data-stu-id="429e8-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="429e8-133">\<behavior></span><span class="sxs-lookup"><span data-stu-id="429e8-133">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="429e8-134">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="429e8-134">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="429e8-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="429e8-135">Remarks</span></span>  
 <span data-ttu-id="429e8-136">Omezení ovládacích prvků umístit omezení na počtu souběžných volání, instance nebo relace, aby se zabránilo typu over-pass-the spotřebu prostředků.</span><span class="sxs-lookup"><span data-stu-id="429e8-136">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="429e8-137">Trasování bude zapsáno pokaždé, když je dosaženo hodnoty atributů.</span><span class="sxs-lookup"><span data-stu-id="429e8-137">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="429e8-138">První trasování bude zapsáno jako upozornění.</span><span class="sxs-lookup"><span data-stu-id="429e8-138">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="429e8-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="429e8-139">Example</span></span>  
 <span data-ttu-id="429e8-140">Následující příklad konfigurace určuje, že služba omezuje maximální souběžných volání 2 a maximální počet souběžných instancí do 10.</span><span class="sxs-lookup"><span data-stu-id="429e8-140">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="429e8-141">Podrobný příklad spuštěním tohoto příkladu, naleznete v tématu [omezování](../../../../../docs/framework/wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="429e8-141">For a detailed example of running this example, see [Throttling](../../../../../docs/framework/wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="429e8-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="429e8-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="429e8-143">Řízení výkonu služby WCF pomocí ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="429e8-143">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
