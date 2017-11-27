---
title: '&lt;transactedBatching&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: edeb10a1a7fa540b3f3e6ef4bf1a4a820fbc1b4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="1a83d-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="1a83d-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="1a83d-103">Určuje, zda je podporováno dávkové zpracování transakcí, pro operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="1a83d-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="1a83d-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1a83d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1a83d-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1a83d-105">\<behaviors></span></span>  
<span data-ttu-id="1a83d-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1a83d-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1a83d-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1a83d-107">\<behavior></span></span>  
<span data-ttu-id="1a83d-108">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="1a83d-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a83d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a83d-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a83d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1a83d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1a83d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1a83d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a83d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1a83d-112">Attributes</span></span>  
  
|<span data-ttu-id="1a83d-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1a83d-113">Attribute</span></span>|<span data-ttu-id="1a83d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1a83d-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="1a83d-115">Celé číslo, které určuje maximální počet operací, které lze zpracovat v dávce přijímat společně v jedné transakci.</span><span class="sxs-lookup"><span data-stu-id="1a83d-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="1a83d-116">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="1a83d-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a83d-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1a83d-117">Child Elements</span></span>  
 <span data-ttu-id="1a83d-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="1a83d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a83d-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1a83d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1a83d-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="1a83d-120">Element</span></span>|<span data-ttu-id="1a83d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1a83d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a83d-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1a83d-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="1a83d-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1a83d-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a83d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a83d-124">Remarks</span></span>  
 <span data-ttu-id="1a83d-125">Přenos, který je nakonfigurovaný s transakční dávkování pokusy o dávky několik přijímat operací do jedné transakci.</span><span class="sxs-lookup"><span data-stu-id="1a83d-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="1a83d-126">Díky tomu poměrně vysoké náklady na vytvoření transakce a potvrzení v každé přijímat operaci se vyhnout.</span><span class="sxs-lookup"><span data-stu-id="1a83d-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a83d-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a83d-127">Example</span></span>  
 <span data-ttu-id="1a83d-128">Následující příklad ukazuje, jak přidat chování dávkového zpracování do služby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="1a83d-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <host>  
        <baseAddresses>  
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
        </baseAddresses>  
      </host>  
  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />  
  
      <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange" />  
    </service>  
  </services>  
  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="endpointBehavior">  
        <transactedBatching maxBatchSize="10" />  
      </behavior>  
    </endpointBehaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a83d-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a83d-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
