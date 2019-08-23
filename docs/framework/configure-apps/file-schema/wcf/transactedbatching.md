---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 12369f1053638583a3864fab396869d0e7045732
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918668"
---
# <a name="transactedbatching"></a><span data-ttu-id="b14d9-101">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="b14d9-101">\<transactedBatching></span></span>

<span data-ttu-id="b14d9-102">Určuje, zda je pro operace Receive podporována dávkování transakcí.</span><span class="sxs-lookup"><span data-stu-id="b14d9-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="b14d9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b14d9-103">\<system.ServiceModel></span></span>\
<span data-ttu-id="b14d9-104">\<> chování </span><span class="sxs-lookup"><span data-stu-id="b14d9-104">\<behaviors></span></span>\
<span data-ttu-id="b14d9-105">\<endpointBehaviors > </span><span class="sxs-lookup"><span data-stu-id="b14d9-105">\<endpointBehaviors></span></span>\
<span data-ttu-id="b14d9-106">\<chování > </span><span class="sxs-lookup"><span data-stu-id="b14d9-106">\<behavior></span></span>\
<span data-ttu-id="b14d9-107">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="b14d9-107">\<transactedBatching></span></span>

## <a name="syntax"></a><span data-ttu-id="b14d9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b14d9-108">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b14d9-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b14d9-109">Attributes and Elements</span></span>

<span data-ttu-id="b14d9-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b14d9-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b14d9-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b14d9-111">Attributes</span></span>

|<span data-ttu-id="b14d9-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b14d9-112">Attribute</span></span>|<span data-ttu-id="b14d9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b14d9-113">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="b14d9-114">Celé číslo, které určuje maximální počet operací příjmu, které mohou být v jedné transakci dávkově spojeny.</span><span class="sxs-lookup"><span data-stu-id="b14d9-114">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="b14d9-115">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="b14d9-115">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b14d9-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b14d9-116">Child Elements</span></span>

<span data-ttu-id="b14d9-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="b14d9-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b14d9-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b14d9-118">Parent Elements</span></span>

|<span data-ttu-id="b14d9-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="b14d9-119">Element</span></span>|<span data-ttu-id="b14d9-120">Popis</span><span class="sxs-lookup"><span data-stu-id="b14d9-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b14d9-121">\<> chování</span><span class="sxs-lookup"><span data-stu-id="b14d9-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b14d9-122">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b14d9-122">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b14d9-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b14d9-123">Remarks</span></span>

<span data-ttu-id="b14d9-124">Přenos, který je nakonfigurován s dávkování transakce, se pokusí o dávkování několika operací Receive do jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="b14d9-124">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="b14d9-125">Tím se vyhnete poměrně vysokým nákladům na vytvoření transakce a jejím potvrzením v každé operaci přijetí.</span><span class="sxs-lookup"><span data-stu-id="b14d9-125">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="b14d9-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="b14d9-126">Example</span></span>

<span data-ttu-id="b14d9-127">Následující příklad ukazuje, jak přidat transakční chování dávkování do služby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b14d9-127">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
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

## <a name="see-also"></a><span data-ttu-id="b14d9-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b14d9-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
