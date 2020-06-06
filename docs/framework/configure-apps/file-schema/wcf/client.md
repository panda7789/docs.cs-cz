---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "72773937"
---
# \<client>
<span data-ttu-id="d26f1-101">`client`Prvek definuje seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="d26f1-101">The `client` element defines a list of endpoints that a client can connect to.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a><span data-ttu-id="d26f1-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d26f1-102">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="d26f1-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d26f1-103">Attributes and Elements</span></span>
 <span data-ttu-id="d26f1-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d26f1-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d26f1-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="d26f1-105">Attributes</span></span>
 <span data-ttu-id="d26f1-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="d26f1-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="d26f1-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d26f1-107">Child Elements</span></span>

|<span data-ttu-id="d26f1-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="d26f1-108">Element</span></span>|<span data-ttu-id="d26f1-109">Description</span><span class="sxs-lookup"><span data-stu-id="d26f1-109">Description</span></span>|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="d26f1-110">Obsahuje kolekci elementů koncového bodu, které určují koncové body, ke kterým se může tento klient připojit.</span><span class="sxs-lookup"><span data-stu-id="d26f1-110">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[\<metadata>](metadata.md)|<span data-ttu-id="d26f1-111">Obsahuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="d26f1-111">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d26f1-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d26f1-112">Parent Elements</span></span>

|<span data-ttu-id="d26f1-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="d26f1-113">Element</span></span>|<span data-ttu-id="d26f1-114">Description</span><span class="sxs-lookup"><span data-stu-id="d26f1-114">Description</span></span>|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="d26f1-115">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d26f1-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d26f1-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d26f1-116">Remarks</span></span>
 <span data-ttu-id="d26f1-117">`client`Oddíl definuje seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="d26f1-117">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="d26f1-118">Každý koncový bod uvedený v části klienta definuje vlastní vazbu, chování a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="d26f1-118">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="d26f1-119">Je jednoznačně identifikován kombinací `name` `contract` atributů a.</span><span class="sxs-lookup"><span data-stu-id="d26f1-119">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="d26f1-120">Kód klienta Určuje, že se má `name` připojit ke koncovému bodu pro službu, kterou klient implementuje.</span><span class="sxs-lookup"><span data-stu-id="d26f1-120">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="d26f1-121">Pokud `name` je atribut vynechán, koncový bod funguje jako výchozí koncový bod pro kontrakt, který implementuje.</span><span class="sxs-lookup"><span data-stu-id="d26f1-121">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="d26f1-122">Kromě toho tato část také určuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="d26f1-122">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="d26f1-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="d26f1-123">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d26f1-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d26f1-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="d26f1-125">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="d26f1-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="d26f1-126">Klienti</span><span class="sxs-lookup"><span data-stu-id="d26f1-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
