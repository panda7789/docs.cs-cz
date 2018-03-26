---
title: '&lt;serviceThrottling&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a059684967af26c72aca48a3fa6bb10c2f26b0c5
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="ltservicethrottlinggt"></a><span data-ttu-id="7b74b-102">&lt;serviceThrottling&gt;</span><span class="sxs-lookup"><span data-stu-id="7b74b-102">&lt;serviceThrottling&gt;</span></span>
<span data-ttu-id="7b74b-103">Určuje omezení mechanismus služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7b74b-103">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="7b74b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7b74b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b74b-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7b74b-105">\<behaviors></span></span>  
<span data-ttu-id="7b74b-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7b74b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7b74b-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7b74b-107">\<behavior></span></span>  
<span data-ttu-id="7b74b-108">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="7b74b-108">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b74b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b74b-109">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"  
    maxConcurrentInstances="Integer"  
    maxConcurrentSessions="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b74b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7b74b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7b74b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7b74b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b74b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7b74b-112">Attributes</span></span>  
  
|<span data-ttu-id="7b74b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7b74b-113">Attribute</span></span>|<span data-ttu-id="7b74b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7b74b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b74b-115">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="7b74b-115">maxConcurrentCalls</span></span>|<span data-ttu-id="7b74b-116">Kladné celé číslo, který omezuje počet zpráv, které aktuálně zpracovávají napříč <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7b74b-116">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="7b74b-117">Volání nad tento limit jsou zařazeny do fronty.</span><span class="sxs-lookup"><span data-stu-id="7b74b-117">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="7b74b-118">Tuto hodnotu nastavíte na 0 je stejné jako jeho nastavení na Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="7b74b-118">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="7b74b-119">Výchozí hodnota je 16 \* počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="7b74b-119">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="7b74b-120">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="7b74b-120">maxConcurrentInstances</span></span>|<span data-ttu-id="7b74b-121">Kladné celé číslo, které omezuje počet <xref:System.ServiceModel.InstanceContext> objekty, které jsou spouštěny v jednu chvíli napříč <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7b74b-121">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="7b74b-122">Požadavky na vytvoření další instance jsou zařazeny do fronty a dokončit při slot pod limit bude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7b74b-122">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="7b74b-123">Výchozí hodnota je součtem maxConcurrentSessions a MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="7b74b-123">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="7b74b-124">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="7b74b-124">maxConcurrentSessions</span></span>|<span data-ttu-id="7b74b-125">Kladné celé číslo, který omezuje počet relací <xref:System.ServiceModel.ServiceHost> může přijmout objekt.</span><span class="sxs-lookup"><span data-stu-id="7b74b-125">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="7b74b-126">Služba bude akceptovat připojení nad tento limit, ale jsou aktivní pouze kanály pod limit (zprávy se načítají z kanál).</span><span class="sxs-lookup"><span data-stu-id="7b74b-126">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="7b74b-127">Tuto hodnotu nastavíte na 0 je stejné jako jeho nastavení na Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="7b74b-127">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="7b74b-128">Výchozí hodnota je 100 \* počet procesorů.</span><span class="sxs-lookup"><span data-stu-id="7b74b-128">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b74b-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7b74b-129">Child Elements</span></span>  
 <span data-ttu-id="7b74b-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="7b74b-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b74b-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7b74b-131">Parent Elements</span></span>  
  
|<span data-ttu-id="7b74b-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="7b74b-132">Element</span></span>|<span data-ttu-id="7b74b-133">Popis</span><span class="sxs-lookup"><span data-stu-id="7b74b-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b74b-134">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7b74b-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="7b74b-135">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="7b74b-135">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b74b-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b74b-136">Remarks</span></span>  
 <span data-ttu-id="7b74b-137">Omezení ovládacích prvků umístit omezení na počet souběžných volání, instancí nebo relací, aby se zabránilo nadměrné spotřeby prostředků.</span><span class="sxs-lookup"><span data-stu-id="7b74b-137">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="7b74b-138">Trasování je zapsán pokaždé, když je dosaženo hodnoty atributů.</span><span class="sxs-lookup"><span data-stu-id="7b74b-138">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="7b74b-139">První trasování bude zapsáno jako upozornění.</span><span class="sxs-lookup"><span data-stu-id="7b74b-139">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b74b-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b74b-140">Example</span></span>  
 <span data-ttu-id="7b74b-141">Následující příklad konfigurace určuje, že služba omezuje maximální souběžných volání 2 a maximální počet souběžných instancí do 10.</span><span class="sxs-lookup"><span data-stu-id="7b74b-141">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="7b74b-142">Podrobný příklad spuštěných v tomto příkladu najdete v tématu [omezování](../../../../../docs/framework/wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="7b74b-142">For a detailed example of running this example, see [Throttling](../../../../../docs/framework/wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>   
  <serviceBehaviors>   
    <behavior name="CalculatorServiceBehavior">   
      <serviceDebug includeExceptionDetailInFaults="False" />   
      <serviceMetadata httpGetEnabled="True"/>   
      <!-- Specify throttling behavior -->  
      <serviceThrottling maxConcurrentCalls="2"   
           maxConcurrentInstances="10"/>   
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b74b-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b74b-143">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>  
 [<span data-ttu-id="7b74b-144">Řízení výkonu služby WCF pomocí ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="7b74b-144">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
