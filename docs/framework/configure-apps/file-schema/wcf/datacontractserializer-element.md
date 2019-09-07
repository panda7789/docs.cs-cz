---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: e24dae47171f741af064ca2eaa822928690acf6e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400455"
---
# <a name="datacontractserializer"></a><span data-ttu-id="5ff24-101">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5ff24-101">\<dataContractSerializer></span></span>
<span data-ttu-id="5ff24-102">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5ff24-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="5ff24-103">Tento prvek se vyskytuje ve dvou různých hierarchiích.</span><span class="sxs-lookup"><span data-stu-id="5ff24-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="5ff24-104">Jedna je uvedena v následující části hierarchie schématu a druhá je uvedena v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="5ff24-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
<span data-ttu-id="5ff24-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5ff24-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5ff24-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5ff24-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5ff24-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5ff24-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5ff24-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5ff24-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="5ff24-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5ff24-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="5ff24-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> dataContractSerializer**</span><span class="sxs-lookup"><span data-stu-id="5ff24-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ff24-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ff24-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ff24-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5ff24-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5ff24-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5ff24-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ff24-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="5ff24-114">Attributes</span></span>  
  
|<span data-ttu-id="5ff24-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ff24-115">Element</span></span>|<span data-ttu-id="5ff24-116">Popis</span><span class="sxs-lookup"><span data-stu-id="5ff24-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5ff24-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="5ff24-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="5ff24-118">Logická hodnota, která určuje, zda mají být při serializaci nebo deserializaci ignorována data poskytnutá koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="5ff24-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="5ff24-119">Tento atribut lze nastavit pouze `<dataContractSerializer>` v `<behavior>` rámci elementu.</span><span class="sxs-lookup"><span data-stu-id="5ff24-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="5ff24-120">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="5ff24-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="5ff24-121">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="5ff24-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="5ff24-122">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="5ff24-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ff24-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5ff24-123">Child Elements</span></span>  
 <span data-ttu-id="5ff24-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="5ff24-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ff24-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5ff24-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5ff24-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="5ff24-126">Element</span></span>|<span data-ttu-id="5ff24-127">Popis</span><span class="sxs-lookup"><span data-stu-id="5ff24-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ff24-128">\<> chování</span><span class="sxs-lookup"><span data-stu-id="5ff24-128">\<behavior></span></span>](behavior-of-servicebehaviors.md)|<span data-ttu-id="5ff24-129">Kolekce nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="5ff24-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="5ff24-130">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="5ff24-130">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="5ff24-131">Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje prvky pro nastavení možností <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5ff24-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ff24-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ff24-132">Remarks</span></span>  
 <span data-ttu-id="5ff24-133">Jak je uvedeno v úvodu tohoto tématu, je to druhá hierarchie, ve které dojde \<k prvku X509Extension >.</span><span class="sxs-lookup"><span data-stu-id="5ff24-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="5ff24-134">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="5ff24-134">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
  
 [<span data-ttu-id="5ff24-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="5ff24-135">\<dataContractSerializer></span></span>](datacontractserializer-element.md)  
  
 <span data-ttu-id="5ff24-136">Další informace o známých typech naleznete v tématu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5ff24-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff24-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ff24-137">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="5ff24-138">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="5ff24-138">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="5ff24-139">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="5ff24-139">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
