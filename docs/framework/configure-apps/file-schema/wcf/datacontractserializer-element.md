---
title: '&lt;DataContractSerializer&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: c79c8e8db2a4ea4526000bcbe336d1e664f9c4c2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150952"
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="5a66e-102">&lt;DataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="5a66e-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="5a66e-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5a66e-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="5a66e-104">Tento element vyskytuje ve dvou různých hierarchií.</span><span class="sxs-lookup"><span data-stu-id="5a66e-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="5a66e-105">Jeden je uvedena v následující části hierarchie schémat a druhý je uveden v oddílu Poznámky.</span><span class="sxs-lookup"><span data-stu-id="5a66e-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="5a66e-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5a66e-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a66e-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5a66e-107">\<behaviors></span></span>  
<span data-ttu-id="5a66e-108">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5a66e-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="5a66e-109">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5a66e-109">\<behavior></span></span>  
<span data-ttu-id="5a66e-110">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="5a66e-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a66e-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a66e-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a66e-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a66e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5a66e-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5a66e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a66e-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a66e-114">Attributes</span></span>  
  
|<span data-ttu-id="5a66e-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a66e-115">Element</span></span>|<span data-ttu-id="5a66e-116">Popis</span><span class="sxs-lookup"><span data-stu-id="5a66e-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a66e-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="5a66e-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="5a66e-118">Logická hodnota, která určuje, jestli se má ignorovat data dodaná nástrojem koncový bod, když je serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="5a66e-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="5a66e-119">Tento atribut je nastavit pouze v `<dataContractSerializer>` pod `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="5a66e-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="5a66e-120">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="5a66e-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="5a66e-121">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="5a66e-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="5a66e-122">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="5a66e-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a66e-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a66e-123">Child Elements</span></span>  
 <span data-ttu-id="5a66e-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a66e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a66e-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a66e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5a66e-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a66e-126">Element</span></span>|<span data-ttu-id="5a66e-127">Popis</span><span class="sxs-lookup"><span data-stu-id="5a66e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a66e-128">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5a66e-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="5a66e-129">Kolekce nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="5a66e-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="5a66e-130">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="5a66e-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="5a66e-131">Představuje kořenový element <xref:System.Runtime.Serialization> části obor názvů a obsahuje prvky pro nastavení voleb <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5a66e-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a66e-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a66e-132">Remarks</span></span>  
 <span data-ttu-id="5a66e-133">Jak jsme uvedli v úvodu tohoto tématu, toto je druhá hierarchie, ve kterém \<X509Extension > element vyskytuje.</span><span class="sxs-lookup"><span data-stu-id="5a66e-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="5a66e-134">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="5a66e-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="5a66e-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="5a66e-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="5a66e-136">Další informace o známých typů najdete v tématu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5a66e-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a66e-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a66e-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="5a66e-138">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="5a66e-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="5a66e-139">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="5a66e-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
