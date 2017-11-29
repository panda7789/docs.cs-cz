---
title: '&lt;klienta&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 67f91f4462fc8c11b1769d5805a4ad1407385a50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientgt"></a><span data-ttu-id="01149-102">&lt;klienta&gt;</span><span class="sxs-lookup"><span data-stu-id="01149-102">&lt;client&gt;</span></span>
<span data-ttu-id="01149-103">`client` Element definuje seznam koncových bodů, které klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="01149-103">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="01149-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="01149-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="01149-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="01149-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01149-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01149-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01149-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="01149-107">Attributes and Elements</span></span>  
 <span data-ttu-id="01149-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="01149-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01149-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="01149-109">Attributes</span></span>  
 <span data-ttu-id="01149-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="01149-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="01149-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="01149-111">Child Elements</span></span>  
  
|<span data-ttu-id="01149-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="01149-112">Element</span></span>|<span data-ttu-id="01149-113">Popis</span><span class="sxs-lookup"><span data-stu-id="01149-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01149-114">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="01149-114">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="01149-115">Obsahuje kolekci elementů koncový bod, které určují koncové body, které tento klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="01149-115">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="01149-116">\<metadata ></span><span class="sxs-lookup"><span data-stu-id="01149-116">\<metadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|<span data-ttu-id="01149-117">Obsahuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="01149-117">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01149-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="01149-118">Parent Elements</span></span>  
  
|<span data-ttu-id="01149-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="01149-119">Element</span></span>|<span data-ttu-id="01149-120">Popis</span><span class="sxs-lookup"><span data-stu-id="01149-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01149-121">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="01149-121">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="01149-122">Kořenový element všechny konfigurační prvky Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="01149-122">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01149-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01149-123">Remarks</span></span>  
 <span data-ttu-id="01149-124">`client` Oddíl definuje seznam koncových bodů, které klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="01149-124">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="01149-125">Každý koncový bod uvedený v oddílu klienta definuje vlastní vazby, chování a kontrakt.</span><span class="sxs-lookup"><span data-stu-id="01149-125">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="01149-126">Je jedinečně identifikovaný kombinací `name` a `contract` atributy.</span><span class="sxs-lookup"><span data-stu-id="01149-126">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="01149-127">Určuje kód klienta `name` pro připojení k koncový bod služby, který implementuje klienta.</span><span class="sxs-lookup"><span data-stu-id="01149-127">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="01149-128">Pokud `name` atribut vynechán, koncový bod funguje jako výchozí koncový bod pro daný kontrakt se implementuje.</span><span class="sxs-lookup"><span data-stu-id="01149-128">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="01149-129">Kromě toho tato část také určuje nastavení pro zpracování metadat.</span><span class="sxs-lookup"><span data-stu-id="01149-129">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01149-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="01149-130">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01149-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="01149-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 [<span data-ttu-id="01149-132">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="01149-132">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="01149-133">Klienti</span><span class="sxs-lookup"><span data-stu-id="01149-133">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
