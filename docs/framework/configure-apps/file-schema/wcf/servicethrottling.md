---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399567"
---
# \<serviceThrottling>
<span data-ttu-id="2f1a9-101">Určuje mechanismus omezování služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2f1a9-101">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**  
  
## <a name="syntax"></a><span data-ttu-id="2f1a9-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f1a9-102">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f1a9-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2f1a9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2f1a9-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f1a9-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="2f1a9-105">Attributes</span></span>  
  
|<span data-ttu-id="2f1a9-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="2f1a9-106">Attribute</span></span>|<span data-ttu-id="2f1a9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2f1a9-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f1a9-108">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="2f1a9-108">maxConcurrentCalls</span></span>|<span data-ttu-id="2f1a9-109">Kladné celé číslo omezující počet zpráv, které jsou aktuálně zpracovány v rámci <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="2f1a9-109">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="2f1a9-110">Volání přesahující limit jsou zařazená do fronty.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-110">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="2f1a9-111">Nastavení této hodnoty na 0 je ekvivalentem nastavení Int32. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-111">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="2f1a9-112">Výchozí hodnota je 16 × počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-112">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="2f1a9-113">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="2f1a9-113">maxConcurrentInstances</span></span>|<span data-ttu-id="2f1a9-114">Kladné celé číslo, které omezuje počet <xref:System.ServiceModel.InstanceContext> objektů, které jsou spouštěny v jednom okamžiku napříč <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="2f1a9-114">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="2f1a9-115">Žádosti o vytvoření dalších instancí se zařadí do fronty a dokončí, když se uvolní slot pod limitem.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-115">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="2f1a9-116">Výchozí hodnota je součet hodnot maxConcurrentSessions a MaxConcurrentCalls.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-116">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="2f1a9-117">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="2f1a9-117">maxConcurrentSessions</span></span>|<span data-ttu-id="2f1a9-118">Kladné celé číslo omezující počet relací, které <xref:System.ServiceModel.ServiceHost> může objekt přijmout.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-118">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="2f1a9-119">Služba bude přijímat připojení přesahující limit, ale budou aktivní jenom kanály pod limitem (zprávy se čtou z kanálu).</span><span class="sxs-lookup"><span data-stu-id="2f1a9-119">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="2f1a9-120">Nastavení této hodnoty na 0 je ekvivalentem nastavení Int32. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-120">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="2f1a9-121">Výchozí hodnota je 100 × počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-121">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f1a9-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2f1a9-122">Child Elements</span></span>  
 <span data-ttu-id="2f1a9-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="2f1a9-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f1a9-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2f1a9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2f1a9-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="2f1a9-125">Element</span></span>|<span data-ttu-id="2f1a9-126">Description</span><span class="sxs-lookup"><span data-stu-id="2f1a9-126">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2f1a9-127">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f1a9-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f1a9-128">Remarks</span></span>  
 <span data-ttu-id="2f1a9-129">Omezení ovládacích prvků omezuje počet souběžných volání, instancí nebo relací, které zabrání přečerpání prostředků.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-129">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="2f1a9-130">Trasování je zapsáno pokaždé, když je dosaženo hodnoty atributů.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-130">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="2f1a9-131">První trasování je zapsáno jako varování.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-131">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f1a9-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f1a9-132">Example</span></span>  
 <span data-ttu-id="2f1a9-133">Následující příklad konfigurace určuje, že služba omezuje maximální počet souběžných volání na 2 a maximální počet souběžných instancí na 10.</span><span class="sxs-lookup"><span data-stu-id="2f1a9-133">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="2f1a9-134">Podrobný příklad spuštění tohoto příkladu naleznete v tématu [omezování](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="2f1a9-134">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f1a9-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f1a9-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="2f1a9-136">Řízení výkonu služby WCF pomocí ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="2f1a9-136">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
