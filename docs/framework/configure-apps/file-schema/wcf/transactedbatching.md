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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fc5d5cc77fcb227efd36106f1f8cb31efad24cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="ec52c-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="ec52c-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="ec52c-103">Určuje, zda je podporováno dávkové zpracování transakcí, pro operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="ec52c-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="ec52c-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ec52c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ec52c-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ec52c-105">\<behaviors></span></span>  
<span data-ttu-id="ec52c-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ec52c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ec52c-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ec52c-107">\<behavior></span></span>  
<span data-ttu-id="ec52c-108">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="ec52c-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec52c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec52c-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec52c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ec52c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ec52c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ec52c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec52c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="ec52c-112">Attributes</span></span>  
  
|<span data-ttu-id="ec52c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="ec52c-113">Attribute</span></span>|<span data-ttu-id="ec52c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ec52c-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="ec52c-115">Celé číslo, které určuje maximální počet operací, které lze zpracovat v dávce přijímat společně v jedné transakci.</span><span class="sxs-lookup"><span data-stu-id="ec52c-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="ec52c-116">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="ec52c-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec52c-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ec52c-117">Child Elements</span></span>  
 <span data-ttu-id="ec52c-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="ec52c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec52c-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ec52c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ec52c-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="ec52c-120">Element</span></span>|<span data-ttu-id="ec52c-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ec52c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec52c-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ec52c-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ec52c-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ec52c-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec52c-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec52c-124">Remarks</span></span>  
 <span data-ttu-id="ec52c-125">Přenos, který je nakonfigurovaný s transakční dávkování pokusy o dávky několik přijímat operací do jedné transakci.</span><span class="sxs-lookup"><span data-stu-id="ec52c-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="ec52c-126">Díky tomu poměrně vysoké náklady na vytvoření transakce a potvrzení v každé přijímat operaci se vyhnout.</span><span class="sxs-lookup"><span data-stu-id="ec52c-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec52c-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec52c-127">Example</span></span>  
 <span data-ttu-id="ec52c-128">Následující příklad ukazuje, jak přidat chování dávkového zpracování do služby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ec52c-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ec52c-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec52c-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
