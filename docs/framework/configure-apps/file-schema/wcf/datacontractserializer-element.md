---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 7e440810fee1dddb7025d1385b1edb4838d98a39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925915"
---
# <a name="datacontractserializer"></a><span data-ttu-id="95882-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="95882-101">\<dataContractSerializer></span></span>
<span data-ttu-id="95882-102">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="95882-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="95882-103">Tento prvek se vyskytuje ve dvou různých hierarchiích.</span><span class="sxs-lookup"><span data-stu-id="95882-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="95882-104">Jedna je uvedena v následující části hierarchie schématu a druhá je uvedena v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="95882-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="95882-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="95882-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="95882-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="95882-106">\<behaviors></span></span>  
<span data-ttu-id="95882-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="95882-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="95882-108">\<> chování</span><span class="sxs-lookup"><span data-stu-id="95882-108">\<behavior></span></span>  
<span data-ttu-id="95882-109">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="95882-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95882-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95882-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95882-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="95882-111">Attributes and Elements</span></span>  
 <span data-ttu-id="95882-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="95882-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95882-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="95882-113">Attributes</span></span>  
  
|<span data-ttu-id="95882-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="95882-114">Element</span></span>|<span data-ttu-id="95882-115">Popis</span><span class="sxs-lookup"><span data-stu-id="95882-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95882-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="95882-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="95882-117">Logická hodnota, která určuje, zda mají být při serializaci nebo deserializaci ignorována data poskytnutá koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="95882-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="95882-118">Tento atribut lze nastavit pouze `<dataContractSerializer>` v `<behavior>` rámci elementu.</span><span class="sxs-lookup"><span data-stu-id="95882-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="95882-119">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="95882-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="95882-120">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="95882-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="95882-121">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="95882-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95882-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="95882-122">Child Elements</span></span>  
 <span data-ttu-id="95882-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="95882-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95882-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="95882-124">Parent Elements</span></span>  
  
|<span data-ttu-id="95882-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="95882-125">Element</span></span>|<span data-ttu-id="95882-126">Popis</span><span class="sxs-lookup"><span data-stu-id="95882-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95882-127">\<> chování</span><span class="sxs-lookup"><span data-stu-id="95882-127">\<behavior></span></span>](behavior-of-servicebehaviors.md)|<span data-ttu-id="95882-128">Kolekce nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="95882-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="95882-129">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="95882-129">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="95882-130">Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje prvky pro nastavení možností <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="95882-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95882-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95882-131">Remarks</span></span>  
 <span data-ttu-id="95882-132">Jak je uvedeno v úvodu tohoto tématu, je to druhá hierarchie, ve které dojde \<k prvku X509Extension >.</span><span class="sxs-lookup"><span data-stu-id="95882-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="95882-133">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="95882-133">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
  
 [<span data-ttu-id="95882-134">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="95882-134">\<dataContractSerializer></span></span>](datacontractserializer-element.md)  
  
 <span data-ttu-id="95882-135">Další informace o známých typech naleznete v tématu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="95882-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95882-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95882-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="95882-137">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="95882-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="95882-138">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="95882-138">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
