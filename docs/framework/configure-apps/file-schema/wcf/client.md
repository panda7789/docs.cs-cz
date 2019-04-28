---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 2e0352efdd5b709984338fe4484b120bddb7d545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704294"
---
# <a name="client"></a><span data-ttu-id="bcae9-101">\<client></span><span class="sxs-lookup"><span data-stu-id="bcae9-101">\<client></span></span>
<span data-ttu-id="bcae9-102">`client` Element definuje seznam koncových bodů, které se klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="bcae9-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="bcae9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bcae9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bcae9-104">\<client></span><span class="sxs-lookup"><span data-stu-id="bcae9-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcae9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcae9-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcae9-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bcae9-106">Attributes and Elements</span></span>  
 <span data-ttu-id="bcae9-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bcae9-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcae9-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="bcae9-108">Attributes</span></span>  
 <span data-ttu-id="bcae9-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="bcae9-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bcae9-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bcae9-110">Child Elements</span></span>  
  
|<span data-ttu-id="bcae9-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="bcae9-111">Element</span></span>|<span data-ttu-id="bcae9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bcae9-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcae9-113">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="bcae9-113">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="bcae9-114">Obsahuje kolekci prvků koncového bodu, které určovat koncové body, které tento klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="bcae9-114">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="bcae9-115">\<metadata></span><span class="sxs-lookup"><span data-stu-id="bcae9-115">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="bcae9-116">Obsahuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="bcae9-116">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bcae9-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bcae9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="bcae9-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="bcae9-118">Element</span></span>|<span data-ttu-id="bcae9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="bcae9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcae9-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bcae9-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="bcae9-121">Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bcae9-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcae9-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcae9-122">Remarks</span></span>  
 <span data-ttu-id="bcae9-123">`client` Oddíl definuje seznam koncových bodů, které se klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="bcae9-123">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="bcae9-124">Každý koncový bod uvedený v oddílu klienta definuje vlastní vazby, chování a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="bcae9-124">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="bcae9-125">Je jedinečně identifikovaný kombinací `name` a `contract` atributy.</span><span class="sxs-lookup"><span data-stu-id="bcae9-125">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="bcae9-126">Určuje kód klienta `name` pro připojení na koncový bod služby, který implementuje klienta.</span><span class="sxs-lookup"><span data-stu-id="bcae9-126">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="bcae9-127">Pokud `name` atribut je vynechán, koncový bod chová jako výchozího koncového bodu pro kontrakt jej implementuje.</span><span class="sxs-lookup"><span data-stu-id="bcae9-127">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="bcae9-128">Kromě toho tato část také určuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="bcae9-128">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcae9-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcae9-129">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bcae9-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcae9-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="bcae9-131">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="bcae9-131">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="bcae9-132">Klienti</span><span class="sxs-lookup"><span data-stu-id="bcae9-132">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
