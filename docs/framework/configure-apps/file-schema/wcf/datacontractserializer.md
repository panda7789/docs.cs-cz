---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 8814a48df8933cf08db78e397c24d42f2da26026
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919235"
---
# <a name="datacontractserializer"></a><span data-ttu-id="40e4c-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="40e4c-102">dataContractSerializer</span></span>
<span data-ttu-id="40e4c-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="40e4c-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="40e4c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="40e4c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="40e4c-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="40e4c-105">\<behaviors></span></span>  
<span data-ttu-id="40e4c-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="40e4c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="40e4c-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="40e4c-107">\<behavior></span></span>  
<span data-ttu-id="40e4c-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="40e4c-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40e4c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40e4c-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40e4c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="40e4c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="40e4c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="40e4c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40e4c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="40e4c-112">Attributes</span></span>  
  
|<span data-ttu-id="40e4c-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="40e4c-113">Element</span></span>|<span data-ttu-id="40e4c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="40e4c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40e4c-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="40e4c-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="40e4c-116">Logická hodnota, která určuje, zda se mají ignorovat data poskytnutá koncovým bodem při jeho serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="40e4c-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="40e4c-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="40e4c-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="40e4c-118">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="40e4c-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40e4c-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="40e4c-119">Child Elements</span></span>  
 <span data-ttu-id="40e4c-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="40e4c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40e4c-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="40e4c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="40e4c-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="40e4c-122">Element</span></span>|<span data-ttu-id="40e4c-123">Popis</span><span class="sxs-lookup"><span data-stu-id="40e4c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40e4c-124">\<> chování</span><span class="sxs-lookup"><span data-stu-id="40e4c-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="40e4c-125">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="40e4c-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40e4c-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40e4c-126">Remarks</span></span>  
 <span data-ttu-id="40e4c-127">Další informace <xref:System.Runtime.Serialization.DataContractSerializer> o známých typech naleznete v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="40e4c-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="40e4c-128">Prvek chování (je-li k dispozici) by se `<enableWebScript>` měl vždy zobrazit před prvkem chování v konfiguračním souboru. `<dataContractSerializer>`</span><span class="sxs-lookup"><span data-stu-id="40e4c-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="40e4c-129">V opačném případě není výsledné chování definováno.</span><span class="sxs-lookup"><span data-stu-id="40e4c-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e4c-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40e4c-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="40e4c-131">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="40e4c-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="40e4c-132">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="40e4c-132">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
