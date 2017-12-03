---
title: dataContractSerializer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a64f5ae4573efbd8c0f7d622e6b94b7786585bb1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="datacontractserializer"></a><span data-ttu-id="2918d-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="2918d-102">dataContractSerializer</span></span>
<span data-ttu-id="2918d-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2918d-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="2918d-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2918d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2918d-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2918d-105">\<behaviors></span></span>  
<span data-ttu-id="2918d-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2918d-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="2918d-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2918d-107">\<behavior></span></span>  
<span data-ttu-id="2918d-108">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="2918d-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2918d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2918d-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
      maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2918d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2918d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2918d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2918d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2918d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2918d-112">Attributes</span></span>  
  
|<span data-ttu-id="2918d-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="2918d-113">Element</span></span>|<span data-ttu-id="2918d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2918d-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2918d-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="2918d-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="2918d-116">Logická hodnota, která určuje, jestli se ignorovat data poskytl koncového bodu, když je právě serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="2918d-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="2918d-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="2918d-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="2918d-118">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="2918d-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2918d-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2918d-119">Child Elements</span></span>  
 <span data-ttu-id="2918d-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="2918d-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2918d-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2918d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2918d-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="2918d-122">Element</span></span>|<span data-ttu-id="2918d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="2918d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2918d-124">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2918d-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2918d-125">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2918d-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2918d-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2918d-126">Remarks</span></span>  
 <span data-ttu-id="2918d-127">Najdete v článku <xref:System.Runtime.Serialization.DataContractSerializer> dokumentace pro další informace o známé typy.</span><span class="sxs-lookup"><span data-stu-id="2918d-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2918d-128">`<dataContractSerializer>` Element chování (pokud existuje) vždy zobrazit před `<enableWebScript>` chování element v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="2918d-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="2918d-129">Jinak jejich výsledné chování není definován.</span><span class="sxs-lookup"><span data-stu-id="2918d-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2918d-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="2918d-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="2918d-131">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="2918d-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="2918d-132">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="2918d-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
