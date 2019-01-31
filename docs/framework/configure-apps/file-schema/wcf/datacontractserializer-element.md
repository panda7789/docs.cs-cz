---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 1b4fd959d5e522150751d2e9b8be8c5b2252bf27
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254948"
---
# <a name="datacontractserializer"></a><span data-ttu-id="43e52-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="43e52-101">\<dataContractSerializer></span></span>
<span data-ttu-id="43e52-102">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="43e52-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="43e52-103">Tento element vyskytuje ve dvou různých hierarchií.</span><span class="sxs-lookup"><span data-stu-id="43e52-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="43e52-104">Jeden je uvedena v následující části hierarchie schémat a druhý je uveden v oddílu Poznámky.</span><span class="sxs-lookup"><span data-stu-id="43e52-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="43e52-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="43e52-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="43e52-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="43e52-106">\<behaviors></span></span>  
<span data-ttu-id="43e52-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="43e52-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="43e52-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="43e52-108">\<behavior></span></span>  
<span data-ttu-id="43e52-109">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="43e52-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43e52-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43e52-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43e52-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="43e52-111">Attributes and Elements</span></span>  
 <span data-ttu-id="43e52-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="43e52-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43e52-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="43e52-113">Attributes</span></span>  
  
|<span data-ttu-id="43e52-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="43e52-114">Element</span></span>|<span data-ttu-id="43e52-115">Popis</span><span class="sxs-lookup"><span data-stu-id="43e52-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43e52-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="43e52-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="43e52-117">Logická hodnota, která určuje, jestli se má ignorovat data dodaná nástrojem koncový bod, když je serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="43e52-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="43e52-118">Tento atribut je nastavit pouze v `<dataContractSerializer>` pod `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="43e52-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="43e52-119">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="43e52-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="43e52-120">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="43e52-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="43e52-121">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="43e52-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43e52-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="43e52-122">Child Elements</span></span>  
 <span data-ttu-id="43e52-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="43e52-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43e52-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="43e52-124">Parent Elements</span></span>  
  
|<span data-ttu-id="43e52-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="43e52-125">Element</span></span>|<span data-ttu-id="43e52-126">Popis</span><span class="sxs-lookup"><span data-stu-id="43e52-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43e52-127">\<behavior></span><span class="sxs-lookup"><span data-stu-id="43e52-127">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="43e52-128">Kolekce nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="43e52-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="43e52-129">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="43e52-129">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="43e52-130">Představuje kořenový element <xref:System.Runtime.Serialization> části obor názvů a obsahuje prvky pro nastavení voleb <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="43e52-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43e52-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43e52-131">Remarks</span></span>  
 <span data-ttu-id="43e52-132">Jak jsme uvedli v úvodu tohoto tématu, toto je druhá hierarchie, ve kterém \<X509Extension > element vyskytuje.</span><span class="sxs-lookup"><span data-stu-id="43e52-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="43e52-133">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="43e52-133">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="43e52-134">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="43e52-134">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="43e52-135">Další informace o známých typů najdete v tématu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="43e52-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e52-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43e52-136">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="43e52-137">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="43e52-137">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="43e52-138">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="43e52-138">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
