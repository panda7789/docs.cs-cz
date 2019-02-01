---
title: <dataContractSerializer> of <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 488b0754194c1fa7896a168daac0a3a497076e56
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265932"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="7fe42-102">\<dataContractSerializer> of \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="7fe42-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="7fe42-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7fe42-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="7fe42-104">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="7fe42-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="7fe42-105">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="7fe42-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe42-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fe42-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fe42-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7fe42-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7fe42-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7fe42-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fe42-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="7fe42-109">Attributes</span></span>  
  
|<span data-ttu-id="7fe42-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="7fe42-110">Element</span></span>|<span data-ttu-id="7fe42-111">Popis</span><span class="sxs-lookup"><span data-stu-id="7fe42-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fe42-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="7fe42-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="7fe42-113">Logická hodnota, která určuje, jestli se má ignorovat data dodaná nástrojem koncový bod, když je serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="7fe42-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="7fe42-114">Tento atribut je nastavit pouze v `<dataContractSerializer>` pod `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="7fe42-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="7fe42-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="7fe42-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="7fe42-116">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="7fe42-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="7fe42-117">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="7fe42-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fe42-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7fe42-118">Child Elements</span></span>  
  
|<span data-ttu-id="7fe42-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="7fe42-119">Element</span></span>|<span data-ttu-id="7fe42-120">Popis</span><span class="sxs-lookup"><span data-stu-id="7fe42-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fe42-121">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="7fe42-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="7fe42-122">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="7fe42-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="7fe42-123">Další informace o kontraktech dat a známých typech najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="7fe42-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7fe42-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7fe42-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7fe42-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="7fe42-125">Element</span></span>|<span data-ttu-id="7fe42-126">Popis</span><span class="sxs-lookup"><span data-stu-id="7fe42-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fe42-127">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="7fe42-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="7fe42-128">Představuje kořenový element <xref:System.Runtime.Serialization> části obor názvů a obsahuje prvky pro nastavení voleb <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7fe42-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fe42-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fe42-129">Remarks</span></span>  
 <span data-ttu-id="7fe42-130">Další informace o známých typů najdete v tématu <xref:System.Runtime.Serialization.DataContractSerializer> a [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="7fe42-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe42-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fe42-131">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="7fe42-132">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="7fe42-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
