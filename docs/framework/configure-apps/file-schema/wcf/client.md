---
title: '&lt;Klienta&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: b8a006d3dee4149569b3f5b573d9d765504b0d65
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752634"
---
# <a name="ltclientgt"></a><span data-ttu-id="74ee8-102">&lt;Klienta&gt;</span><span class="sxs-lookup"><span data-stu-id="74ee8-102">&lt;client&gt;</span></span>
<span data-ttu-id="74ee8-103">`client` Element definuje seznam koncových bodů, které klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="74ee8-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="74ee8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="74ee8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="74ee8-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="74ee8-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74ee8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74ee8-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74ee8-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74ee8-107">Attributes and Elements</span></span>  
 <span data-ttu-id="74ee8-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74ee8-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74ee8-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="74ee8-109">Attributes</span></span>  
 <span data-ttu-id="74ee8-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="74ee8-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="74ee8-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="74ee8-111">Child Elements</span></span>  
  
|<span data-ttu-id="74ee8-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="74ee8-112">Element</span></span>|<span data-ttu-id="74ee8-113">Popis</span><span class="sxs-lookup"><span data-stu-id="74ee8-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74ee8-114">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="74ee8-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="74ee8-115">Obsahuje kolekci elementů koncový bod, které určují koncové body, které tento klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="74ee8-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="74ee8-116">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="74ee8-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="74ee8-117">Obsahuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="74ee8-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74ee8-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="74ee8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="74ee8-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="74ee8-119">Element</span></span>|<span data-ttu-id="74ee8-120">Popis</span><span class="sxs-lookup"><span data-stu-id="74ee8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74ee8-121">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="74ee8-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="74ee8-122">Kořenový element všechny konfigurační prvky Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="74ee8-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74ee8-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74ee8-123">Remarks</span></span>  
 <span data-ttu-id="74ee8-124">`client` Oddíl definuje seznam koncových bodů, které klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="74ee8-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="74ee8-125">Každý koncový bod uvedený v oddílu klienta definuje vlastní vazby, chování a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="74ee8-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="74ee8-126">Je jedinečně identifikovaný kombinací `name` a `contract` atributy.</span><span class="sxs-lookup"><span data-stu-id="74ee8-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="74ee8-127">Určuje kód klienta `name` pro připojení k koncový bod služby, který implementuje klienta.</span><span class="sxs-lookup"><span data-stu-id="74ee8-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="74ee8-128">Pokud `name` atribut vynechán, koncový bod funguje jako výchozí koncový bod pro daný kontrakt se implementuje.</span><span class="sxs-lookup"><span data-stu-id="74ee8-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="74ee8-129">Kromě toho tato část také určuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="74ee8-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74ee8-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="74ee8-130">Example</span></span>  
  
```xml  
<client>  
    <endpoint address="/HelloWorld/"  
              bindingConfiguration="usingDefaults"  
              name="MyBinding"  
              binding="customBinding"  
              contract="HelloWorld">  
    <addressProperties actingAs="http://www.microsoft.com/TestActor"  
             identityData="BasicReadWrite" identityType="Spn" isAddressPrivate="false">  
    </endpoint>  
</client>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74ee8-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="74ee8-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="74ee8-132">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="74ee8-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="74ee8-133">Klienti</span><span class="sxs-lookup"><span data-stu-id="74ee8-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
