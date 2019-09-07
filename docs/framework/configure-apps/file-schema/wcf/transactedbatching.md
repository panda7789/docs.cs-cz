---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399403"
---
# <a name="transactedbatching"></a><span data-ttu-id="ec028-101">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="ec028-101">\<transactedBatching></span></span>

<span data-ttu-id="ec028-102">Určuje, zda je pro operace Receive podporována dávkování transakcí.</span><span class="sxs-lookup"><span data-stu-id="ec028-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="ec028-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ec028-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ec028-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ec028-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ec028-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ec028-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ec028-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ec028-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="ec028-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ec028-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="ec028-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transactedBatching >**</span><span class="sxs-lookup"><span data-stu-id="ec028-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="ec028-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec028-109">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec028-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ec028-110">Attributes and Elements</span></span>

<span data-ttu-id="ec028-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ec028-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec028-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="ec028-112">Attributes</span></span>

|<span data-ttu-id="ec028-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="ec028-113">Attribute</span></span>|<span data-ttu-id="ec028-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ec028-114">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="ec028-115">Celé číslo, které určuje maximální počet operací příjmu, které mohou být v jedné transakci dávkově spojeny.</span><span class="sxs-lookup"><span data-stu-id="ec028-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="ec028-116">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="ec028-116">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ec028-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ec028-117">Child Elements</span></span>

<span data-ttu-id="ec028-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="ec028-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ec028-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ec028-119">Parent Elements</span></span>

|<span data-ttu-id="ec028-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="ec028-120">Element</span></span>|<span data-ttu-id="ec028-121">Popis</span><span class="sxs-lookup"><span data-stu-id="ec028-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ec028-122">\<> chování</span><span class="sxs-lookup"><span data-stu-id="ec028-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ec028-123">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ec028-123">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ec028-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec028-124">Remarks</span></span>

<span data-ttu-id="ec028-125">Přenos, který je nakonfigurován s dávkování transakce, se pokusí o dávkování několika operací Receive do jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="ec028-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="ec028-126">Tím se vyhnete poměrně vysokým nákladům na vytvoření transakce a jejím potvrzením v každé operaci přijetí.</span><span class="sxs-lookup"><span data-stu-id="ec028-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="ec028-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec028-127">Example</span></span>

<span data-ttu-id="ec028-128">Následující příklad ukazuje, jak přidat transakční chování dávkování do služby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ec028-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ec028-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec028-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
