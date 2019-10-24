---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773937"
---
# <a name="client"></a><span data-ttu-id="465fa-101">\<client ></span><span class="sxs-lookup"><span data-stu-id="465fa-101">\<client></span></span>
<span data-ttu-id="465fa-102">Element `client` definuje seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="465fa-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>

<span data-ttu-id="465fa-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="465fa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="465fa-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="465fa-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="465fa-105">&nbsp; &nbsp; &nbsp; &nbsp; **\<client >**</span><span class="sxs-lookup"><span data-stu-id="465fa-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**</span></span>

## <a name="syntax"></a><span data-ttu-id="465fa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="465fa-106">Syntax</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="465fa-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="465fa-107">Attributes and Elements</span></span>
 <span data-ttu-id="465fa-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="465fa-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="465fa-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="465fa-109">Attributes</span></span>
 <span data-ttu-id="465fa-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="465fa-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="465fa-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="465fa-111">Child Elements</span></span>

|<span data-ttu-id="465fa-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="465fa-112">Element</span></span>|<span data-ttu-id="465fa-113">Popis</span><span class="sxs-lookup"><span data-stu-id="465fa-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="465fa-114">\<endpoint ></span><span class="sxs-lookup"><span data-stu-id="465fa-114">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="465fa-115">Obsahuje kolekci elementů koncového bodu, které určují koncové body, ke kterým se může tento klient připojit.</span><span class="sxs-lookup"><span data-stu-id="465fa-115">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[<span data-ttu-id="465fa-116">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="465fa-116">\<metadata></span></span>](metadata.md)|<span data-ttu-id="465fa-117">Obsahuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="465fa-117">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="465fa-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="465fa-118">Parent Elements</span></span>

|<span data-ttu-id="465fa-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="465fa-119">Element</span></span>|<span data-ttu-id="465fa-120">Popis</span><span class="sxs-lookup"><span data-stu-id="465fa-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="465fa-121">\<system. serviceModel ></span><span class="sxs-lookup"><span data-stu-id="465fa-121">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="465fa-122">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="465fa-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="465fa-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="465fa-123">Remarks</span></span>
 <span data-ttu-id="465fa-124">Oddíl `client` definuje seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="465fa-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="465fa-125">Každý koncový bod uvedený v části klienta definuje vlastní vazbu, chování a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="465fa-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="465fa-126">Je jednoznačně identifikován kombinací atributů `name` a `contract`.</span><span class="sxs-lookup"><span data-stu-id="465fa-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="465fa-127">Klientský kód určuje `name` pro připojení ke koncovému bodu pro službu, kterou klient implementuje.</span><span class="sxs-lookup"><span data-stu-id="465fa-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="465fa-128">Pokud je atribut `name` vynechán, koncový bod funguje jako výchozí koncový bod pro kontrakt, který implementuje.</span><span class="sxs-lookup"><span data-stu-id="465fa-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="465fa-129">Kromě toho tato část také určuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="465fa-129">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="465fa-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="465fa-130">Example</span></span>

```xml
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```

## <a name="see-also"></a><span data-ttu-id="465fa-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="465fa-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="465fa-132">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="465fa-132">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="465fa-133">Klienti</span><span class="sxs-lookup"><span data-stu-id="465fa-133">Clients</span></span>](../../../wcf/feature-details/clients.md)
