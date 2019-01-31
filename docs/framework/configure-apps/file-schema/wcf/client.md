---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 93365c109f015b2ec72b5216dcb8c46258d022e2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280901"
---
# <a name="client"></a><span data-ttu-id="74b02-101">\<client></span><span class="sxs-lookup"><span data-stu-id="74b02-101">\<client></span></span>
<span data-ttu-id="74b02-102">`client` Element definuje seznam koncových bodů, které se klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="74b02-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="74b02-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="74b02-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="74b02-104">\<client></span><span class="sxs-lookup"><span data-stu-id="74b02-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74b02-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74b02-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74b02-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74b02-106">Attributes and Elements</span></span>  
 <span data-ttu-id="74b02-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74b02-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74b02-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="74b02-108">Attributes</span></span>  
 <span data-ttu-id="74b02-109">Žádná</span><span class="sxs-lookup"><span data-stu-id="74b02-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="74b02-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="74b02-110">Child Elements</span></span>  
  
|<span data-ttu-id="74b02-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="74b02-111">Element</span></span>|<span data-ttu-id="74b02-112">Popis</span><span class="sxs-lookup"><span data-stu-id="74b02-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74b02-113">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="74b02-113">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="74b02-114">Obsahuje kolekci prvků koncového bodu, které určovat koncové body, které tento klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="74b02-114">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="74b02-115">\<metadata></span><span class="sxs-lookup"><span data-stu-id="74b02-115">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="74b02-116">Obsahuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="74b02-116">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74b02-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="74b02-117">Parent Elements</span></span>  
  
|<span data-ttu-id="74b02-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="74b02-118">Element</span></span>|<span data-ttu-id="74b02-119">Popis</span><span class="sxs-lookup"><span data-stu-id="74b02-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74b02-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="74b02-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="74b02-121">Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="74b02-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74b02-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74b02-122">Remarks</span></span>  
 <span data-ttu-id="74b02-123">`client` Oddíl definuje seznam koncových bodů, které se klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="74b02-123">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="74b02-124">Každý koncový bod uvedený v oddílu klienta definuje vlastní vazby, chování a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="74b02-124">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="74b02-125">Je jedinečně identifikovaný kombinací `name` a `contract` atributy.</span><span class="sxs-lookup"><span data-stu-id="74b02-125">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="74b02-126">Určuje kód klienta `name` pro připojení na koncový bod služby, který implementuje klienta.</span><span class="sxs-lookup"><span data-stu-id="74b02-126">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="74b02-127">Pokud `name` atribut je vynechán, koncový bod chová jako výchozího koncového bodu pro kontrakt jej implementuje.</span><span class="sxs-lookup"><span data-stu-id="74b02-127">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="74b02-128">Kromě toho tato část také určuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="74b02-128">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74b02-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="74b02-129">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74b02-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74b02-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="74b02-131">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="74b02-131">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="74b02-132">Klienti</span><span class="sxs-lookup"><span data-stu-id="74b02-132">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
