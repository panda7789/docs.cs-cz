---
title: '&lt;dataContractSerializer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27b80c831fdc66bd3b022645c3de9c0c31ee575a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="6cd8c-102">&lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="6cd8c-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="6cd8c-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="6cd8c-104">Tento element proběhne dvě různé hierarchie.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="6cd8c-105">Jeden je uvedena v následující části schéma hierarchie a druhý je uveden v oddílu Poznámky.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="6cd8c-106">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6cd8c-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="6cd8c-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="6cd8c-107">\<behaviors></span></span>  
<span data-ttu-id="6cd8c-108">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6cd8c-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="6cd8c-109">\<chování ></span><span class="sxs-lookup"><span data-stu-id="6cd8c-109">\<behavior></span></span>  
<span data-ttu-id="6cd8c-110">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="6cd8c-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd8c-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cd8c-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
   maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cd8c-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6cd8c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6cd8c-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cd8c-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="6cd8c-114">Attributes</span></span>  
  
|<span data-ttu-id="6cd8c-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="6cd8c-115">Element</span></span>|<span data-ttu-id="6cd8c-116">Popis</span><span class="sxs-lookup"><span data-stu-id="6cd8c-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6cd8c-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="6cd8c-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="6cd8c-118">Logická hodnota, která určuje, jestli se ignorovat dat uvedených v koncovém bodě při jeho serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="6cd8c-119">Tento atribut je nastavit pouze na `<dataContractSerializer>` pod `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="6cd8c-120">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="6cd8c-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="6cd8c-121">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="6cd8c-122">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6cd8c-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6cd8c-123">Child Elements</span></span>  
 <span data-ttu-id="6cd8c-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="6cd8c-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6cd8c-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6cd8c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6cd8c-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="6cd8c-126">Element</span></span>|<span data-ttu-id="6cd8c-127">Popis</span><span class="sxs-lookup"><span data-stu-id="6cd8c-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cd8c-128">\<chování ></span><span class="sxs-lookup"><span data-stu-id="6cd8c-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="6cd8c-129">Kolekce nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="6cd8c-130">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="6cd8c-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="6cd8c-131">Reprezentuje kořenový element <xref:System.Runtime.Serialization> část oboru názvů a obsahuje prvky pro nastavení možností nástroje <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cd8c-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cd8c-132">Remarks</span></span>  
 <span data-ttu-id="6cd8c-133">Jak jsme uvedli v úvodu tohoto tématu, to je druhá hierarchie, ve kterém \<X509Extension > dojde k elementu.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="6cd8c-134">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="6cd8c-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="6cd8c-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="6cd8c-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="6cd8c-136">Další informace o známé typy najdete v tématu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6cd8c-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd8c-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cd8c-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="6cd8c-138">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="6cd8c-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="6cd8c-139">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="6cd8c-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
