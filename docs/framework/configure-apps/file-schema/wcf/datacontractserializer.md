---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 933d49092c392fa293468d546e521bf7ed858376
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539841"
---
# <a name="datacontractserializer"></a><span data-ttu-id="b7230-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="b7230-102">dataContractSerializer</span></span>
<span data-ttu-id="b7230-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b7230-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="b7230-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b7230-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b7230-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b7230-105">\<behaviors></span></span>  
<span data-ttu-id="b7230-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="b7230-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="b7230-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b7230-107">\<behavior></span></span>  
<span data-ttu-id="b7230-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="b7230-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7230-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7230-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7230-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b7230-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7230-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b7230-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7230-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b7230-112">Attributes</span></span>  
  
|<span data-ttu-id="b7230-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="b7230-113">Element</span></span>|<span data-ttu-id="b7230-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b7230-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7230-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="b7230-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="b7230-116">Logická hodnota, která určuje, jestli se má ignorovat data dodaná nástrojem koncový bod, když je serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="b7230-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="b7230-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="b7230-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="b7230-118">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="b7230-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7230-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b7230-119">Child Elements</span></span>  
 <span data-ttu-id="b7230-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="b7230-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7230-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b7230-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b7230-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="b7230-122">Element</span></span>|<span data-ttu-id="b7230-123">Popis</span><span class="sxs-lookup"><span data-stu-id="b7230-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7230-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b7230-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b7230-125">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b7230-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7230-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7230-126">Remarks</span></span>  
 <span data-ttu-id="b7230-127">Zobrazit <xref:System.Runtime.Serialization.DataContractSerializer> dokumentaci pro další informace o známých typů.</span><span class="sxs-lookup"><span data-stu-id="b7230-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b7230-128">`<dataContractSerializer>` Chování – element (pokud existuje) by měla vždy předcházet `<enableWebScript>` prvek chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b7230-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="b7230-129">V opačném případě výsledné chování není definováno.</span><span class="sxs-lookup"><span data-stu-id="b7230-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7230-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7230-130">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="b7230-131">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="b7230-131">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="b7230-132">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="b7230-132">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
