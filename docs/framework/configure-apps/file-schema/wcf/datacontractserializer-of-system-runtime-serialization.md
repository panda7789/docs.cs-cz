---
title: <dataContractSerializer>z <System. Runtime. Serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: eb556f533af1f99049382e9a2e34465f88d563db
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398082"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="73b13-102">\<dataContractSerializer> z \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="73b13-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="73b13-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="73b13-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="73b13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73b13-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73b13-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="73b13-105">Attributes and Elements</span></span>  
 <span data-ttu-id="73b13-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="73b13-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73b13-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="73b13-107">Attributes</span></span>  
  
|<span data-ttu-id="73b13-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="73b13-108">Element</span></span>|<span data-ttu-id="73b13-109">Description</span><span class="sxs-lookup"><span data-stu-id="73b13-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73b13-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="73b13-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="73b13-111">Logická hodnota, která určuje, zda mají být při serializaci nebo deserializaci ignorována data poskytnutá koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="73b13-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="73b13-112">Tento atribut lze nastavit pouze v `<dataContractSerializer>` rámci `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="73b13-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="73b13-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="73b13-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="73b13-114">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="73b13-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="73b13-115">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="73b13-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73b13-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="73b13-116">Child Elements</span></span>  
  
|<span data-ttu-id="73b13-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="73b13-117">Element</span></span>|<span data-ttu-id="73b13-118">Description</span><span class="sxs-lookup"><span data-stu-id="73b13-118">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="73b13-119">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="73b13-119">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="73b13-120">Další informace o kontraktech dat a známých typech najdete v tématu [známé typy kontraktu dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="73b13-120">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73b13-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="73b13-121">Parent Elements</span></span>  
  
|<span data-ttu-id="73b13-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="73b13-122">Element</span></span>|<span data-ttu-id="73b13-123">Description</span><span class="sxs-lookup"><span data-stu-id="73b13-123">Description</span></span>|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="73b13-124">Představuje kořenový prvek <xref:System.Runtime.Serialization> oddílu oboru názvů a obsahuje prvky pro nastavení možností <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="73b13-124">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73b13-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73b13-125">Remarks</span></span>  
 <span data-ttu-id="73b13-126">Další informace o známých typech naleznete v tématu <xref:System.Runtime.Serialization.DataContractSerializer> a [známé typy kontraktu dat](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="73b13-126">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73b13-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="73b13-127">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="73b13-128">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="73b13-128">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
