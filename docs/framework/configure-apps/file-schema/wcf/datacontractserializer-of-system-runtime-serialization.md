---
title: <dataContractSerializer>z < System. Runtime. Serialization >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: eb556f533af1f99049382e9a2e34465f88d563db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398082"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="0460a-102">\<dataContractSerializer> of \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="0460a-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="0460a-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0460a-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="0460a-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0460a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0460a-105">&nbsp;&nbsp;[ **\<System. Runtime. Serialization – >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="0460a-105">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="0460a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> dataContractSerializer**</span><span class="sxs-lookup"><span data-stu-id="0460a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0460a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0460a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0460a-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0460a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0460a-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0460a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0460a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0460a-110">Attributes</span></span>  
  
|<span data-ttu-id="0460a-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="0460a-111">Element</span></span>|<span data-ttu-id="0460a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0460a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0460a-113">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="0460a-113">ignoreExtensionDataObject</span></span>|<span data-ttu-id="0460a-114">Logická hodnota, která určuje, zda mají být při serializaci nebo deserializaci ignorována data poskytnutá koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="0460a-114">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="0460a-115">Tento atribut lze nastavit pouze `<dataContractSerializer>` v `<behavior>` rámci elementu.</span><span class="sxs-lookup"><span data-stu-id="0460a-115">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="0460a-116">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="0460a-116">maxItemsInObjectGraph</span></span>|<span data-ttu-id="0460a-117">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="0460a-117">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="0460a-118">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="0460a-118">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0460a-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0460a-119">Child Elements</span></span>  
  
|<span data-ttu-id="0460a-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="0460a-120">Element</span></span>|<span data-ttu-id="0460a-121">Popis</span><span class="sxs-lookup"><span data-stu-id="0460a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0460a-122">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="0460a-122">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="0460a-123">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="0460a-123">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="0460a-124">Další informace o kontraktech dat a známých typech najdete v tématu [známé typy kontraktu dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="0460a-124">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0460a-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0460a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="0460a-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="0460a-126">Element</span></span>|<span data-ttu-id="0460a-127">Popis</span><span class="sxs-lookup"><span data-stu-id="0460a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0460a-128">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="0460a-128">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="0460a-129">Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje prvky pro nastavení možností <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0460a-129">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0460a-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0460a-130">Remarks</span></span>  
 <span data-ttu-id="0460a-131">Další informace o známých typech naleznete v tématu <xref:System.Runtime.Serialization.DataContractSerializer> a [známé typy kontraktu dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="0460a-131">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0460a-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0460a-132">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="0460a-133">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="0460a-133">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
