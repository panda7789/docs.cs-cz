---
title: "&lt;dataContractSerializer&gt; – &lt;system.runtime.serialization&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e0c8d0e82696935a480935ebbb71530e052f8d8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltdatacontractserializergt-of-ltsystemruntimeserializationgt"></a><span data-ttu-id="91719-102">&lt;dataContractSerializer&gt; – &lt;system.runtime.serialization&gt;</span><span class="sxs-lookup"><span data-stu-id="91719-102">&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="91719-103">Obsahuje konfigurační data pro <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="91719-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="91719-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="91719-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="91719-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="91719-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91719-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91719-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91719-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="91719-107">Attributes and Elements</span></span>  
 <span data-ttu-id="91719-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="91719-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91719-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="91719-109">Attributes</span></span>  
  
|<span data-ttu-id="91719-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="91719-110">Element</span></span>|<span data-ttu-id="91719-111">Popis</span><span class="sxs-lookup"><span data-stu-id="91719-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91719-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="91719-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="91719-113">Logická hodnota, která určuje, jestli se ignorovat dat uvedených v koncovém bodě při jeho serializován nebo deserializován.</span><span class="sxs-lookup"><span data-stu-id="91719-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="91719-114">Tento atribut je nastavit pouze na `<dataContractSerializer>` pod `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="91719-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="91719-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="91719-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="91719-116">Celé číslo, které určuje maximální počet položek k serializaci nebo deserializaci.</span><span class="sxs-lookup"><span data-stu-id="91719-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="91719-117">Tento atribut je 65536.</span><span class="sxs-lookup"><span data-stu-id="91719-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91719-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="91719-118">Child Elements</span></span>  
  
|<span data-ttu-id="91719-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="91719-119">Element</span></span>|<span data-ttu-id="91719-120">Popis</span><span class="sxs-lookup"><span data-stu-id="91719-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91719-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="91719-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="91719-122">Obsahuje známé typy, které <xref:System.Runtime.Serialization.DataContractSerializer> používá při deserializaci.</span><span class="sxs-lookup"><span data-stu-id="91719-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="91719-123">Další informace o kontraktech dat a známé typy najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="91719-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91719-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="91719-124">Parent Elements</span></span>  
  
|<span data-ttu-id="91719-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="91719-125">Element</span></span>|<span data-ttu-id="91719-126">Popis</span><span class="sxs-lookup"><span data-stu-id="91719-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91719-127">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="91719-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="91719-128">Reprezentuje kořenový element <xref:System.Runtime.Serialization> část oboru názvů a obsahuje prvky pro nastavení možností nástroje <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="91719-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91719-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91719-129">Remarks</span></span>  
 <span data-ttu-id="91719-130">Další informace o známé typy najdete v tématu <xref:System.Runtime.Serialization.DataContractSerializer> a [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="91719-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91719-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="91719-131">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 [<span data-ttu-id="91719-132">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="91719-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
