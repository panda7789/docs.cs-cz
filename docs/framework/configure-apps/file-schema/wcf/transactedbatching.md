---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399403"
---
# \<transactedBatching>

<span data-ttu-id="5bc01-101">Určuje, zda je pro operace Receive podporována dávkování transakcí.</span><span class="sxs-lookup"><span data-stu-id="5bc01-101">Specifies whether transaction batching is supported for receive operations.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**  

## <a name="syntax"></a><span data-ttu-id="5bc01-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bc01-102">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5bc01-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5bc01-103">Attributes and Elements</span></span>

<span data-ttu-id="5bc01-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5bc01-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5bc01-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="5bc01-105">Attributes</span></span>

|<span data-ttu-id="5bc01-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="5bc01-106">Attribute</span></span>|<span data-ttu-id="5bc01-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5bc01-107">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="5bc01-108">Celé číslo, které určuje maximální počet operací příjmu, které mohou být v jedné transakci dávkově spojeny.</span><span class="sxs-lookup"><span data-stu-id="5bc01-108">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="5bc01-109">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="5bc01-109">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5bc01-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5bc01-110">Child Elements</span></span>

<span data-ttu-id="5bc01-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="5bc01-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5bc01-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5bc01-112">Parent Elements</span></span>

|<span data-ttu-id="5bc01-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="5bc01-113">Element</span></span>|<span data-ttu-id="5bc01-114">Description</span><span class="sxs-lookup"><span data-stu-id="5bc01-114">Description</span></span>|
|-------------|-----------------|
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="5bc01-115">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="5bc01-115">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5bc01-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5bc01-116">Remarks</span></span>

<span data-ttu-id="5bc01-117">Přenos, který je nakonfigurován s dávkování transakce, se pokusí o dávkování několika operací Receive do jedné transakce.</span><span class="sxs-lookup"><span data-stu-id="5bc01-117">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="5bc01-118">Tím se vyhnete poměrně vysokým nákladům na vytvoření transakce a jejím potvrzením v každé operaci přijetí.</span><span class="sxs-lookup"><span data-stu-id="5bc01-118">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="5bc01-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="5bc01-119">Example</span></span>

<span data-ttu-id="5bc01-120">Následující příklad ukazuje, jak přidat transakční chování dávkování do služby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="5bc01-120">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5bc01-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="5bc01-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
