---
title: '&lt;transactedBatching&gt;'
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: f56751ea3f8bdc9ecbeff57db835e5fc2edbb73e
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148445"
---
# <a name="lttransactedbatchinggt"></a><span data-ttu-id="4d9c8-102">&lt;transactedBatching&gt;</span><span class="sxs-lookup"><span data-stu-id="4d9c8-102">&lt;transactedBatching&gt;</span></span>
<span data-ttu-id="4d9c8-103">Určuje, zda jsou podporovány dávkové transakce pro operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="4d9c8-103">Specifies whether transaction batching is supported for receive operations.</span></span>  
  
 <span data-ttu-id="4d9c8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4d9c8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4d9c8-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4d9c8-105">\<behaviors></span></span>  
<span data-ttu-id="4d9c8-106">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4d9c8-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4d9c8-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4d9c8-107">\<behavior></span></span>  
<span data-ttu-id="4d9c8-108">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="4d9c8-108">\<transactedBatching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d9c8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d9c8-109">Syntax</span></span>  
  
```xml  
<transactedBatching maxBatchSize="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d9c8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4d9c8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4d9c8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4d9c8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d9c8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4d9c8-112">Attributes</span></span>  
  
|<span data-ttu-id="4d9c8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="4d9c8-113">Attribute</span></span>|<span data-ttu-id="4d9c8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4d9c8-114">Description</span></span>|  
|---------------|-----------------|  
|`maxBatchSize`|<span data-ttu-id="4d9c8-115">Celé číslo, které určuje maximální počet operací příjmu, které lze sjednotit společně v rámci jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="4d9c8-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="4d9c8-116">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="4d9c8-116">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d9c8-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4d9c8-117">Child Elements</span></span>  
 <span data-ttu-id="4d9c8-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="4d9c8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d9c8-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4d9c8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4d9c8-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="4d9c8-120">Element</span></span>|<span data-ttu-id="4d9c8-121">Popis</span><span class="sxs-lookup"><span data-stu-id="4d9c8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d9c8-122">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4d9c8-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4d9c8-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4d9c8-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d9c8-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d9c8-124">Remarks</span></span>  
 <span data-ttu-id="4d9c8-125">Přenos, který je nakonfigurovaný s transakcí dávkování pokusy o dávkové několik operací do jedné transakce příjmu.</span><span class="sxs-lookup"><span data-stu-id="4d9c8-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="4d9c8-126">Tímto způsobem, relativně vysoké náklady na vytváření transakcí a potvrzení v každé přijímat vyhnout operaci.</span><span class="sxs-lookup"><span data-stu-id="4d9c8-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d9c8-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d9c8-127">Example</span></span>  
 <span data-ttu-id="4d9c8-128">Následující příklad ukazuje, jak přidat chování dávkového zpracování do služby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="4d9c8-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
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
  
## <a name="see-also"></a><span data-ttu-id="4d9c8-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d9c8-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactedBatchingElement>  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
