---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 8ba16d9cc30b07d3e6b0924e6013ec01443867d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139045"
---
# <a name="datacontractserializer"></a><span data-ttu-id="16cdc-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="16cdc-102">dataContractSerializer</span></span>
<span data-ttu-id="16cdc-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="16cdc-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="16cdc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="16cdc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="16cdc-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="16cdc-105">\<behaviors></span></span>  
<span data-ttu-id="16cdc-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="16cdc-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="16cdc-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="16cdc-107">\<behavior></span></span>  
<span data-ttu-id="16cdc-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="16cdc-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16cdc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16cdc-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16cdc-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="16cdc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="16cdc-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="16cdc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16cdc-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="16cdc-112">Attributes</span></span>  
  
|<span data-ttu-id="16cdc-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="16cdc-113">Element</span></span>|<span data-ttu-id="16cdc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="16cdc-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="16cdc-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="16cdc-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="16cdc-116">Logická hodnota, která určuje, jestli se má ignorovat data dodaná nástrojem koncový bod, když je serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="16cdc-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="16cdc-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="16cdc-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="16cdc-118">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="16cdc-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16cdc-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="16cdc-119">Child Elements</span></span>  
 <span data-ttu-id="16cdc-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="16cdc-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16cdc-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="16cdc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="16cdc-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="16cdc-122">Element</span></span>|<span data-ttu-id="16cdc-123">Popis</span><span class="sxs-lookup"><span data-stu-id="16cdc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16cdc-124">\<chování ></span><span class="sxs-lookup"><span data-stu-id="16cdc-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="16cdc-125">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="16cdc-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16cdc-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16cdc-126">Remarks</span></span>  
 <span data-ttu-id="16cdc-127">Zobrazit <xref:System.Runtime.Serialization.DataContractSerializer> dokumentaci pro další informace o známých typů.</span><span class="sxs-lookup"><span data-stu-id="16cdc-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="16cdc-128">`<dataContractSerializer>` Chování – element (pokud existuje) by měla vždy předcházet `<enableWebScript>` prvek chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="16cdc-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="16cdc-129">V opačném případě výsledné chování není definováno.</span><span class="sxs-lookup"><span data-stu-id="16cdc-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16cdc-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16cdc-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="16cdc-131">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="16cdc-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="16cdc-132">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="16cdc-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
