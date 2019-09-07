---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399567"
---
# <a name="servicethrottling"></a><span data-ttu-id="2ed45-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="2ed45-101">\<serviceThrottling></span></span>
<span data-ttu-id="2ed45-102">Určuje mechanismus omezování služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2ed45-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
<span data-ttu-id="2ed45-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2ed45-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2ed45-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2ed45-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2ed45-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2ed45-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="2ed45-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2ed45-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="2ed45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2ed45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="2ed45-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceThrottling >**</span><span class="sxs-lookup"><span data-stu-id="2ed45-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ed45-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ed45-109">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ed45-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ed45-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2ed45-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ed45-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ed45-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ed45-112">Attributes</span></span>  
  
|<span data-ttu-id="2ed45-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2ed45-113">Attribute</span></span>|<span data-ttu-id="2ed45-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2ed45-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ed45-115">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="2ed45-115">maxConcurrentCalls</span></span>|<span data-ttu-id="2ed45-116">Kladné celé číslo omezující počet zpráv, které jsou aktuálně zpracovány v rámci <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="2ed45-116">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="2ed45-117">Volání přesahující limit jsou zařazená do fronty.</span><span class="sxs-lookup"><span data-stu-id="2ed45-117">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="2ed45-118">Nastavení této hodnoty na 0 je ekvivalentem nastavení Int32. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="2ed45-118">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="2ed45-119">Výchozí hodnota je 16 × počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="2ed45-119">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="2ed45-120">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="2ed45-120">maxConcurrentInstances</span></span>|<span data-ttu-id="2ed45-121">Kladné celé číslo, které omezuje počet <xref:System.ServiceModel.InstanceContext> objektů, které jsou spouštěny v jednom okamžiku <xref:System.ServiceModel.ServiceHost>napříč.</span><span class="sxs-lookup"><span data-stu-id="2ed45-121">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="2ed45-122">Žádosti o vytvoření dalších instancí se zařadí do fronty a dokončí, když se uvolní slot pod limitem.</span><span class="sxs-lookup"><span data-stu-id="2ed45-122">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="2ed45-123">Výchozí hodnota je součet hodnot maxConcurrentSessions a MaxConcurrentCalls.</span><span class="sxs-lookup"><span data-stu-id="2ed45-123">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="2ed45-124">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="2ed45-124">maxConcurrentSessions</span></span>|<span data-ttu-id="2ed45-125">Kladné celé číslo omezující počet relací <xref:System.ServiceModel.ServiceHost> , které může objekt přijmout.</span><span class="sxs-lookup"><span data-stu-id="2ed45-125">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="2ed45-126">Služba bude přijímat připojení přesahující limit, ale budou aktivní jenom kanály pod limitem (zprávy se čtou z kanálu).</span><span class="sxs-lookup"><span data-stu-id="2ed45-126">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="2ed45-127">Nastavení této hodnoty na 0 je ekvivalentem nastavení Int32. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="2ed45-127">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="2ed45-128">Výchozí hodnota je 100 × počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="2ed45-128">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ed45-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2ed45-129">Child Elements</span></span>  
 <span data-ttu-id="2ed45-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ed45-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ed45-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2ed45-131">Parent Elements</span></span>  
  
|<span data-ttu-id="2ed45-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ed45-132">Element</span></span>|<span data-ttu-id="2ed45-133">Popis</span><span class="sxs-lookup"><span data-stu-id="2ed45-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ed45-134">\<> chování</span><span class="sxs-lookup"><span data-stu-id="2ed45-134">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2ed45-135">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="2ed45-135">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ed45-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ed45-136">Remarks</span></span>  
 <span data-ttu-id="2ed45-137">Omezení ovládacích prvků omezuje počet souběžných volání, instancí nebo relací, které zabrání přečerpání prostředků.</span><span class="sxs-lookup"><span data-stu-id="2ed45-137">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="2ed45-138">Trasování je zapsáno pokaždé, když je dosaženo hodnoty atributů.</span><span class="sxs-lookup"><span data-stu-id="2ed45-138">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="2ed45-139">První trasování je zapsáno jako varování.</span><span class="sxs-lookup"><span data-stu-id="2ed45-139">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ed45-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ed45-140">Example</span></span>  
 <span data-ttu-id="2ed45-141">Následující příklad konfigurace určuje, že služba omezuje maximální počet souběžných volání na 2 a maximální počet souběžných instancí na 10.</span><span class="sxs-lookup"><span data-stu-id="2ed45-141">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="2ed45-142">Podrobný příklad spuštění tohoto příkladu naleznete v tématu [omezování](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="2ed45-142">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ed45-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ed45-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="2ed45-144">Řízení výkonu služby WCF pomocí ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="2ed45-144">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
