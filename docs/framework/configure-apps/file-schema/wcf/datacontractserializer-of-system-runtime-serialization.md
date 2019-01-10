---
title: '&lt;dataContractSerializer&gt; – &lt;system.runtime.serialization&gt;'
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: f31dd8479f3bd6b36915b3ff00ff53babe3c0248
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150172"
---
# <a name="ltdatacontractserializergt-of-ltsystemruntimeserializationgt"></a><span data-ttu-id="afbd5-102">&lt;dataContractSerializer&gt; – &lt;system.runtime.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="afbd5-102">&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="afbd5-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="afbd5-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="afbd5-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="afbd5-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="afbd5-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="afbd5-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afbd5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afbd5-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afbd5-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="afbd5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="afbd5-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="afbd5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afbd5-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="afbd5-109">Attributes</span></span>  
  
|<span data-ttu-id="afbd5-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="afbd5-110">Element</span></span>|<span data-ttu-id="afbd5-111">Popis</span><span class="sxs-lookup"><span data-stu-id="afbd5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="afbd5-112">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="afbd5-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="afbd5-113">Logická hodnota, která určuje, jestli se má ignorovat data dodaná nástrojem koncový bod, když je serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="afbd5-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="afbd5-114">Tento atribut je nastavit pouze v `<dataContractSerializer>` pod `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="afbd5-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="afbd5-115">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="afbd5-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="afbd5-116">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="afbd5-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="afbd5-117">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="afbd5-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afbd5-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="afbd5-118">Child Elements</span></span>  
  
|<span data-ttu-id="afbd5-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="afbd5-119">Element</span></span>|<span data-ttu-id="afbd5-120">Popis</span><span class="sxs-lookup"><span data-stu-id="afbd5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afbd5-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="afbd5-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="afbd5-122">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="afbd5-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="afbd5-123">Další informace o kontraktech dat a známých typech najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="afbd5-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afbd5-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="afbd5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="afbd5-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="afbd5-125">Element</span></span>|<span data-ttu-id="afbd5-126">Popis</span><span class="sxs-lookup"><span data-stu-id="afbd5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afbd5-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="afbd5-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="afbd5-128">Představuje kořenový element <xref:System.Runtime.Serialization> části obor názvů a obsahuje prvky pro nastavení voleb <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="afbd5-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afbd5-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="afbd5-129">Remarks</span></span>  
 <span data-ttu-id="afbd5-130">Další informace o známých typů najdete v tématu <xref:System.Runtime.Serialization.DataContractSerializer> a [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="afbd5-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afbd5-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="afbd5-131">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 [<span data-ttu-id="afbd5-132">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="afbd5-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
