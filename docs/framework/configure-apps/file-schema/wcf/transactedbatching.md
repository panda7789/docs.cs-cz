---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 43415d9eac5e61f42006aecb3248dec9811eb3e6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366450"
---
# <a name="transactedbatching"></a><span data-ttu-id="258d1-101">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="258d1-101">\<transactedBatching></span></span>

<span data-ttu-id="258d1-102">Určuje, zda jsou podporovány dávkové transakce pro operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="258d1-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="258d1-103">\<system.ServiceModel>\\</span><span class="sxs-lookup"><span data-stu-id="258d1-103">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="258d1-104">\<chování > \\</span><span class="sxs-lookup"><span data-stu-id="258d1-104">\<behaviors>\\</span></span>
<span data-ttu-id="258d1-105">\<endpointBehaviors>\\</span><span class="sxs-lookup"><span data-stu-id="258d1-105">\<endpointBehaviors>\\</span></span>
<span data-ttu-id="258d1-106">\<chování > \\</span><span class="sxs-lookup"><span data-stu-id="258d1-106">\<behavior>\\</span></span>
<span data-ttu-id="258d1-107">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="258d1-107">\<transactedBatching></span></span>

## <a name="syntax"></a><span data-ttu-id="258d1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="258d1-108">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="258d1-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="258d1-109">Attributes and Elements</span></span>

<span data-ttu-id="258d1-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="258d1-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="258d1-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="258d1-111">Attributes</span></span>

|<span data-ttu-id="258d1-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="258d1-112">Attribute</span></span>|<span data-ttu-id="258d1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="258d1-113">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="258d1-114">Celé číslo, které určuje maximální počet operací příjmu, které lze sjednotit společně v rámci jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="258d1-114">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="258d1-115">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="258d1-115">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="258d1-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="258d1-116">Child Elements</span></span>

<span data-ttu-id="258d1-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="258d1-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="258d1-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="258d1-118">Parent Elements</span></span>

|<span data-ttu-id="258d1-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="258d1-119">Element</span></span>|<span data-ttu-id="258d1-120">Popis</span><span class="sxs-lookup"><span data-stu-id="258d1-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="258d1-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="258d1-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="258d1-122">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="258d1-122">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="258d1-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="258d1-123">Remarks</span></span>

<span data-ttu-id="258d1-124">Přenos, který je nakonfigurovaný s transakcí dávkování pokusy o dávkové několik operací do jedné transakce příjmu.</span><span class="sxs-lookup"><span data-stu-id="258d1-124">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="258d1-125">Tímto způsobem, relativně vysoké náklady na vytváření transakcí a potvrzení v každé přijímat vyhnout operaci.</span><span class="sxs-lookup"><span data-stu-id="258d1-125">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="258d1-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="258d1-126">Example</span></span>

<span data-ttu-id="258d1-127">Následující příklad ukazuje, jak přidat chování dávkového zpracování do služby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="258d1-127">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="258d1-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="258d1-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
