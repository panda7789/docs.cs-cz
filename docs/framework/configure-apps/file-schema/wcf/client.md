---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7dce5984882e48c3e62efc44ef00b6256d9eb64e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919529"
---
# <a name="client"></a><span data-ttu-id="caf0a-101">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="caf0a-101">\<client></span></span>
<span data-ttu-id="caf0a-102">`client` Prvek definuje seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="caf0a-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="caf0a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="caf0a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="caf0a-104">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="caf0a-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caf0a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caf0a-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="caf0a-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="caf0a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="caf0a-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="caf0a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="caf0a-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="caf0a-108">Attributes</span></span>  
 <span data-ttu-id="caf0a-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="caf0a-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="caf0a-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="caf0a-110">Child Elements</span></span>  
  
|<span data-ttu-id="caf0a-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="caf0a-111">Element</span></span>|<span data-ttu-id="caf0a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="caf0a-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="caf0a-113">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="caf0a-113">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="caf0a-114">Obsahuje kolekci elementů koncového bodu, které určují koncové body, ke kterým se může tento klient připojit.</span><span class="sxs-lookup"><span data-stu-id="caf0a-114">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="caf0a-115">\<metadata></span><span class="sxs-lookup"><span data-stu-id="caf0a-115">\<metadata></span></span>](metadata.md)|<span data-ttu-id="caf0a-116">Obsahuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="caf0a-116">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="caf0a-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="caf0a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="caf0a-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="caf0a-118">Element</span></span>|<span data-ttu-id="caf0a-119">Popis</span><span class="sxs-lookup"><span data-stu-id="caf0a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="caf0a-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="caf0a-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="caf0a-121">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="caf0a-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caf0a-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="caf0a-122">Remarks</span></span>  
 <span data-ttu-id="caf0a-123">`client` Oddíl definuje seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="caf0a-123">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="caf0a-124">Každý koncový bod uvedený v části klienta definuje vlastní vazbu, chování a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="caf0a-124">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="caf0a-125">Je jednoznačně identifikován kombinací `name` atributů a. `contract`</span><span class="sxs-lookup"><span data-stu-id="caf0a-125">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="caf0a-126">Kód klienta Určuje, že `name` se má připojit ke koncovému bodu pro službu, kterou klient implementuje.</span><span class="sxs-lookup"><span data-stu-id="caf0a-126">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="caf0a-127">Pokud je `name` atribut vynechán, koncový bod funguje jako výchozí koncový bod pro kontrakt, který implementuje.</span><span class="sxs-lookup"><span data-stu-id="caf0a-127">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="caf0a-128">Kromě toho tato část také určuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="caf0a-128">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="caf0a-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="caf0a-129">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="caf0a-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="caf0a-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="caf0a-131">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="caf0a-131">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="caf0a-132">Klienti</span><span class="sxs-lookup"><span data-stu-id="caf0a-132">Clients</span></span>](../../../wcf/feature-details/clients.md)
