---
title: <dataContractSerializer> of <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: c81fdb040f2e0d6c9a3728d8ed3b917443ecb42e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115359"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="028e0-102">\<dataContractSerializer> of \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="028e0-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="028e0-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="028e0-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="028e0-104">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="028e0-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="028e0-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="028e0-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="028e0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="028e0-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="028e0-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="028e0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="028e0-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="028e0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="028e0-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="028e0-109">Attributes</span></span>  
  
|<span data-ttu-id="028e0-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="028e0-110">Element</span></span>|<span data-ttu-id="028e0-111">Popis</span><span class="sxs-lookup"><span data-stu-id="028e0-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="028e0-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="028e0-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="028e0-113">Logická hodnota, která určuje, jestli se má ignorovat data dodaná nástrojem koncový bod, když je serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="028e0-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="028e0-114">Tento atribut je nastavit pouze v `<dataContractSerializer>` pod `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="028e0-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="028e0-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="028e0-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="028e0-116">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="028e0-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="028e0-117">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="028e0-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="028e0-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="028e0-118">Child Elements</span></span>  
  
|<span data-ttu-id="028e0-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="028e0-119">Element</span></span>|<span data-ttu-id="028e0-120">Popis</span><span class="sxs-lookup"><span data-stu-id="028e0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="028e0-121">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="028e0-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="028e0-122">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="028e0-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="028e0-123">Další informace o kontraktech dat a známých typech najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="028e0-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="028e0-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="028e0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="028e0-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="028e0-125">Element</span></span>|<span data-ttu-id="028e0-126">Popis</span><span class="sxs-lookup"><span data-stu-id="028e0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="028e0-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="028e0-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="028e0-128">Představuje kořenový element <xref:System.Runtime.Serialization> části obor názvů a obsahuje prvky pro nastavení voleb <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="028e0-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="028e0-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="028e0-129">Remarks</span></span>  
 <span data-ttu-id="028e0-130">Další informace o známých typů najdete v tématu <xref:System.Runtime.Serialization.DataContractSerializer> a [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="028e0-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028e0-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="028e0-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="028e0-132">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="028e0-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
