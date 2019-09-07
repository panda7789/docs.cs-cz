---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400434"
---
# <a name="datacontractserializer"></a><span data-ttu-id="0fc83-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="0fc83-102">dataContractSerializer</span></span>
<span data-ttu-id="0fc83-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0fc83-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="0fc83-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0fc83-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0fc83-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0fc83-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0fc83-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0fc83-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="0fc83-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0fc83-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="0fc83-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0fc83-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="0fc83-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> dataContractSerializer**</span><span class="sxs-lookup"><span data-stu-id="0fc83-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fc83-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fc83-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fc83-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0fc83-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0fc83-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0fc83-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fc83-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="0fc83-113">Attributes</span></span>  
  
|<span data-ttu-id="0fc83-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="0fc83-114">Element</span></span>|<span data-ttu-id="0fc83-115">Popis</span><span class="sxs-lookup"><span data-stu-id="0fc83-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0fc83-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="0fc83-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="0fc83-117">Logická hodnota, která určuje, zda se mají ignorovat data poskytnutá koncovým bodem při jeho serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="0fc83-117">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="0fc83-118">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="0fc83-118">maxItemsInObjectGraph</span></span>|<span data-ttu-id="0fc83-119">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="0fc83-119">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fc83-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0fc83-120">Child Elements</span></span>  
 <span data-ttu-id="0fc83-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="0fc83-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fc83-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0fc83-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0fc83-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="0fc83-123">Element</span></span>|<span data-ttu-id="0fc83-124">Popis</span><span class="sxs-lookup"><span data-stu-id="0fc83-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fc83-125">\<> chování</span><span class="sxs-lookup"><span data-stu-id="0fc83-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0fc83-126">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="0fc83-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fc83-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0fc83-127">Remarks</span></span>  
 <span data-ttu-id="0fc83-128">Další informace <xref:System.Runtime.Serialization.DataContractSerializer> o známých typech naleznete v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="0fc83-128">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="0fc83-129">Prvek chování (je-li k dispozici) by se `<enableWebScript>` měl vždy zobrazit před prvkem chování v konfiguračním souboru. `<dataContractSerializer>`</span><span class="sxs-lookup"><span data-stu-id="0fc83-129">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="0fc83-130">V opačném případě není výsledné chování definováno.</span><span class="sxs-lookup"><span data-stu-id="0fc83-130">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc83-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fc83-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="0fc83-132">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="0fc83-132">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="0fc83-133">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="0fc83-133">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
