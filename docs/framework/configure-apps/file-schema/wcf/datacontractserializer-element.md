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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400455"
---
# \<dataContractSerializer>
<span data-ttu-id="a59fb-101">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="a59fb-101">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="a59fb-102">Tento prvek se vyskytuje ve dvou různých hierarchiích.</span><span class="sxs-lookup"><span data-stu-id="a59fb-102">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="a59fb-103">Jedna je uvedena v následující části hierarchie schématu a druhá je uvedena v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="a59fb-103">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="a59fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a59fb-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a59fb-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a59fb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a59fb-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a59fb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a59fb-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="a59fb-107">Attributes</span></span>  
  
|<span data-ttu-id="a59fb-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="a59fb-108">Element</span></span>|<span data-ttu-id="a59fb-109">Description</span><span class="sxs-lookup"><span data-stu-id="a59fb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a59fb-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="a59fb-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="a59fb-111">Logická hodnota, která určuje, zda mají být při serializaci nebo deserializaci ignorována data poskytnutá koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="a59fb-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="a59fb-112">Tento atribut lze nastavit pouze v `<dataContractSerializer>` rámci `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="a59fb-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="a59fb-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="a59fb-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="a59fb-114">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="a59fb-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="a59fb-115">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="a59fb-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a59fb-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a59fb-116">Child Elements</span></span>  
 <span data-ttu-id="a59fb-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="a59fb-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a59fb-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a59fb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a59fb-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="a59fb-119">Element</span></span>|<span data-ttu-id="a59fb-120">Description</span><span class="sxs-lookup"><span data-stu-id="a59fb-120">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|<span data-ttu-id="a59fb-121">Kolekce nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="a59fb-121">A collection of settings for the behavior of a service.</span></span>|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="a59fb-122">Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje prvky pro nastavení možností <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="a59fb-122">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a59fb-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a59fb-123">Remarks</span></span>  
 <span data-ttu-id="a59fb-124">Jak je uvedeno v úvodu tohoto tématu, je to druhá hierarchie, ve které se \<X509Extension> element vyskytuje.</span><span class="sxs-lookup"><span data-stu-id="a59fb-124">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 <span data-ttu-id="a59fb-125">Další informace o známých typech naleznete v tématu <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="a59fb-125">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a59fb-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a59fb-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="a59fb-127">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="a59fb-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="a59fb-128">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="a59fb-128">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
