---
title: <dataContractSerializer>z < System. Runtime. Serialization >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 380d9ba5b8407d78b5045fd34fcdf37c0818d6f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919353"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="db61e-102">\<dataContractSerializer> of \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="db61e-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="db61e-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="db61e-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="db61e-104">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="db61e-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="db61e-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="db61e-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db61e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db61e-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer"
                       type="String" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db61e-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="db61e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="db61e-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="db61e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db61e-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="db61e-109">Attributes</span></span>  
  
|<span data-ttu-id="db61e-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="db61e-110">Element</span></span>|<span data-ttu-id="db61e-111">Popis</span><span class="sxs-lookup"><span data-stu-id="db61e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db61e-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="db61e-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="db61e-113">Logická hodnota, která určuje, zda mají být při serializaci nebo deserializaci ignorována data poskytnutá koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="db61e-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="db61e-114">Tento atribut lze nastavit pouze `<dataContractSerializer>` v `<behavior>` rámci elementu.</span><span class="sxs-lookup"><span data-stu-id="db61e-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="db61e-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="db61e-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="db61e-116">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="db61e-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="db61e-117">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="db61e-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db61e-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="db61e-118">Child Elements</span></span>  
  
|<span data-ttu-id="db61e-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="db61e-119">Element</span></span>|<span data-ttu-id="db61e-120">Popis</span><span class="sxs-lookup"><span data-stu-id="db61e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db61e-121">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="db61e-121">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="db61e-122">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="db61e-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="db61e-123">Další informace o kontraktech dat a známých typech najdete v tématu [známé typy kontraktu dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="db61e-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="db61e-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="db61e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="db61e-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="db61e-125">Element</span></span>|<span data-ttu-id="db61e-126">Popis</span><span class="sxs-lookup"><span data-stu-id="db61e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db61e-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="db61e-127">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="db61e-128">Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje prvky pro nastavení možností <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="db61e-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db61e-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db61e-129">Remarks</span></span>  
 <span data-ttu-id="db61e-130">Další informace o známých typech naleznete v tématu <xref:System.Runtime.Serialization.DataContractSerializer> a [známé typy kontraktu dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="db61e-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db61e-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db61e-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="db61e-132">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="db61e-132">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
