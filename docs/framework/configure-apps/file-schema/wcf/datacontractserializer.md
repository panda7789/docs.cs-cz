---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 7952e6cc4d2fe7eaa77e297a650f7ffbd7aec785
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040932"
---
# <a name="datacontractserializer"></a><span data-ttu-id="d3c93-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="d3c93-102">dataContractSerializer</span></span>
<span data-ttu-id="d3c93-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d3c93-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="d3c93-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d3c93-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d3c93-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="d3c93-105">\<behaviors></span></span>  
<span data-ttu-id="d3c93-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d3c93-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d3c93-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="d3c93-107">\<behavior></span></span>  
<span data-ttu-id="d3c93-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="d3c93-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3c93-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3c93-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3c93-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d3c93-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d3c93-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d3c93-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3c93-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d3c93-112">Attributes</span></span>  
  
|<span data-ttu-id="d3c93-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3c93-113">Element</span></span>|<span data-ttu-id="d3c93-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d3c93-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d3c93-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="d3c93-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="d3c93-116">Logická hodnota, která určuje, zda se mají ignorovat data poskytnutá koncovým bodem při jeho serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="d3c93-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="d3c93-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="d3c93-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="d3c93-118">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="d3c93-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3c93-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d3c93-119">Child Elements</span></span>  
 <span data-ttu-id="d3c93-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="d3c93-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3c93-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d3c93-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d3c93-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3c93-122">Element</span></span>|<span data-ttu-id="d3c93-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d3c93-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3c93-124">\<> chování</span><span class="sxs-lookup"><span data-stu-id="d3c93-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="d3c93-125">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d3c93-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3c93-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3c93-126">Remarks</span></span>  
 <span data-ttu-id="d3c93-127">Další informace <xref:System.Runtime.Serialization.DataContractSerializer> o známých typech naleznete v dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="d3c93-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="d3c93-128">Prvek chování (je-li k dispozici) by se `<enableWebScript>` měl vždy zobrazit před prvkem chování v konfiguračním souboru. `<dataContractSerializer>`</span><span class="sxs-lookup"><span data-stu-id="d3c93-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="d3c93-129">V opačném případě není výsledné chování definováno.</span><span class="sxs-lookup"><span data-stu-id="d3c93-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c93-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3c93-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="d3c93-131">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="d3c93-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="d3c93-132">Přenos a serializace dat</span><span class="sxs-lookup"><span data-stu-id="d3c93-132">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
