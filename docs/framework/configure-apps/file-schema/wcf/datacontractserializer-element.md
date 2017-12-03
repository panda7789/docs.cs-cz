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
ms.openlocfilehash: d38e3786c595c3fe6cc9ea54b68784c927901731
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="09598-102">&lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="09598-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="09598-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="09598-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="09598-104">Tento element proběhne dvě různé hierarchie.</span><span class="sxs-lookup"><span data-stu-id="09598-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="09598-105">Jeden je uvedena v následující části schéma hierarchie a druhý je uveden v oddílu Poznámky.</span><span class="sxs-lookup"><span data-stu-id="09598-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="09598-106">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="09598-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="09598-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="09598-107">\<behaviors></span></span>  
<span data-ttu-id="09598-108">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="09598-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="09598-109">\<chování ></span><span class="sxs-lookup"><span data-stu-id="09598-109">\<behavior></span></span>  
<span data-ttu-id="09598-110">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="09598-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09598-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09598-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
   maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09598-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="09598-112">Attributes and Elements</span></span>  
 <span data-ttu-id="09598-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="09598-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09598-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="09598-114">Attributes</span></span>  
  
|<span data-ttu-id="09598-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="09598-115">Element</span></span>|<span data-ttu-id="09598-116">Popis</span><span class="sxs-lookup"><span data-stu-id="09598-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09598-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="09598-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="09598-118">Logická hodnota, která určuje, jestli se ignorovat dat uvedených v koncovém bodě při jeho serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="09598-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="09598-119">Tento atribut je nastavit pouze na `<dataContractSerializer>` pod `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="09598-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="09598-120">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="09598-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="09598-121">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="09598-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="09598-122">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="09598-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09598-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="09598-123">Child Elements</span></span>  
 <span data-ttu-id="09598-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="09598-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09598-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="09598-125">Parent Elements</span></span>  
  
|<span data-ttu-id="09598-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="09598-126">Element</span></span>|<span data-ttu-id="09598-127">Popis</span><span class="sxs-lookup"><span data-stu-id="09598-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09598-128">\<chování ></span><span class="sxs-lookup"><span data-stu-id="09598-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="09598-129">Kolekce nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="09598-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="09598-130">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="09598-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="09598-131">Reprezentuje kořenový element <xref:System.Runtime.Serialization> část oboru názvů a obsahuje prvky pro nastavení možností nástroje <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="09598-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09598-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09598-132">Remarks</span></span>  
 <span data-ttu-id="09598-133">Jak jsme uvedli v úvodu tohoto tématu, to je druhá hierarchie, ve kterém \<X509Extension > dojde k elementu.</span><span class="sxs-lookup"><span data-stu-id="09598-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="09598-134">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="09598-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="09598-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="09598-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="09598-136">Další informace o známé typy najdete v tématu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="09598-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09598-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="09598-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="09598-138">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="09598-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="09598-139">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="09598-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
