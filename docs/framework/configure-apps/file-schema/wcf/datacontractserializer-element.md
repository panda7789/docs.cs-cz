---
title: '&lt;dataContractSerializer&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: d8e0f2ac6e417609ec17d345d1cb20f2a4255dba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657575"
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="14e58-102">&lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="14e58-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="14e58-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="14e58-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="14e58-104">Tento element vyskytuje ve dvou různých hierarchií.</span><span class="sxs-lookup"><span data-stu-id="14e58-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="14e58-105">Jeden je uvedena v následující části hierarchie schémat a druhý je uveden v oddílu Poznámky.</span><span class="sxs-lookup"><span data-stu-id="14e58-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="14e58-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="14e58-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="14e58-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="14e58-107">\<behaviors></span></span>  
<span data-ttu-id="14e58-108">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="14e58-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="14e58-109">\<chování ></span><span class="sxs-lookup"><span data-stu-id="14e58-109">\<behavior></span></span>  
<span data-ttu-id="14e58-110">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="14e58-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e58-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14e58-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14e58-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="14e58-112">Attributes and Elements</span></span>  
 <span data-ttu-id="14e58-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="14e58-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14e58-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="14e58-114">Attributes</span></span>  
  
|<span data-ttu-id="14e58-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="14e58-115">Element</span></span>|<span data-ttu-id="14e58-116">Popis</span><span class="sxs-lookup"><span data-stu-id="14e58-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14e58-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="14e58-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="14e58-118">Logická hodnota, která určuje, jestli se má ignorovat data dodaná nástrojem koncový bod, když je serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="14e58-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="14e58-119">Tento atribut je nastavit pouze v `<dataContractSerializer>` pod `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="14e58-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="14e58-120">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="14e58-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="14e58-121">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="14e58-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="14e58-122">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="14e58-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14e58-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="14e58-123">Child Elements</span></span>  
 <span data-ttu-id="14e58-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="14e58-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14e58-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="14e58-125">Parent Elements</span></span>  
  
|<span data-ttu-id="14e58-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="14e58-126">Element</span></span>|<span data-ttu-id="14e58-127">Popis</span><span class="sxs-lookup"><span data-stu-id="14e58-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14e58-128">\<behavior></span><span class="sxs-lookup"><span data-stu-id="14e58-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="14e58-129">Kolekce nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="14e58-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="14e58-130">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="14e58-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="14e58-131">Představuje kořenový element <xref:System.Runtime.Serialization> části obor názvů a obsahuje prvky pro nastavení voleb <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="14e58-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14e58-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14e58-132">Remarks</span></span>  
 <span data-ttu-id="14e58-133">Jak jsme uvedli v úvodu tohoto tématu, toto je druhá hierarchie, ve kterém \<X509Extension > element vyskytuje.</span><span class="sxs-lookup"><span data-stu-id="14e58-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="14e58-134">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="14e58-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="14e58-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="14e58-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="14e58-136">Další informace o známých typů najdete v tématu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="14e58-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e58-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14e58-137">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="14e58-138">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="14e58-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="14e58-139">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="14e58-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
